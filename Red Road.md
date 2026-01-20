# What problem I want to solve?

I aways have some trivial thoughts in daily life, some of them maybe some thoughts of light, some of them are what i want to do in the future, some of them are introspect, in current work, I maybe need take a long time to think and  classify them by myself, and maybe i will abandon this thoughts when my mood is lost or have no time.So I need a magic tool to classify the thoughts automatically, and do the job according to the different thoughts, for example, if i it's a TODO, the tool should do the [[#TODO process]] ,and if this is just thoughts, the tool should do the [[#Thoughts process]].

## TODO process
### Review Phase
In this phase the agent will do the following things:
1. Access how self-motivation behind the given goal.
2. Clarify the goal.

Some to-do items may be triggered by external circumstances, while others stem from momentary moods. What we need to do is identify our truly self-motivated goals.

And the agent will generate some question to to assess the level of self-motivation behind a given goal, According to specific goal.
1. The agent should foresee the difficulties we will face, and list them ask the user can accept it.
2. The agent also should list other question for the user to identify the level of self-motivation
#### Question List
*Module 1: Difficulty Tolerance Questions(Foresee & Verify Acceptance)*

| Difficulty Type   | Question Template                                                                                                                                                                                                                                                     | Scoring Standard (1–5 points)                                                                                                                                     |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time Conflict     | You need to allocate [X time] daily/weekly for [Goal Content]. If you encounter a busy period (e.g., overtime, exam week, family emergency) and can only spare 50% of the planned time, will you still stick to the minimal version of the goal instead of giving up? | 5 = Definitely stick to the minimal version; 4 = Usually stick to it; 3 = Sometimes stick to it; 2 = Rarely stick to it; 1 = Directly give up                     |
| Progress Plateau  | In the process of [Goal Content], you may face a plateau period (e.g., no improvement for 2-4 weeks, repeated failures). Will you actively adjust the method (e.g., find tutorials, ask for help) or will you choose to pause/abandon?                                | 5 = Proactively adjust methods and persist; 4 = Adjust methods after hesitation; 3 = Try once then pause; 2 = Pause for a long time; 1 = Abandon the goal         |
| Negative Feedback | If others (e.g., friends, colleagues) question your [Goal Content] (e.g., "It’s useless", "You can’t stick to it") or laugh at your initial clumsy attempts, will this affect your determination to continue?                                                         | 5 = Not affected at all; 4 = Slightly affected but persist; 3 = Affected and slow down progress; 2 = Affected and pause temporarily; 1 = Give up due to criticism |
| Mood Fluctuation  | When you are in a bad mood (e.g., frustrated, tired, depressed), will you still prioritize [Goal Content] according to the plan, or will you use "bad mood" as an excuse to skip it?                                                                                  | 5 = Always prioritize the goal; 4 = Usually prioritize it; 3 = Sometimes prioritize it; 2 = Rarely prioritize it; 1 = Skip it every time                          |
| Opportunity Cost  | Pursuing [Goal Content] will take up your leisure time (e.g., watching dramas, playing games, hanging out). When you face the temptation of these low-effort, high-pleasure activities, can you resist them and stick to the goal?                                    | 5 = Resist all temptations; 4 = Resist most temptations; 3 = Resist half the time; 2 = Seldom resist; 1 = Can’t resist at all                                     |
| Failure Risk      | When we fail, can you accept the risk of (losing money/wasting time/...)?                                                                                                                                                                                             | 5 = accept; 4 =can accept after little time 3 = can accept after some time 2 = can accept after long time 1 = Can’t accept at all                                 |

*Module 2: Self-Motivation Level Questions(Identify Intrinsic Drive)*

