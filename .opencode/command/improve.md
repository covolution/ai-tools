---
description: Fetch improvement tasks from a GitHub issue and apply selected ones to a project
---

# Improve Command

You are an AI agent that applies improvement tasks from a GitHub issue to a local project. You work interactively — the user chooses which tasks to action, you create a branch per task, apply the changes, and validate if tests/build scripts exist.

**Arguments:** `$ARGUMENTS` (format: `<project-path> <github-issue-url>`)

---

## Step 1 — Parse Arguments

Extract both arguments from `$ARGUMENTS`:
- `PROJECT_PATH`: the local filesystem path to the project to improve
- `ISSUE_URL`: the GitHub issue URL containing improvement tasks

If either argument is missing, tell the user:
> Usage: `/improve <project-path> <github-issue-url>`

Verify `PROJECT_PATH` exists on disk. If not, report the error and stop.

---

## Step 2 — Fetch the GitHub Issue

Use the `gh` CLI to fetch the issue content:

```bash
gh issue view <issue-number> --repo <owner>/<repo> --json title,body,comments
```

Parse `owner`, `repo`, and `issue-number` from the provided `ISSUE_URL`.

If `gh` is not available or the issue cannot be fetched, report the error and stop.

---

## Step 3 — Extract Improvement Tasks

Analyse the issue title, body, and comments to identify a list of discrete improvement tasks. Tasks may appear as:
- Markdown checkboxes (`- [ ] ...`)
- Numbered list items
- Bullet points describing distinct changes

Present the tasks to the user as a numbered list:

```
Found X improvement tasks in <ISSUE_URL>:

1. <task description>
2. <task description>
3. <task description>
...

Which task(s) would you like to work on? (enter numbers, e.g. 1 3 5, or "all")
```

Wait for the user's response before proceeding.

---

## Step 4 — Work On Each Selected Task

For each task the user selected, follow this workflow in sequence:

### 4a — Check for Uncommitted Changes

Before switching branches, run:

```bash
git -C <PROJECT_PATH> status --porcelain
```

If there are any uncommitted changes (staged or unstaged), **stop and ask the user**:

```
There are uncommitted changes in <current-branch>:

  <git status output>

How would you like to proceed?
  1. Stash changes and continue
  2. Leave changes as-is and continue (may cause conflicts)
  3. Stop — I'll handle this manually
```

- If **stash**: run `git -C <PROJECT_PATH> stash push -m "fix: stash before switching to next task"` then continue.
- If **leave as-is**: warn the user and continue.
- If **stop**: halt the entire command.

### 4b — Create a Branch

From the project root at `PROJECT_PATH`, determine the current default branch (`main` or `master`), ensure it is up to date, then create a new branch:

```bash
git checkout <default-branch> && git pull
git checkout -b fix/<issue-number>-<task-slug>
```

Where `<task-slug>` is a short kebab-case summary of the task (max 5 words).

### 4b — Apply the Improvement

Before making any changes, check if an `AGENTS.md` (or `agents.md`) file exists in `PROJECT_PATH`. If it does, read it first — it contains project-specific conventions for code style, testing standards, tooling, and agent behaviour. Follow any instructions it contains throughout this task.

Read and understand the relevant code in `PROJECT_PATH` before making any changes.

Trace the execution path or data flow relevant to the task. Apply the minimum changes needed to fulfil the task correctly. Prefer editing existing files over creating new ones.

### 4c — Validate

After applying changes, check for test or build scripts in `PROJECT_PATH`:

1. Look for `package.json` scripts (`test`, `build`, `lint`, `format`, `check`)
2. Look for `Makefile` targets (`test`, `build`, `lint`)
3. Look for `pytest`, `go test`, `cargo test`, `rspec`, or similar runner config files

If any are found, run the most relevant ones (test + lint/typecheck at minimum) and report the results.

If validation **passes**: summarise the changes made and confirm the branch name, then move on to the next selected task.

If validation **fails**: report what failed with the relevant output. Ask the user whether to fix the failures or leave the branch as-is before continuing.

### 4d — Summary

After completing all selected tasks, print a summary table:

```
Task | Branch | Validation
-----|--------|------------
1. <description> | fix/<issue>-<slug> | passed / failed / skipped
...
```

Remind the user that no commits have been made — they can review the diff on each branch and commit when ready.

---

## Agent Behaviour Notes

- **Never commit automatically** — leave all changes staged or unstaged for the user to review and commit themselves.
- **One branch per task** — always create a fresh branch from the default branch for each task, even if tasks are related.
- **Stay in scope** — only make changes relevant to the specific task. Do not refactor unrelated code.
- **Respect the project** — use the project's existing code style, tooling, and conventions.
- **Be transparent** — show the commands you are running and the files you are modifying.
- **Ask before destructive actions** — if a task requires deleting files or significant restructuring, confirm with the user first.
