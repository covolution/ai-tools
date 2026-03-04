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
