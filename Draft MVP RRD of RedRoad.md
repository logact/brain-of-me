This is a complete **Master Product Requirement Document (PRD)** designed specifically for an AI coding agent (like Cursor, Windsurf, or a Senior Dev) to read and implement.

It preserves the full complexity of **Module C** and **Module D** as requested.

You can copy-paste the entire block below into a file named `cursor_rules.md` or `spec.md` in your project root, and then ask Cursor to "Read spec.md and start Phase 1."

---

# Volition OS (MVP) - Master Technical Specification

## 1. Project Overview

Product: Volition OS (The Action Engine)

Core Philosophy: A productivity tool that manages Biological Energy (Volition), not just Time. It uses AI to decompose large goals into atomic "edible" units and serves them based on the user's current energy state.

MVP Scope: Focus strictly on the "Input $\rightarrow$ Architect $\rightarrow$ Action Engine" loop. No social features, no voice mode, no gamification yet.

## 2. Technical Stack

- **Frontend:** Next.js 14+ (App Router), TailwindCSS, Shadcn/UI, Lucide Icons.
    
- **Backend:** Next.js Server Actions (API Routes).
    
- **Database:** Supabase (PostgreSQL).
    
- **AI/LLM:** OpenAI API (GPT-4o) or Anthropic (Claude 3.5 Sonnet) via Vercel SDK.
    
- **State Management:** React Query (TanStack Query) for async operations.
    

---

## 3. Database Schema (Supabase)

The schema supports the "Fractal" nature of Module C (Projects > Phases > Milestones > Clusters > Jobs).

SQL

```
-- 1. PROJECTS (The High Level Goals)
create table projects (
  id uuid default gen_random_uuid() primary key,
  user_id uuid references auth.users not null,
  title text not null,
  complexity text check (complexity in ('S', 'M', 'L', 'XL')), -- Set by Module C
  total_est_hours int,
  status text default 'ACTIVE',
  created_at timestamp with time zone default now()
);

-- 2. PHASES (For Large Projects - The "Chapters")
create table phases (
  id uuid default gen_random_uuid() primary key,
  project_id uuid references projects on delete cascade,
  title text not null, -- e.g., "MVP Core", "Scale"
  order_index int not null,
  status text default 'LOCKED' -- 'ACTIVE', 'DONE', 'LOCKED'
);

-- 3. MILESTONES (Major Deliverables)
create table milestones (
  id uuid default gen_random_uuid() primary key,
  phase_id uuid references phases on delete cascade,
  title text not null, -- e.g., "Auth & DB Setup"
  status text default 'LOCKED'
);

-- 4. CLUSTERS (The "Miller's Law" groupings)
create table job_clusters (
  id uuid default gen_random_uuid() primary key,
  milestone_id uuid references milestones on delete cascade,
  title text not null, -- e.g., "Supabase Config"
  theme text, -- e.g., "Backend", "Frontend"
  is_active boolean default false
);

-- 5. JOBS (The Atomic Units)
create table jobs (
  id uuid default gen_random_uuid() primary key,
  cluster_id uuid references job_clusters on delete cascade,
  title text not null, -- e.g., "Run npm install"
  energy_level text check (energy_level in ('QUICK_WIN', 'DEEP_WORK', 'ANCHOR')),
  est_minutes int default 15,
  status text default 'PENDING', -- 'PENDING', 'DONE', 'SKIPPED'
  is_crisis boolean default false -- For Module D "Crisis" filter
);
```

---

## 4. Module Specifications & Logic Flow

### Module A & B: Input & Gatekeeper

- **User Flow:** User enters a raw idea (e.g., "Build a SaaS app").
    
- **Logic:**
    
    1. LLM analyzes input.
        
    2. If input is vague, generate a "Gateway Task" (MVP Proof).
        
    3. _Constraint:_ The user **MUST** check off this single task (e.g., "Create Github Repo") before the Project is saved to DB.
        

### Module C: The Adaptive Architect (The AI Pipeline)

_Critical System:_ Do not simplify. This runs in 3 distinct steps to ensure accuracy.

**Step 1: The Sizer (API: `/api/architect/size`)**

- **Prompt Role:** "Senior Technical Project Manager."
    
- **Input:** Project Title + User Constraints.
    
