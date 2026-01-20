Here is the updated, integrated Product Specification (Version 2.0).

I have inserted **"The Site Survey"** as the entry protocol for **Module C (The Architect)**. This ensures that no plan is generated without first establishing the "Triangle of Scope" (Tools, Constraints, and Outcome), solving the generic planning issue we discussed.

---

# Product Specification: The Action Engine (Volition OS) v2.0

Core Philosophy:

Traditional tools manage Time (Calendars) or Lists (To-Do apps). This system manages Volition (Human Willpower). It assumes the user is biological, volatile, and prone to "loss of flow." It actively restructures tasks to match the user's reality.

---

## 1. System Architecture: The "Idea-to-Action" Pipeline

The system moves data through six distinct stages to ensure clarity before execution.

1. **Input:** Voice/Text Entry.
    
2. **The Classifier:** Sorts "Noise" from "Intent."
    
3. **The Gatekeeper:** Validates "Intent" via Stress Tests & MVP.
    
4. **The Surveyor (NEW):** Defines Context, Constraints, and Tools.
    
5. **The Architect:** Breaks "Goals" into "Milestones" and "Jobs."
    
6. **The Action Engine:** Serves "Jobs" based on Energy/State.
    
7. **The Recalibrator:** Feeds execution data back to the Architect to repair broken plans.
    

---

## 2. Module Breakdown

### Module A: The Classifier (The Sorter)

- **Logic:** Immediate semantic analysis of user input.
    
- **Routing:**
    
    - _Reflective/Emotional_ ("I feel stuck") $\rightarrow$ **The Incubator**.
        
    - _Intent/Ambition_ ("I want to learn AI") $\rightarrow$ **The Gatekeeper**.
        

### Module B: The Gatekeeper (The Validator)

- **Objective:** Prevent "Wishful Thinking" from clogging the system.
    
- **Mechanism 1: The Contextual Stress Test.**
    
    - Agent asks trade-off questions (e.g., "What will you give up to do this?").
        
- **Mechanism 2: The MVP (Minimum Viable Proof).**
    
    - Agent generates a micro-task requiring _output_ (not consumption).
        
    - _Example:_ "Write the first paragraph," not "Watch a video about writing."
        
- **Outcome:** Only goals with proven "Willingness to Act" move forward.
    

### Module C: The Architect (The Strategist)

_Now divided into two distinct phases to ensure plans are personalized, not generic._

#### **Phase 1: The Site Survey (The Scoping)**

- **Trigger:** Immediate post-Gatekeeper approval.
    
- **Objective:** Define the "Triangle of Scope" to prevent hallucinated planning.
    
- **The "Assumptive Inquiry" Protocol:**
    
    - The Agent avoids open-ended fatigue ("How do you want to do this?").
        
    - Instead, it verifies **Context**, **Constraints**, and **Tools** via targeted questions.
        
    - _Vector 1 (Tools):_ "Are we building this with your standard stack (Python/React), or exploring new tools?"
        
    - _Vector 2 (Constraints):_ "What is the hard time-cap per week? (e.g., 5 hours)."
        
    - _Vector 3 (Definition of Done):_ "Describe the finished outcome in one sentence."
        

#### **Phase 2: Fractal Decomposition (The Blueprint)**

- **Objective:** Turning the Scoped Goal into binary executable units.
    
- **The Structure:**
    
    1. **North Star:** The Goal (Ongoing).
        
    2. **Milestones:** Major phases (Locked / Active / Done).
        
    3. **Jobs:** Atomic tasks $< 2$ hours (Pending).
        
- **Logic:** "Rolling Wave Planning." The Agent only decomposes the _Active Milestone_. Future milestones remain locked/vague to reduce cognitive load.
    

### Module D: The Action Engine (The Tactician)

- **Objective:** Dynamic Execution.
    
- **The "Daily 3" Menu:**
    
    1. **The Anchor:** High Energy / Deep Work.
        
    2. **The Filler:** Medium Energy / Maintenance.
        
    3. **The Quick Win:** Low Energy / Momentum.
        
- **Selection Logic:**
    
    - _Standard:_ Pulls tasks from the **Architect's Active Milestone**.
        
    - _Crisis Override:_ If `deadline < 24h`, forces "Crisis Mode."
        
    - _Recovery Mode:_ If `user_state = BURNOUT`, serves only Quick Wins.
        

### Module E: The Recalibrator (The Self-Healing Loop)

- **Objective:** Fix the plan when execution fails.
    
- **The Escalation Ladder:**
    
    - **Level 1 (Tactical):** User delays task 1x $\rightarrow$ Action Engine reschedules.
        
    - **Level 2 (Structural):** User fails task 3x or marks "Hard" $\rightarrow$ **Wakes the Architect.** The Architect _explodes_ the task into 3 smaller sub-tasks (Re-decomposition).
        
    - **Level 3 (Strategic):** User ignores Milestone for 14 days $\rightarrow$ **Wakes the Gatekeeper.** Suggests moving Goal to Incubator (Quarantine).
        

---

## 3. The Technical Data Model (Updated)

Added `constraints` and `context` objects to support the Site Survey.

JSON

```
{
  "goal_id": "G_001",
  "title": "Build AI App",
  "state": "ACTIVE",
  "scope": {
     "hard_constraint_hours_per_week": 10,
     "preferred_tools": ["Python", "FastAPI", "React"],
     "definition_of_done": "A deployed web app that takes text input and returns a summary."
  },
  "architecture": {
    "current_milestone_index": 0,
    "milestones": [
      {
        "id": "M_1",
        "title": "Environment & Skeleton",
        "status": "ACTIVE",
        "jobs": [
          {
            "id": "J_101",
            "title": "Initialize Repo with FastAPI",
            "type": "ANCHOR",
            "status": "PENDING", 
            "metadata": {
              "deadline": null,
              "friction_score": 0
            }
          }
        ]
      }
    ]
  },
  "incubator_logs": []
}
```

---

## 4. User Experience (UX) Philosophy

- **Compass, not Map:** Focus on "What is next," not "Everything at once."
    
- **No "Overdue" Shame:** Stalled tasks are a data problem, not a character flaw.
    
- **Smart Friction:**
    
    - _Planning Phase (Architect):_ **High Friction.** The AI asks clarifying questions (The Site Survey) to ensure the plan is realistic.
        
    - _Execution Phase (Action Engine):_ **Zero Friction.** The AI serves tasks immediately without questions.
        

---

### Critical Implementation Note

The **Transition Prompts** must now handle four distinct personalities:

1. **Gatekeeper:** Skeptical, challenging. (_"Do you really want this?"_)
    
2. **Surveyor:** Inquisitive, clarifying. (_"What tools are we using? How much time do we have?"_)
    
3. **Architect:** Analytical, structured. (_"Here is the breakdown."_)
    
4. **Action Engine:** Energetic, concise. (_"Here is your first job."_)
    

---

**Would you like me to draft the specific "Assumptive Inquiry" script for the Surveyor phase next?**