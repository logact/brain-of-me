# MVP Requirement Document (MRD) - Thought Classification & Management Tool

# 1. Document Overview

## 1.1 Document Purpose

Define the minimum viable product features of the Thought Classification & Management Tool, focusing on solving the pain point of inefficient manual sorting of trivial daily thoughts. The MVP aims to automatically classify thoughts into TODOs and casual thoughts, execute corresponding processing workflows, and verify user demand for intelligent thought management with minimal resources.

## 1.2 Product Name

MindSort Lite (MVP Version)

## 1.3 Target Users

Individuals who frequently generate trivial daily thoughts (including inspirations, future plans, and self-reflections) but struggle with manual classification, easy abandonment due to time constraints or low mood, and inefficient follow-up of actionable items.

## 1.4 MVP Release Goal

1. Validate if users accept automatic classification of thoughts into TODOs and casual thoughts.
    
2. Verify the usability and effectiveness of the TODO process (Review/Test/Action phases) and Thoughts process (Review phase) in helping users manage thoughts.
    
3. Achieve ≥ 3 daily active users (DAU) in the first week, with ≥ 70% of generated thoughts successfully classified and processed.
    
4. Collect user feedback on workflow rationality and functional optimization suggestions.
    

# 2. User Personas & Pain Points

## 2.1 Primary User Persona

**Name**: Lin Tao **Age**: 28 **Profile**: Office worker, often has scattered thoughts (e.g., "learn Python", "reflect on meeting mistakes", "travel to Chengdu next month") during work and leisure. Lacks time to sort them out regularly, often forgets or abandons actionable thoughts when busy or in a bad mood. **Habits**: Records thoughts in notes randomly, rarely classifies them; gives up goals easily when facing difficulties or mood swings. **Needs**: Automatically classify thoughts, scientifically assess and promote follow-up of actionable items, and systematically organize casual thoughts for future review.

## 2.2 User Pain Points & Scenarios

| Pain Point                              | User Scenario                                                                                                                                                           |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Inefficient manual classification       | Lin Tao has 5+ thoughts every day, spending 10+ minutes sorting them into "to-do" and "just thoughts", which he finds tedious and often skips.                          |
| Easy abandonment of actionable thoughts | He sets a goal like "learn Python", but when busy with overtime or in a bad mood, he gives up easily without assessing his motivation and feasibility.                  |
| Disorganized casual thoughts            | His self-reflections and inspirations are scattered in notes, unable to connect with previous thoughts, missing the opportunity to derive action plans.                 |
| Unsystematic follow-up of goals         | When he tries to execute a goal, he lacks step-by-step decomposition and dynamic adjustment, leading to failure due to excessive difficulty or unreasonable scheduling. |

# 3. Core Requirements (Must-Have)

## 3.1 Functional Requirements

### 3.1.1 Thought Input & Automatic Classification

|Requirement ID|Feature Description|User Flow|Acceptance Criteria|
|---|---|---|---|
|FR-001|Thought Input|User enters text thoughts → submits to the tool|1. Support plain text input (5-500 characters). 2. Submit successfully with one click, no duplicate submission.|
|FR-002|Automatic Classification|Tool analyzes input text → classifies into "TODO" or "Thoughts" → notifies user of classification result|1. Classification accuracy ≥ 80% (judged by user confirmation). 2. User can manually adjust classification if incorrect. 3. Classification result is displayed within 2 seconds after submission.|

### 3.1.2 TODO Process (Review/Test/Action Phases)

#### Phase 1: Review Phase (Self-Motivation Assessment)

