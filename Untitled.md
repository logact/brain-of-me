
## 1. The "Clean File" Structure

Every code file, regardless of language, should follow this vertical flow to make navigation predictable:

1. **Imports/Dependencies:** Grouped by (External Libraries) then (Internal Files).
    
2. **Constants & Configurations:** Hardcoded values that won't change.
    
3. **Core Logic / Primary Class:** The "Meat" of the file.
    
4. **Helper Functions:** Small, private functions used by the core logic.
    
5. **Exports/Entry Point:** How the file interfaces with the rest of the system.
    

---

## 2. Naming Standard (The 3-Second Rule)

If you cannot understand what a variable holds within 3 seconds of looking at it, the name is too short or too vague.

- **Variables:** Use **Nouns** to describe the _data_ (`userEmail`, `retryCount`).
 
- **Functions:** Use **Verbs** to describe the _action_ (`calculateTotal()`, `isAuthorized()`).
    
- **Booleans:** Must sound like a **Yes/No Question** (`isValid`, `hasToken`, `shouldRedirect`).
    
- **Collections:** Use plurals (`users`, `items`) or suffixes (`userList`, `productMap`).
    

---

## 3. The "Anti-Complexity" Rules

These rules prevent "Spaghetti Code" which is the biggest threat to a solo developer's productivity.

### A. The "One-Thing" Rule

A function should do **one** thing, do it **well**, and do it **only**.

- If your function name has "And" in it (e.g., `validateAndSaveUser`), split it into two functions.
    

### B. The "Small is Beautiful" Rule

- **Functions:** Aim for < 20 lines.
    
- **Files:** Aim for < 300 lines. If a file gets bigger, it’s usually a sign that it should be broken into smaller modules.
    

### C. Guard Clauses (Flat over Nested)

Avoid "Arrow Code" where your logic drifts to the right side of the screen due to nested `if` statements.

|**Avoid (Nested)**|**Prefer (Guard Clause)**|
|---|---|
|`if (user) {`|`if (!user) return;`|
|`if (user.active) {`|`if (!user.active) return;`|
|`// logic here`|`// logic here (No indent!)`|
|`}`||
|`}`||

---

## 4. Documentation for "Future You"

Since you have no teammates, comments are notes to yourself 6 months from now.

- **Don't comment the "What":** `x = x + 1; // Increment x` (This is noise).
    
- **Do comment the "Why":** `// We increment by 1 to skip the header row in the CSV.` (This is context).
    
- **The "Hacks" Warning:** If you have to write "ugly" code to fix a weird bug, document it with `// FIXME:` or `// HACK:` so you don't accidentally "clean it" later and break the fix.
    

---

## 5. Error Handling Standard

Never let a program fail silently.

1. **Catch early:** Catch errors where they happen.
    
2. **Be specific:** Don't just say "Error occurred." Say "Database connection failed in FetchUser."
    
3. **Fallback:** Always define what should happen if the code fails (Return a `null`, an empty list, or a user-friendly error message).
    

---

## 6. The Solo Dev's "Zero-Manual-Work" Rule

To keep this standard alive without effort, you must automate.

- **Auto-Format on Save:** Enable this in your IDE so the computer handles the indentation and spacing.
    
- **Linting:** Use a linter to catch "smelly" code (like unused variables or unreachable code) before you even run it.
    
- **Git Atomic Commits:** Commit small changes with clear messages.
    
    - _Bad:_ `git commit -m "fixed stuff"`
        
    - _Good:_ `git commit -m "refactor: move login logic to auth service"`
        

---

**Would you like me to help you draft a "Project Readme" template that incorporates these standards for your new repository?**