- **Output:** JSON `{ complexity: "L", est_hours: 150, strategy: "PHASED" }`.
    

**Step 2: The Structural Blueprint (API: `/api/architect/structure`)**

- **Input:** Output from Step 1.
    
- **Task:** Generate **Phases** and **Milestones** only.
    
- **Constraint:** Do not generate Jobs yet. Keep it high level.
    

**Step 3: The Atomic Decomposer (API: `/api/architect/decompose`)**

- **Trigger:** Triggered _only_ for the first Active Milestone immediately. Future milestones are decomposed "Just In Time" (when the user unlocks them).
    
- **Task:** Break the Milestone into **Job Clusters** (groupings) and **Jobs**.
    
- **Rule:** Max 7 jobs per cluster (Miller's Law).
    
- **Tagging:** Every job must have an `energy_level` tag (`QUICK_WIN`, `DEEP_WORK`).
    

### Module D: The Action Engine (The Serving Logic)

_Critical System:_ This replaces the traditional "To-Do List" view.

**The UI:**

- A Dashboard with "State Toggles": `[⚡ High Energy]` `[🔋 Normal]` `[🪫 Low Energy]` `[🔥 Crisis]`.
    
- A "Single Card" display area (The Deck).
    

**The Logic (SQL Query):**

1. **Check Crisis:** IF `Crisis` toggle is ON, select jobs where `is_crisis = true`.
    
2. **Filter by Active Cluster:** Select jobs ONLY from `job_clusters` where `is_active = true`. (Prevents context switching).
    
3. **Filter by Energy:**
    
    - If `Low Energy`: Select `energy_level = 'QUICK_WIN'`.
        
    - If `High Energy`: Select `energy_level = 'DEEP_WORK'`.
        
4. **Sort:** By `order_index` ASC.
    
5. **Limit:** Return 1 Job.
    

---

## 5. Development Roadmap for Cursor

This is the step-by-step instruction set for the AI Agent.

### Phase 1: Foundation (Setup)

1. Initialize Next.js project with Typescript, Tailwind, Shadcn.
    
2. Set up Supabase client and run the SQL Schema provided in Section 3.
    
3. Create TypeScript Interfaces for `Project`, `Milestone`, `Job`.
    

### Phase 2: The Architect (Backend)

1. Create the `server actions` for OpenAI/Claude integration.
    
2. Implement **Step 1 (Sizer)**: Write a prompt that takes a string and returns the Complexity JSON.
    
3. Implement **Step 2 (Structure)**: Write a prompt that takes the Complexity JSON and inserts rows into `Phases` and `Milestones` tables.
    
4. Implement **Step 3 (Decomposition)**: Write the prompt that generates `Clusters` and `Jobs` for a specific Milestone ID.
    

### Phase 3: The Action Engine (Frontend)

1. Build the `FocusMode` component (The Card View).
    
2. Implement the "Energy Toggles" (State).
    
3. Write the `fetchNextJob` function that calls Supabase with the specific filtering logic defined in Module D.
    
4. Add "Complete" and "Skip" buttons. "Complete" updates DB `status='DONE'` and fetches the next card.
    

### Phase 4: The Glue (Input Flow)

1. Build the Landing Page input box.
    
2. Connect input to the "Gatekeeper" logic (Modal pop-up for the first task).
    
3. On success, trigger the Architect pipeline and redirect to `FocusMode`.
    

---

## 6. Prompt Engineering (Reference for Agent)

**System Prompt for Step 3 (Decomposer):**

> "You are an expert Engineer. You have been given a Milestone: '{milestone_title}'.
> 
> 1. Group the necessary work into logical 'Clusters' (e.g., Setup, Logic, UI).
>     
> 2. Inside each cluster, list atomic tasks (under 2 hours).
>     
> 3. Assign an energy tag to each: 'QUICK_WIN' (low effort) or 'DEEP_WORK' (high focus).
>     
> 4. Return strictly valid JSON structure matching the database schema."
>     

---

## 7. Success Criteria

1. User enters "Build a Portfolio".
    
2. System requires them to "Create Folder" first (Gatekeeper).
    
3. System takes ~20s to generate a multi-tier plan in DB.
    
4. User sees a card saying "Install React" (Quick Win).
    
5. User toggles "High Energy" -> Card changes to "Design Component Structure" (Deep Work).