| Requirement ID | Feature Description                      | User Flow                                                                                                                                        | Acceptance Criteria                                                                                                                                                                                                                                                       |
| -------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FR-003         | Generate Motivation Assessment Questions | Tool extracts TODO core content → generates personalized questions based on Module 1 (Difficulty Tolerance) and Module 2 (Self-Motivation Level) | 1. Generate 6 questions for Module 1 and 5 questions for Module 2, replacing [Goal Content] and [X time] with actual TODO details. 2. Questions are relevant to the TODO type (e.g., skill-based, project-based).                                                         |
| FR-004         | Score Calculation & Decision Making      | User answers questions and scores → tool calculates total weighted score → outputs decision result                                               | 1. Follow the formula: Total Score = (Module 1 Score × 0.4) + (Module 2 Score × 0.6). 2. Display score breakdown and corresponding decision (Highly Recommended/Conditionally Recommended/Not Recommended). 3. Provide specific action suggestions based on the decision. |

#### Phase 2: Test Phase (Ultra-Minimal MVP Generation)

| Requirement ID | Feature Description    | User Flow                                                                          | Acceptance Criteria                                                                                                                                                                                     |
| -------------- | ---------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FR-005         | Auto-Generate Test MVP | Tool identifies TODO type (skill/project-based) → generates ultra-minimal test MVP | 1. Skill-based TODO: MVP = 10-20 minutes of daily practice for 1 week. 2. Project-based TODO: MVP = complete the first smallest module. 3. User can adjust MVP details (duration, difficulty) manually. |
| FR-006         | Test Result Evaluation | User executes MVP → tool records completion status → judges pass/fail              | 1. Calculate completion rate (actual completion times / planned times). 2. Pass standard: completion rate ≥ 80% → enter Action phase; otherwise → re-optimize MVP.                                      |

#### Phase 3: Action Phase (Goal Decomposition & Dynamic Adjustment)

| Requirement ID | Feature Description                | User Flow                                                                                    | Acceptance Criteria                                                                                                                                                                                                                |
| -------------- | ---------------------------------- | -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| FR-007         | Goal Decomposition                 | Tool splits ultimate TODO into progressive milestones → decomposes into daily SMART tasks    | 1. Milestones are measurable and progressive (easy to difficult). 2. Daily tasks are minimal and fit daily life. 3. Follow SMART principle (Specific, Measurable, Achievable, Relevant, Time-bound).                               |
| FR-008         | Action Scheduling                  | Tool refers to user’s current schedule → arranges daily tasks                                | 1. User can input basic schedule (e.g., work hours 9:00-18:00). 2. Tasks are scheduled in free time, avoiding conflicts. 3. Display daily task list with time slots.                                                               |
| FR-009         | Action Assessment                  | User completes task → submits feedback (difficulty, mood) → tool collects completion details | 1. Feedback options: Difficulty (1-5 points, 1=very easy, 5=very difficult); Mood (positive/neutral/negative). 2. Automatically record completion status (completed/partially completed/not completed), used time.                 |
| FR-010         | Dynamic Adjustment & Re-Scheduling | Tool analyzes assessment data → adjusts task difficulty/method → re-schedules if needed      | 1. Good feedback (difficulty 2-3 points, positive mood): Increase difficulty appropriately. 2. Poor feedback (difficulty 4-5 points, negative mood): Reduce difficulty. 3. Re-schedule tasks to fit time changes after adjustment. |

### 3.1.3 Thoughts Process (Review Phase)

|Requirement ID|Feature Description|User Flow|Acceptance Criteria|
|---|---|---|---|
|FR-011|Thought Analysis & Contextualization|Tool analyzes thought content → compares with previous thoughts → contextualizes for planning|1. Identify consistency, relevance, or opposition with previous thoughts. 2. Summarize analysis results in plain language. 3. Link to related previous thoughts for contextual display.|
|FR-012|Thought Archiving & Review|Tool archives processed thoughts → supports user review|1. Thoughts are archived by date and category. 2. User can search thoughts by keywords. 3. Display contextual links during review.|

## 3.2 Non-Functional Requirements

