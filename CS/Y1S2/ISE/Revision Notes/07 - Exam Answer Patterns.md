# Exam Answer Patterns

## General Answer Style

- When a question asks for a number of bullet points, produce exactly that many clear bullet points. [L16 p90](<16 - Agile vs Traditional and Maintenance.pdf#page=90>)
- Scenario answers should cite scenario facts and explain why those facts support the chosen method, risk strategy, or process. [L16 p94](<16 - Agile vs Traditional and Maintenance.pdf#page=94>) [L16 p95](<16 - Agile vs Traditional and Maintenance.pdf#page=95>) [L16 p96](<16 - Agile vs Traditional and Maintenance.pdf#page=96>)
- Definition questions should name the concept and give a short distinguishing explanation. [L01 p58](<01 - Introduction to Software Engineering.pdf#page=58>) [L03 p32](<03 - Requirements Introduction.pdf#page=32>)
- Compare questions should explicitly say how the two concepts differ, such as requirements vs specifications or release vs acceptance testing. [L04 p3](<04 - Requirements Gathering.pdf#page=3>) [L07 p1](<07 - Specifications.pdf#page=1>) [L12 p13](<12 - Release and Acceptance Testing.pdf#page=13>)

## Common Four-Mark Patterns

- Four SE activities: specification, development, validation, evolution. [L01 p58](<01 - Introduction to Software Engineering.pdf#page=58>)
- Four Agile Manifesto values: individuals/interactions, working software, customer collaboration, responding to change. [L16 p56](<16 - Agile vs Traditional and Maintenance.pdf#page=56>)
- Requirements vs specifications with UML: requirements model user/stakeholder needs; specifications model technical/system design. [L05 p7](<05 - Requirements Modelling.pdf#page=7>) [L07 p1](<07 - Specifications.pdf#page=1>)
- Release vs acceptance testing: release is internal readiness; acceptance is client/customer sign-off against requirements. [L12 p13](<12 - Release and Acceptance Testing.pdf#page=13>) [L14 p7](<14 - Configuration and Deployment.pdf#page=7>)

## Common Three- or Six-Mark Patterns

- Three stakeholder categories: primary, secondary, tertiary. [L03 p37](<03 - Requirements Introduction.pdf#page=37>)
- Three maintenance/evolution changes: fault fixing, adaptation, new functionality/enhancement. [L16 p8](<16 - Agile vs Traditional and Maintenance.pdf#page=8>) [L16 p39](<16 - Agile vs Traditional and Maintenance.pdf#page=39>)
- Three risk responses: avoid, mitigate/minimise, contingency/handling. [L18 p8](<18 - Risk Management.pdf#page=8>)
- Six-mark risk answers should name each strategy and give a scenario-specific example. [L18 p8](<18 - Risk Management.pdf#page=8>)

## Planning Question Pattern

Use this for Gantt, critical-path, and staffing questions. [L19 p11](<19 - Agile Planning and Project Management.pdf#page=11>)

1. Create a task table: task, duration, dependencies, staff needed.
2. Mark earliest start and earliest finish for every task.
3. Identify the longest dependency chain as the critical path.
4. State the project duration from the critical path.
5. Check overlapping tasks for staff conflicts.
6. If asked to fix the schedule, move a task with slack and state why the finish date is unchanged.

Good phrases:
- "Task X is critical because delaying it delays the final completion date."
- "Task Y has slack, so it can be moved to solve the staffing clash."
- "This avoids extending the project because the critical path is unchanged."
- "The schedule is invalid at this point because it requires more staff than are available."

## Scenario Answer Ingredients

- For accessibility or uncertain-user scenarios, involve users early, use personas/use cases, prototype, collect feedback, and define acceptance criteria. [L03 p40](<03 - Requirements Introduction.pdf#page=40>) [L03 p47](<03 - Requirements Introduction.pdf#page=47>) [L08 p7](<08 - Prototyping.pdf#page=7>) [L14 p7](<14 - Configuration and Deployment.pdf#page=7>)
- For financial, legal, safety, or data-sensitive scenarios, use more formal requirements, documentation, risk analysis, QA, and testing. [L16 p96](<16 - Agile vs Traditional and Maintenance.pdf#page=96>) [L17 p12](<17 - Software Quality.pdf#page=12>) [L18 p8](<18 - Risk Management.pdf#page=8>)
- For vague product ideas, use agile methods, rapid feedback, user stories, prototypes, and incremental delivery. [L16 p47](<16 - Agile vs Traditional and Maintenance.pdf#page=47>) [L16 p49](<16 - Agile vs Traditional and Maintenance.pdf#page=49>) [L16 p94](<16 - Agile vs Traditional and Maintenance.pdf#page=94>)
- For team-availability risks, use pair programming, collective ownership, documentation, and avoid placing single points of failure on critical tasks. [L16 p68](<16 - Agile vs Traditional and Maintenance.pdf#page=68>) [L19 p11](<19 - Agile Planning and Project Management.pdf#page=11>)
- For platform/version-release scenarios, mention configuration management, CI, automated tests, release management, tags, and platform-specific builds. [L02 p26](<02 - Git Ready for Teamwork.pdf#page=26>) [L14 p9](<14 - Configuration and Deployment.pdf#page=9>)
