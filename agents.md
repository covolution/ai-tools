# AI Tools - Agents & Skills

This repository contains a curated collection of AI agents and skills designed to enhance development workflows and provide specialized capabilities for various software engineering tasks.

## Repository Structure

```
ai-tools/
├── .agents/                              # Main agents and skills directory
│   └── skills/                          # Individual skill modules
│       ├── architect-refine-critique/    # Multi-phase architecture design review
│       ├── c4-architecture/              # C4 model architecture diagrams
│       ├── commit-work/                  # Git commit and change staging
│       ├── lightweight-design-analysis/  # Code design quality assessment
│       ├── lightweight-implementation-analysis-protocol/  # Implementation flow analysis
│       └── mermaid-diagrams/             # Software diagram generation
├── .claude/                              # Symlink to .agents (for CLI compatibility)
└── README.md                             # Main repository documentation
```

## Available Skills

### 1. **Architect-Refine-Critique** 
   - **Purpose**: Multi-phase design review workflow using chained subagents
   - **Triggers**: Design reviews, architecture reviews, significant refactoring, new service/module design
   - **Capabilities**: 
     - Architect phase: Initial design proposal analysis
     - Refiner phase: Design refinement recommendations
     - Critique phase: Quality assessment and feedback

### 2. **C4 Architecture**
   - **Purpose**: Generate architecture documentation using C4 model and Mermaid diagrams
   - **Triggers**: Architecture diagrams, system design documentation, visual structure representation
   - **Diagram Types**:
     - Context diagrams (systems and external entities)
     - Container diagrams (high-level application structure)
     - Component diagrams (internal component organization)
     - Deployment diagrams (runtime environment structure)

### 3. **Commit Work**
   - **Purpose**: Create high-quality Git commits with structured messaging
   - **Triggers**: Git commits, commit message crafting, change staging
   - **Capabilities**:
     - Review and stage intended changes
     - Split work into logical commits
     - Write clear commit messages (including Conventional Commits)

### 4. **Lightweight Design Analysis**
   - **Purpose**: Evaluate code design quality across multiple dimensions
   - **Analysis Dimensions**:
     1. Naming conventions
     2. Object Calisthenics
     3. Coupling & Cohesion
     4. Immutability patterns
     5. Domain Integrity
     6. Type System usage
     7. Simplicity and clarity
     8. Performance considerations
   - **Triggers**: Code analysis requests, design reviews, refactoring opportunities

### 5. **Lightweight Implementation Analysis Protocol**
   - **Purpose**: Understand code execution flow before making changes
   - **Features**:
     - Trace execution paths with file:line references
     - Create lightweight text diagrams showing class.method() flows
     - Verify understanding with users before implementation
   - **Prevents**: Wasted effort from incorrect assumptions
   - **Triggers**: Bug fixes, feature implementations, debugging, TDD cycles

### 6. **Mermaid Diagrams**
   - **Purpose**: Create comprehensive software diagrams using Mermaid syntax
   - **Diagram Types**:
     - Class diagrams (domain modeling, OOP design)
     - Sequence diagrams (application flows, API interactions)
     - Flowcharts (processes, algorithms, user journeys)
     - Entity relationship diagrams (database schemas)
     - State diagrams (state machines)
     - Git graphs (commit history)
     - Pie/Gantt charts (data visualization)
   - **Triggers**: Visualization requests, system flow mapping, database design documentation

## Skill Management

## Usage Examples

### Design Review Workflow
```
Request: "Can you do a design review of my microservice architecture?"
→ Triggers: architect-refine-critique skill
→ Output: Multi-phase review with architect, refiner, and critique feedback
```

### Architecture Visualization
```
Request: "Generate a C4 architecture diagram for my system"
→ Triggers: c4-architecture skill
→ Output: Context, container, component, and deployment diagrams
```

### Implementation Planning
```
Request: "Help me debug this issue in the authentication flow"
→ Triggers: lightweight-implementation-analysis-protocol skill
→ Output: Execution flow trace with file:line references
```

### Code Quality Assessment
```
Request: "Analyze the design quality of this module"
→ Triggers: lightweight-design-analysis skill
→ Output: Comprehensive analysis across 8 design dimensions
```

### Git Workflow
```
Request: "Help me create a clean commit from these changes"
→ Triggers: commit-work skill
→ Output: Staged changes with well-structured commit messages
```

## Key Design Principles

