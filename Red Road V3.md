This is the final, crystallized Product Specification for **"The Action Engine."**

It integrates every component we have discussed: the filtering of noise, the validation of intent, the structural decomposition of goals, the energy-based execution, and the self-healing feedback loop.

---

# Product Specification: The Action Engine (Volition OS)

Core Philosophy:

Traditional tools manage Time (Calendars) or Lists (To-Do apps). This system manages Volition (Human Willpower). It assumes the user is biological, volatile, and prone to "loss of flow." It does not just track tasks; it actively restructures them to match the user's reality.

---

## 1. System Architecture: The "Idea-to-Action" Pipeline

The system moves data through five distinct stages.

1. **Input:** Voice/Text Entry.
    
2. **The Classifier:** Sorts "Noise" from "Intent."
    
3. **The Gatekeeper:** Validates "Intent" via Stress Tests & MVP.
    
4. **The Architect (Strategy):** Breaks "Goals" into "Milestones" and "Jobs."
    
5. **The Action Engine (Tactics):** Serves "Jobs" based on Energy/State.
    
6. **The Recalibrator (Loop):** Feeds execution data back to the Architect to repair broken plans.
    

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
    
    - Agent asks 3 trade-off questions (e.g., "What will you give up to do this?").
        
- **Mechanism 2: The MVP (Minimum Viable Proof).**
    
    - Agent generates a micro-task requiring _output_ (not consumption).
        
    - _The Feynman Test:_ User must explain the concept simply to pass.
        
- **Outcome:** Only goals with proven "Willingness to Act" move to the Architect.
    

### Module C: The Architect (The Strategist)

- **Objective:** Fractal Decomposition. Turning vague goals into binary executable units.
    
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
        
    - _Crisis Override:_ If `deadline < 24h`, ignores energy levels and forces "Crisis Mode."
        
    - _Recovery Mode:_ If `user_state = BURNOUT`, serves only Quick Wins.
        

### Module E: The Recalibrator (The Self-Healing Loop)

- **Objective:** Fix the plan when execution fails.
    
- **The Escalation Ladder:**
    
    - **Level 1 (Tactical):** User delays task 1x. $\rightarrow$ Action Engine reschedules.
        
    - **Level 2 (Structural):** User fails task 3x or marks "Hard." $\rightarrow$ **Wakes the Architect.** The Architect _explodes_ the task into 3 smaller sub-tasks (Re-decomposition).
        
    - **Level 3 (Strategic):** User ignores Milestone for 14 days. $\rightarrow$ **Wakes the Gatekeeper.** Suggests moving Goal to Incubator (Quarantine).
        

---

## 3. The Technical Data Model

This JSON structure supports the hierarchical decomposition and the bi-directional feedback loop.

JSON

```
{
  "goal_id": "G_001",
  "title": "Build AI App",
  "state": "ACTIVE",
  "architecture": {
    "current_milestone_index": 0,
    "milestones": [
      {
        "id": "M_1",
        "title": "Database Schema",
        "status": "ACTIVE",
        "jobs": [
          {
            "id": "J_101",
            "title": "Code User Table",
            "type": "ANCHOR",
            "status": "STALLED", 
            "metadata": {
              "deadline": null,
              "friction_score": 3, // Increased every time user fails/skips
              "user_feedback": ["Too complex", "Need to learn SQL"] 
            }
          }
        ]
      },
      {
        "id": "M_2",
        "title": "Frontend UI",
        "status": "LOCKED",
        "jobs": [] // Empty until M_1 is done
      }
    ]
  },
  "incubator_logs": [] // Stores thoughts/vents related to this goal
}
```

---

## 4. User Experience (UX) Philosophy

- **The Interface acts as a Compass, not a Map.** It shows you "What is next," not "Everything at once."
    
- **No "Overdue" Shame.** Tasks are not marked red/overdue; they are marked "Stalled" and treated as a data problem, not a character flaw.
    
- **Conversational Friction.** The AI pauses the user during planning (Architect Mode) to ensure clarity, but removes all friction during execution (Action Mode).
    

---

### Critical Implementation Note

The success of this product relies entirely on the **transition prompts**. The user must feel the shift in the AI's personality:

1. **Gatekeeper:** Skeptical, challenging.
    
2. **Architect:** Analytical, structured, patient.
    
3. **Action Engine:** Energetic, concise, forgiving.
    

**This is the complete product vision.**

Would you like me to create the **"Prompt System"** for the **Recalibration/Feedback Loop**? This is the specific logic script the AI uses when it detects a user is "Stuck" (Level 2 Escalation) and needs to decompose a task.