# Volition OS - Master Technical Specification

> **AI INSTRUCTIONS:**
> 1. This is the Source of Truth. Do not deviate from the Database Schema or Logic Flow.
> 2. Critical Rules:
>    - NEVER simplify "Module C" (The Architect). It must run in 3 distinct steps.
>    - NEVER simplify "Module D" (The Action Engine). It must filter by Energy Level.
>    - Use Next.js Server Actions for all backend logic.

## 1. Project Overview
**Product:** Volition OS (The Action Engine)
**Core Philosophy:** Manage Biological Energy (Volition), not just Time. Decompose goals into "edible" units based on current energy state.
**MVP Scope:** Input -> Architect -> Action Engine loop. No social/gamification features.

## 2. Technical Stack
- **Frontend:** Next.js 14+ (App Router), TailwindCSS, Shadcn/UI, Lucide Icons.
- **Backend:** Next.js Server Actions.
- **Database:** Supabase (PostgreSQL).
- **AI/LLM:** OpenAI API (GPT-4o) via Vercel SDK.
- **State:** React Query (TanStack Query).

## 3. Database Schema (Supabase)
*Strictly enforce this schema. Do not add fields without permission.*

```sql
-- 1. PROJECTS (The High Level Goals)
create table projects (
  id uuid default gen_random_uuid() primary key,
  user_id uuid references auth.users not null,
  title text not null,
  complexity text check (complexity in ('S', 'M', 'L', 'XL')),
  total_est_hours int,
  status text default 'ACTIVE',
  created_at timestamp with time zone default now()
);

-- 2. PHASES (For Large Projects - The "Chapters")
create table phases (
  id uuid default gen_random_uuid() primary key,
  project_id uuid references projects on delete cascade,
  title text not null,
  order_index int not null,
  status text default 'LOCKED'
);

-- 3. MILESTONES (Major Deliverables)
create table milestones (
  id uuid default gen_random_uuid() primary key,
  phase_id uuid references phases on delete cascade,
  title text not null,
  status text default 'LOCKED'
);

-- 4. CLUSTERS (The "Miller's Law" groupings)
create table job_clusters (
  id uuid default gen_random_uuid() primary key,
  milestone_id uuid references milestones on delete cascade,
  title text not null,
  theme text,
  is_active boolean default false
);

-- 5. JOBS (The Atomic Units)
create table jobs (
  id uuid default gen_random_uuid() primary key,
  cluster_id uuid references job_clusters on delete cascade,
  title text not null,
  energy_level text check (energy_level in ('QUICK_WIN', 'DEEP_WORK', 'ANCHOR')),
  est_minutes int default 15,
  status text default 'PENDING', -- 'PENDING', 'DONE', 'SKIPPED'
  is_crisis boolean default false
);