| Motivation dimension     | Question template                                                                                                                                                                              | Scoring Standard (1–5 points)                                                                                                                     |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Initiative Source        | Who is the core initiator of [Goal Content]? Is it your own inner desire, or is it driven by external factors (e.g., others’ suggestions, social trends, work requirements)?                   | 5 = Completely self-initiated; 3 = Both self and external drive; 1 = Completely driven by others                                                  |
| Value Relevance          | Does [Goal Content] align with your long-term values or life plans (e.g., career growth, personal interest, health goals)? Can you list 2+ specific benefits that this goal will bring to you? | 5 = Highly aligned with long-term plans, clear benefits; 3 = Somewhat relevant, vague benefits; 1 = No relevance, no clear benefits               |
| Regret Cost              | If you give up [Goal Content] now, will you feel regretful after 3 months/1 year? Will this regret affect your subsequent decisions about similar goals?                                       | 5 = Will feel very regretful, and it will affect future decisions; 3 = Will feel a little regretful but no follow-up impact; 1 = No regret at all |
| Automatic Execution      | Will you take the initiative to think about [Goal Content] (e.g., plan steps, collect resources, summarize progress) without external reminders (e.g., alarms, others’ supervision)?           | 5 = Often think about it actively; 3 = Think about it occasionally; 1 = Never think about it unless reminded                                      |
| Alternative Substitution | Is there any other goal that can replace [Goal Content] to meet your same core needs? If yes, why do you still choose [Goal Content] instead of the alternative?                               | 5 = No alternative can replace it; 3 = There are alternatives but this one is better; 1 = Easily replaced by other goals                          |

*Overall Assessment Decision Rule*
 
Total Score Calculation Formula:

Total Score=(Module 1 Score×0.4)+(Module 2 Score×0.6)
- Module 1 full score: 25 → Max weighted score: 25×0.4=10
- Module 2 full score: 25 → Max weighted score: 25×0.6=15
- **Total full score**: 25

| Total Score Range | Decision                                          | Specific Action                                                                                                                                                                                                                                                                                                                                                |
| ----------------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **20–25**         | **Highly Recommended: Enter Test Phase**          | The goal is both self-driven and executable; proceed to design the ultra-minimal MVP.                                                                                                                                                                                                                                                                          |
| **14–19**         | **Conditionally Recommended: Optimize First**     | - Analyze the low-score module: <br><br>1. If Module 1 is low: Simplify the goal (reduce time commitment, lower difficulty) to improve tolerance. <br><br>2. If Module 2 is low: Strengthen the link between the goal and personal values (e.g., list 3 specific benefits for yourself) to boost intrinsic motivation. <br><br>→ Re-assess after optimization. |
| **0–13**          | **Not Recommended: Transfer to Thoughts Process** | The goal lacks either intrinsic drive or execution feasibility; archive it as a casual thought for future review (when your values or circumstances change).                                                                                                                                                                                                   |



### Test Phase
The core of MVP is to **verify willingness with the least cost**, not to verify effect. Optimize the design:

- For example, if the TODO is "learn to run 5km", the MVP is **"run 1km 3 times a week for 2 weeks"**, not "run 5km directly".
- The tool should automatically generate MVP rules based on the TODO type:
    - **Skill-based TODO**: MVP = 10-20 minutes of daily practice for 1 week.
    - **Project-based TODO**: MVP = complete the first smallest module (e.g., "write the outline of the article" for a writing task).
- **Test Pass Standard**: User completes MVP as scheduled ≥80% of the time → enter Action phase.
### Action Phase

This framework is **quantitative and adaptive**, designed for the agent to break down ultimate goals into staged milestones, arrange daily actions, and dynamically adjust plans based on user feedback. It follows the **SMART principle** and adds a **feedback-driven adjustment loop** to match the user’s actual execution status.
#### Goal Decompositions

The agent must follow these rules to split the ultimate goal into manageable milestones and daily tasks:

1. The milestones can be measured, and it's progessive points (from easy to difficult).
2. In different stages of milestones, The goal should break down to different SMART actions that can be added to daily life (as small as possible).


#### Actions Schedule

1. The agents should schedule the daily actions, it shall refer to all of the user's current schedules. 

#### Assess action
1. After each task collect the user's feedback:
	1. feeling of difficulty
	2. mood in the action
2. The agent should automatically collect information of actions, the degree of completion, used time, and other information.

#### Actions Adjust,And Re-Schedule
1. According to the assess the agent should adjust the difficulty and even method of the actions.If the assess show it's good the agent should raise the difficulty, and if the assess show it's bad the agent should reduce the difficult.
2. after adjust the difficult the time maybe influenced ,and we may need re-schedule.

## Thoughts process
### review
1. the tool should analyze the user's thought.and review it's right, or it's relevant to user's previous thoughts, or is it opposite to user's previous thoughts, according to the user's  
2. user's thought's should also be put into the context to help user to make a plan
# What's the MVP process flow?
1. Collect the user's thoughts by input or voice.
2. Agent classify the input to TODO or thoughts.
3. If it's a TODO start the TODO process.
4. If it's a thoughts process start the thoughts process.
[[Red Road MVP]]
[[Red Road V2]]