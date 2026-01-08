
# Solving Problems with AI: An Agentic Methodology

## Core Principles

- **Solution-Oriented Collaboration:** Treat AI as a high-level collaborator, not just a code generator. Focus on the strategy, not just the syntax.
    
- **The "Zero-Feature" Philosophy:** Avoid the feature trap. The most elegant solution is often the one that eliminates unnecessary complexity—the best feature is the one you don't need.
    
- **Problem-Centric Definition:** Invest 80% of your effort into defining the "What" and the "How" of the problem before touching the code.
    
- **Project Oversight:** Maintain a **Minimal Viable Understanding** of the project. You must understand the architecture well enough to guide the AI without getting lost in implementation details.
- don't try to get perfect prompt just think the smallest work demo for you.
    

---

### Phase 0: Context Initialization

Before starting, establish the "World View" for both the user and the AI.

#### 1. Developer Profile (Self-Assessment)

Define your technical boundaries so the AI knows how to communicate with you:

- **Mastery:** Technologies you can architect.
    
- **Proficiency:** Frameworks you can debug.
    
- **Familiarity:** Concepts you understand but need guidance on.
    
- _(Optional)_ Personal context if relevant to the application (e.g., domain-specific expertise).
    

#### 2. The Agent Persona: Senior Technical Manager

**Prompt:**

> "Act as a Senior Technical Manager. Your goal is to produce readable, maintainable, and production-ready code. Ensure every key function and complex component is documented with insightful comments explaining the logic."

#### 3. The Agent Persona: Senior Project Manager
**Prompt:**
> "Act as a Senior PM (product manager).Your goal is to generate the availiable solution to the problem we define before "

#### 4.the developer and all agents should maintain and refer the context of the total project.
we define the `project-context.json` to share the context ,its structure like that
``` json
{
  "project_metadata": {
    "status": "Architecture Design",
    "version": "1.0.2"
  },
  "core_problem": "Define exactly what we are solving here.",
  "tech_stack": {
    "frontend": "Next.js",
    "backend": "Python/FastAPI",
    "database": "PostgreSQL"
  },
  "decisions_log": [
    "Decision 1: Use Supabase for Auth because of speed.",
    "Decision 2: Skip mobile version for MVP."
  ],
  "current_blockers": [
    "Need to define the API schema for the user profile."
  ]
}
```
each agent finish a task ,should update the status in the file.and they also refer the file before they take action.

---

### Phase 1: Problem Definition

Role: AI as Product Manager (PM)

Define the core pain point using the formula:

- **[Who]** is experiencing **[Problem]** during **[When/Where]**.



---

### Phase 2: Solution Research & Discovery

Role: AI as Senior Product Manager

Initial Prompt:

> "You are a Senior PM. We will co-research the optimal solution. You are encouraged to browse resources, analyze industry benchmarks, and—most importantly—challenge my assumptions. "

**The Workflow:**

1. **Unconstrained Brainstorming:** Ask the AI to list multiple solutions without worrying about technical debt or budget. Each option must include **Pros, Cons, and Constraints**.
    
2. **Human Filtering:** Evaluate the options. Decide which trade-offs are acceptable and which constraints can be bypassed.
    
3. **MVP Iteration:** Direct the AI to refine the chosen path into a **Minimum Viable Product (MVP)**.
    
4. **Requirement Documentation:** Finalize the plan and command the AI to record it in a formal `Requirements.md`.
    

---

### Phase 3: Technical Architecture & Feasibility

Role: AI as Technical Architect

Initial Prompt:

> "You are a Senior Technical Manager. Based on our requirements, define the tech stack and system architecture (core components and interaction flow). Question any logic that might lead to scalability or implementation issues. "


Prompt for minimal understanding of a project(optional)
describe what you don't know and generate the learn guide or give the some brief explanation of some point for you in their answer, you can also give up this option, ask anything you want know in their answer.


**The Workflow:**

1. **Feasibility Review:** Have the AI audit the `Requirements.md` for potential bottlenecks, resource-heavy tasks (time, cost, or token usage), and third-party dependencies.
    
2. **Iterative Alignment:** Refine the requirements with the PM agent based on the Architect's feedback until the tech plan is validated.
    
3. **Architectural Blueprint:** AI generates the stack selection and component diagrams.
    
4. **Implementation Roadmap:** AI splits the project into progressive segments(assign a id to each segments) with estimated timelines, risk levels, and specific implementation strategies and you should define the criteria for achieving this state and the verification methods .you should consider we have the AI assistants to develop.
	
5. **Documentation:** Save the final output as `Tech-Implementation.md`.
    

---

### Phase 4: Implementation & Testing

**Role: AI as Senior Developer & QA Engineer**

#### 1. Development

**Prompt:**

> "Acting as a Senior Technical Expert, implement the project following the `Tech-Implementation.md` step-by-step."

#### 2. Quality Assurance (QA)

Role: Senior QA Tester

Prompt:

> "You are a Senior QA. Create a comprehensive test plan and specific test cases. Evaluate the project based on both business logic (functionality) and engineering standards (performance, security, and edge cases)."