1. **Modularity**: Each skill is self-contained and independently maintainable
2. **Composability**: Skills can be chained together for complex workflows
3. **Versioning**: Skills are locked to ensure reproducible behavior
4. **Documentation**: Each skill includes detailed purpose and trigger information
5. **Single Responsibility**: Each skill focuses on a specific capability

---

For detailed information about specific skills, see the individual skill directories in `.agents/skills/`.

<skills_system priority="1">

## Available Skills

<!-- SKILLS_TABLE_START -->
<usage>
When users ask you to perform tasks, check if any of the available skills below can help complete the task more effectively. Skills provide specialized capabilities and domain knowledge.

How to use skills:
- Invoke: `npx openskills read <skill-name>` (run in your shell)
  - For multiple: `npx openskills read skill-one,skill-two`
- The skill content will load with detailed instructions on how to complete the task
- Base directory provided in output for resolving bundled resources (references/, scripts/, assets/)

Usage notes:
- Only use skills listed in <available_skills> below
- Do not invoke a skill that is already loaded in your context
- Each skill invocation is stateless
</usage>

<available_skills>

<skill>
<name>architect-refine-critique</name>
<description>"Three-phase design review. Chain architect → refiner → critique subagents. Triggers on: 'design review', 'architecture review', '/arc', system design proposals, significant refactoring decisions, new service or module design."</description>
<location>project</location>
</skill>

<skill>
<name>c4-architecture</name>
<description>Generate architecture documentation using C4 model Mermaid diagrams. Use when asked to create architecture diagrams, document system architecture, visualize software structure, create C4 diagrams, or generate context/container/component/deployment diagrams. Triggers include "architecture diagram", "C4 diagram", "system context", "container diagram", "component diagram", "deployment diagram", "document architecture", "visualize architecture".</description>
<location>project</location>
</skill>

<skill>
<name>commit-work</name>
<description>"Create high-quality git commits: review/stage intended changes, split into logical commits, and write clear commit messages (including Conventional Commits). Use when the user asks to commit, craft a commit message, stage changes, or split work into multiple commits."</description>
<location>project</location>
</skill>

<skill>
<name>difficult-workplace-conversations</name>
<description>Structured approach to workplace conflicts, performance discussions, and challenging feedback using preparation-delivery-followup framework. Use when preparing for tough conversations, addressing conflicts, giving critical feedback, or navigating sensitive workplace discussions.</description>
<location>project</location>
</skill>

<skill>
<name>draw-io</name>
<description>draw.io diagram creation, editing, and review. Use for .drawio XML editing, PNG conversion, layout adjustment, and AWS icon usage.</description>
<location>project</location>
</skill>

<skill>
<name>lightweight-design-analysis</name>
<description>"This skill analyzes code for design quality improvements across 8 dimensions: Naming, Object Calisthenics, Coupling & Cohesion, Immutability, Domain Integrity, Type System, Simplicity, and Performance. Ensures rigorous, evidence-based analysis by: (1) Understanding code flow first via implementation-analysis protocol, (2) Systematically evaluating each dimension with specific criteria, (3) Providing actionable findings with file:line references. Triggers when users request: code analysis, design review, refactoring opportunities, code quality assessment, architecture evaluation."</description>
<location>project</location>
</skill>

<skill>
<name>lightweight-implementation-analysis-protocol</name>
<description>"This skill should be used when fixing bugs, implementing features, debugging issues, or making code changes. Ensures understanding of code flow before implementation by: (1) Tracing execution path with specific file:line references, (2) Creating lightweight text diagrams showing class.method() flows, (3) Verifying understanding with user. Prevents wasted effort from assumptions or guessing. Triggers when users request: bug fixes, feature implementations, refactoring, TDD cycles, debugging, code analysis."</description>
<location>project</location>
</skill>

<skill>
<name>mermaid-diagrams</name>
<description>Comprehensive guide for creating software diagrams using Mermaid syntax. Use when users need to create, visualize, or document software through diagrams including class diagrams (domain modeling, object-oriented design), sequence diagrams (application flows, API interactions, code execution), flowcharts (processes, algorithms, user journeys), entity relationship diagrams (database schemas), C4 architecture diagrams (system context, containers, components), state diagrams, git graphs, pie charts, gantt charts, or any other diagram type. Triggers include requests to "diagram", "visualize", "model", "map out", "show the flow", or when explaining system architecture, database design, code structure, or user/application flows.</description>
<location>project</location>
</skill>

</available_skills>
<!-- SKILLS_TABLE_END -->

</skills_system>