| Requirement ID | Type          | Description                                | Acceptance Criteria                                                                                                 |
| -------------- | ------------- | ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| NFR-001        | Performance   | Page load time and function response speed | 1. Page load time < 2 seconds. 2. Classification, question generation, score calculation response time < 3 seconds. |
| NFR-002        | Usability     | User operation complexity                  | User can complete the entire process of inputting thoughts to viewing processing results in ≤ 5 steps.              |
| NFR-003        | Data Security | User thought data and operation records    | Data is stored locally on the device (no cloud sync in MVP), no data leakage.                                       |
| NFR-004        | Compatibility | Device compatibility                       | Supports iOS 15+ and Android 10+ mobile devices, adapts to mobile screen sizes.                                     |

# 4. Out-of-Scope Features (Nice-to-Have)

| Feature               | Description                                                               | Post-MVP Implementation Plan |
| --------------------- | ------------------------------------------------------------------------- | ---------------------------- |
| Voice Input           | Support voice input of thoughts, convert to text automatically.           | Add in Version 1.1           |
| Cloud Sync            | Sync thought data and task progress across multiple devices.              | Add in Version 1.2           |
| Thought Visualization | Visualize thought connections and task progress with mind maps or charts. | Add in Version 1.3           |
| Custom Question Bank  | User can add custom assessment questions for TODO motivation evaluation.  | Add in Version 2.0           |
| Reminder Function     | Send notifications to remind users of daily tasks and thought reviews.    | Add in Version 1.1           |

# 5. Success Criteria

| Category                          | Metrics                                                                    | Target                               |
| --------------------------------- | -------------------------------------------------------------------------- | ------------------------------------ |
| Quantitative                      | Daily Active Users (DAU)                                                   | ≥ 3 in Week 1, ≥ 5 in Week 2         |
| Thought Classification Accuracy   | ≥ 80% (user-confirmed correct classifications / total classifications)     |                                      |
| TODO Completion Rate (Test Phase) | ≥ 70% (users who pass the test phase / users who enter the test phase)     |                                      |
| User Retention Rate (Day 7)       | ≥ 40% (users who use the tool on Day 7 / users who registered on Day 1)    |                                      |
| Qualitative                       | User Satisfaction Score                                                    | ≥ 4.0/5.0 (based on post-use survey) |
| Usefulness Feedback               | ≥ 80% of users think the tool helps manage thoughts and follow up on TODOs |                                      |

# 6. Technical Constraints & Assumptions

## 6.1 Technical Limitations

1. Automatic classification relies on rule-based NLP (no AI training in MVP), with predefined keywords (e.g., "learn", "do", "complete" for TODOs; "think", "feel", "reflect" for Thoughts).
    
2. No backend database; all data (thoughts, tasks, schedules) is stored locally on the user’s device.
    
3. No integration with third-party calendar apps (user manually inputs schedule in MVP).
    
4. Question generation uses fixed templates, with variables replaced by TODO core content (no fully personalized question customization).
    

## 6.2 Assumptions

1. Users are willing to input thoughts in text form and provide feedback on classification results.
    
2. Users can clearly express thoughts in text, enabling the tool to extract core content for classification and assessment.
    
3. Users will follow the tool’s suggested workflows (Review/Test/Action phases) for TODO processing.
    
4. The predefined question templates and scoring rules can effectively assess user motivation and feasibility.
    

# 7. MVP Timeline & Milestones

| Milestone                               | Timeline | Responsible Role                           | Deliverable                                                                          |
| --------------------------------------- | -------- | ------------------------------------------ | ------------------------------------------------------------------------------------ |
| Demand Confirmation & UI/UX Design      | Week 1   | Product Manager + UI/UX Designer           | Finalized MRD, wireframes, and high-fidelity mockups                                 |
| Core Function Development               | Week 2-3 | Full-stack Developer                       | Functional prototype with thought classification, TODO process, and Thoughts process |
| Testing & Bug Fixing                    | Week 4   | QA Tester + Developer                      | Bug-free MVP, test report with pass rate ≥ 95%                                       |
| Internal Trial & Optimization           | Week 5   | Product Team + Selected Users (3-5 people) | Optimized MVP based on trial feedback                                                |
| Public MVP Launch & Feedback Collection | Week 6   | Product Manager                            | MVP released on app stores, feedback collection channel (survey)                     |
