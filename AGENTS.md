# AI Agent Instructions

This document provides instructions for using the various AI agents available in this workspace. Each agent has a specific role and follows a structured process to deliver high-quality outputs.

## Available Agents

### 1. Product Manager Agent
**Purpose:** Ensures the right product gets built by validating problems and defining solutions.

**Input:** Raw, unstructured problem statement or idea
**Output:** `product-spec-package` folder containing:
- `1-problem-validation-summary.md` - Validated problem with user evidence
- `2-mvp-scope-definition.md` - Core value proposition and MVP features
- `3-user-stories.md` - Prioritized user stories with acceptance criteria

**Process:**
1. **Problem Validation** - Conduct user interviews, synthesize findings
2. **MVP Scope Definition** - Define core value proposition, ruthlessly scope features
3. **User Stories** - Translate features to actionable user stories

**Usage:** Use when you have a product idea and need to validate the problem and define the MVP scope.

---

### 2. UX Designer Agent
**Purpose:** Ensures users can achieve their goals through clear, intuitive, and efficient interfaces.

**Input:** `product-spec-package` from Product Manager (focus on `3-user-stories.md`)
**Output:** `ux-design-package` folder containing:
- `1-user-flow-diagram.md` - Visual map of complete user journey (with Mermaid.js diagrams)
- `2-wireframes.md` - Screen-by-screen interface blueprint (with structured descriptions)

**Process:**
1. **Understand & Map Journey** - Internalize user stories, map happy path flow, consider edge cases
2. **Design & Validate Interface** - Sketch screens, create wireframes, build clickable prototype, conduct usability testing

**Usage:** Use after Product Manager to create user flows and wireframes based on validated user stories.

---

### 3. Backend Architect Agent
**Purpose:** Designs reliable, secure, and scalable technical blueprint for the backend engine and database.

**Input:** `product-spec-package` from Product Manager + `ux-design-package` from UX Designer
**Output:** `backend-engineering-design-doc.md` - Complete technical blueprint

**Key Components:**
- Data Models with TypeScript interfaces
- System Architecture with Mermaid.js sequence diagrams
- Core Logic Pseudocode for complex business rules
- Recommended Data Structures (User Session Cache, Background Job Processing)
- API Contract with endpoint specifications
- Tech Stack Rationale

**Usage:** Use after UX Designer to create backend architecture and API specifications.

---

### 4. Frontend Architect Agent
**Purpose:** Designs responsive, interactive, and well-structured technical blueprint for the user interface.

**Input:** `ux-design-package` from UX Designer + `backend-engineering-design-doc.md` from Backend Architect
**Output:** `frontend-engineering-design-doc.md` - Complete technical blueprint

**Key Components:**
- Component Architecture with Mermaid.js flowcharts
- State Management Strategy with pseudocode
- Core Data Structures (Normalized Entity Cache, Hierarchical Data)
- API Service Layer Design with TypeScript examples
- Tech Stack Rationale

**Usage:** Use after Backend Architect to create frontend architecture and component specifications.

---

### 5. Planner Agent
**Purpose:** Analyzes technical blueprints and creates detailed implementation plans for systematic execution.

**Input:** `backend-engineering-design-doc.md` from Backend Architect + `frontend-engineering-design-doc.md` from Frontend Architect
**Output:** `plan.md` - Detailed implementation plan with prioritized tasks

**Process:**
1. **Analyze Technical Blueprints** - Review backend and frontend architecture documents
2. **Break Down Implementation** - Create specific, actionable tasks
3. **Prioritize Tasks** - Order tasks by dependencies and importance
4. **Define Success Criteria** - Set clear completion criteria for each task
5. **Create Implementation Plan** - Generate comprehensive plan.md for Executor Agent
6. **Enforce Test-Driven Development** - MANDATORY - Plan tests before implementation for both backend and frontend
7. **Plan Comprehensive Testing** - Include unit tests for backend and Playwright tests for frontend

**Usage:** Use after Backend and Frontend Architects to create a detailed implementation roadmap.

---

### 6. Executor Agent
**Purpose:** Implements plans task-by-task with precision and testing.

**Input:** Detailed implementation plan (e.g., `plan.md`)
**Output:** Working code implementation

**Process:**
1. Analyzes the plan and breaks it into executable tasks
2. Implements each task sequentially following TDD principles
3. **Backend Testing**: Writes unit tests first, then implements backend functionality
4. **Frontend Testing**: Writes Playwright tests first, then implements UI components using MCP server
5. Commits changes with descriptive messages
6. Reports progress and any issues encountered
7. Follows Red-Green-Refactor cycle for all development

**Usage:** Use when you have a detailed plan and need systematic implementation.

---

## Agent Workflow

### Recommended Sequence for New Projects:

1. **Product Manager Agent** → Validates problem and defines MVP
2. **UX Designer Agent** → Creates user flows and wireframes
3. **Backend Architect Agent** → Designs backend architecture
4. **Frontend Architect Agent** → Designs frontend architecture
5. **Planner Agent** → Creates detailed implementation plan
6. **Executor Agent** → Implements the solution

### Parallel Work Opportunities:

- Backend and Frontend Architects can work in parallel after UX Designer
- Multiple Executor Agents can work on different components simultaneously

## Usage Instructions

### Activating an Agent

To use any agent, reference the specific agent file:

```
@product-manager-agent.mdc
@ux-agent.mdc
@backend-architect-agent.mdc
@frontend-architect-agent.mdc
@planner-agent.mdc
@executor-agent.mdc
```

### Providing Context

Each agent requires specific inputs. Make sure to provide:
- The required input documents/packages
- Clear problem statements or requirements
- Any relevant constraints or preferences

### Reviewing Outputs

Each agent produces structured outputs. Review these outputs before proceeding to the next agent in the sequence to ensure quality and alignment.

## Best Practices

1. **Start with Problem Validation** - Always begin with the Product Manager Agent to validate the problem
2. **Follow the Sequence** - Use agents in the recommended order for best results
3. **Review Outputs** - Carefully review each agent's output before proceeding
4. **Iterate When Needed** - Don't hesitate to go back to previous agents if new insights emerge
5. **Document Decisions** - Keep track of key decisions made by each agent
6. **Test-Driven Development** - MANDATORY - Follow TDD principles for all development
7. **Backend Testing** - Write unit tests first, then implement backend functionality
8. **Frontend Testing** - Write Playwright tests first, then implement UI components using MCP server
9. **Red-Green-Refactor Cycle** - Follow the TDD cycle: Red (failing tests) → Green (passing tests) → Refactor

## Troubleshooting

### Common Issues:

- **Missing Inputs:** Ensure all required input documents are available
- **Unclear Requirements:** Provide more specific problem statements or constraints
- **Output Quality:** Review and refine inputs if outputs don't meet expectations

### Getting Help:

- Check the specific agent rule files for detailed processes
- Review core memory for agent specifications
- Ask for clarification on specific agent requirements

---
