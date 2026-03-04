# AI Tools

This repository contains a curated collection of AI agents and skills designed to enhance development workflows and provide specialized capabilities for various software engineering tasks.

## Repository note

In this repository, `.claude` is the real directory and `.agent` is a symlink to `.claude`. `.kiro` is also a symlink to `.claude`. 

However, Openskills uses `.agent` but it seems most other tools use a plural `.agents`.
This keeps paths working while maintaining a single source of truth for shared skills and agent resources.

## OpenCode plugins

### 1. context-usage

A local OpenCode plugin (`.opencode/plugin/context-usage.ts`) that adds a `context_usage` tool for analysing token usage in the current session. It breaks down token consumption by category (system, user, assistant, tools, reasoning) and identifies the top contributors, helping you understand and manage context window usage.

### 2. opencode-devcontainers

An OpenCode plugin that adds devcontainer support, allowing sessions to run inside Docker-based development containers. See the [usage documentation](https://github.com/athal7/opencode-devcontainers?tab=readme-ov-file#usage) for setup instructions.  It can also work with work-trees, allowing you to run sessions in different branches or directories without affecting your main development environment.

### 3. opencode-quota

[`@slkiser/opencode-quota`](https://github.com/slkiser/opencode-quota) shows GitHub Copilot quota and token usage via toasts and slash commands (`/quota`, `/tokens_daily`, etc.), with zero context window pollution. Configured here with only the `copilot` provider enabled.

Alternatively I could consider [OpenCode MyStatus](https://github.com/vbgate/opencode-mystatus).
