Here is your refined product specification. I have synthesized our entire discussion—replacing the rigid tables with conversational AI, the complex calendar with the "Daily 3" menu, and the vague thoughts process with the "Incubator."

This is no longer just a "To-Do List"; it is a **Commitment Engine**.

---

# Product Concept: The "Commitment Filter"

**Core Philosophy:** Most ideas are noise. Only ideas that survive a "stress test" deserve to be goals. The app focuses on **verifying willingness** before tracking execution.

## 1. The Entry Point (The Classifier)

User Input: Voice or Text (e.g., "I want to make a million dollars" or "I feel like a failure").

Agent Logic: Instantly classifies the input into two buckets:

1. **Actionable Intent:** Triggers the [Gatekeeper Process].
    
2. **Reflective Thought:** Triggers the [Incubator Process].
    

---

## 2. The Gatekeeper (Formerly "Review Phase")

_Instead of a static form, the Agent acts as a gentle skeptic._

### The Conversational Stress Test

The Agent uses user context (Past Patterns, Current Load) to generate 3-5 punchy, realistic questions. It does not show a score to the user; it calculates it in the background.

- **Goal:** Assess **Difficulty Tolerance** & **Intrinsic Drive**.
    
- **The "Context-Aware" logic:**
    
    - _If User is busy:_ Ask about trade-offs ("What current project will you drop to do this?").
        
    - _If User has failed before:_ Ask about specific pain points ("You quit guitar because of finger pain. This requires calluses too. Ready for that?").
        

### The Decision Logic (Hidden Backend)

- **High Score (Go):** Proceed to **Test Phase**.
    
- **Low Score (No-Go):** The Agent says, _"This seems like a 'Nice to Have' rather than a 'Must Do' right now. Let’s put it in the Incubator for later."_ (Soft rejection).
    

---

## 3. The Proving Ground (Formerly "Test Phase")

_Verifying willingness through Action, not promises._

### The MVP Generator

The Agent breaks the goal down into a **"Proof of Work"**—a micro-task that requires tangible output.

- **Rule:** No passive consumption (e.g., "Watch video"). Only active creation.
    
- **Examples:**
    
    - _Goal:_ "Learn Coding." $\rightarrow$ _MVP:_ "Write an HTML file that displays a red box."
        
    - _Goal:_ "Write a Book." $\rightarrow$ _MVP:_ "Write a 300-word outline of the villain."
        

### The "Feynman" Verification

When the user clicks "Done," the Agent asks for a 1-sentence synthesis: _"Explain the core concept you just learned to a 5-year-old."_ This ensures the user didn't just cheat the system.

---

## 4. The Action Engine (Formerly "Action Phase")

_Replacing "Calendar Management" with "Energy Management."_

### The "Daily 3" Menu (Scheduling)

Every morning, the Agent serves a curated menu based on the user's energy and available time slots. It prevents burnout by enforcing variety.

1. **The Anchor (High Energy):** The deep work task. (e.g., "Code the login feature").
    
2. **The Filler (Medium Energy):** Maintenance work. (e.g., "Read 10 pages").
    
3. **The Quick Win (Low Energy):** Momentum starter. (e.g., "Reply to 1 email").
    

### The Context Trigger

Instead of strict times (2:00 PM), the Agent uses **State-Based Triggers**:

- _User:_ "I have 15 mins." $\rightarrow$ _Agent:_ "Do the **Quick Win** task."
    
- _User:_ "I'm tired." $\rightarrow$ _Agent:_ "Skip the Anchor. Just do the **Filler** task to keep the streak."
    

### The Feedback Loop (Data Collection)

- **Micro-Tags:** After an Anchor task, show 3 buttons: 🟢 (Easy), 🟡 (Okay), 🔴 (Hard).
    
- **Dynamic Difficulty Adjustment:**
    
    - _If "Hard" 3x in a row:_ Agent suggests breaking the task down further.
        
    - _If "Easy" 3x in a row:_ Agent suggests increasing the challenge to maintain flow.
        

---

## 5. The Incubator (Formerly "Thoughts Process")

_Handling non-actionable thoughts without judgment._

### The Quarantine Protocol

- **Subjective Thoughts:** (e.g., "I'm stupid.")
    
    - **Action:** Record as "Belief Tag," not Fact.
        
    - **Response:** Socratic Mirroring. _"I've logged that you feel stuck. What specific evidence makes you feel that way today?"_
        
- **Factual Errors:** (e.g., "I will sleep 2 hours.")
    
    - **Action:** Gentle correction with data. _"Data shows productivity drops after 18h awake. Shall we set a 'Crash Limit'?"_
        

### Context Mining

The Agent periodically reviews the Incubator:

- _"You’ve had 'Learn Pottery' in the incubator for 6 months. You mentioned you're bored on weekends—is it time to move this to the Review Phase?"_
    

---

## Technical Data Model (JSON Structure)

To build this, your database objects should look like this:

JSON

```
{
  "item_id": "102",
  "type": "ACTION_MVP", // or THOUGHT_VENT
  "content": "Learn Python",
  "status": {
    "state": "ACTIVE",
    "difficulty_score": 75, // 0-100 Dynamic Score
    "energy_tag": "HIGH_FOCUS"
  },
  "proof_of_work": {
    "required_output": "Print 'Hello World' in terminal",
    "verification_method": "FEYNMAN_TEST"
  },
  "feedback_log": [
    {"date": "2023-10-01", "mood": "TIRED", "effort": "HARD"}
  ]
}
```

### Next Immediate Step

This specification is now solid. The biggest risk is the **Prompt Engineering**—if the Agent's "Review Questions" are boring, the app fails.

**Would you like me to write the final "Master System Prompt" that controls the Gatekeeper (Review Phase)?**