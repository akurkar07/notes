# COMP1003 Exam Glossary

## Core Software Engineering

**Software engineering**  
A systematic, organised approach to developing, operating, and maintaining software.

**Software process**  
The set of activities used to produce and evolve software.

**Specification**  
The activity of defining what the system should do and the constraints it must satisfy. Also used to mean a technical description of how the system will behave or be built.

**Development**  
Designing and implementing the software.

**Validation**  
Checking that the software meets user/customer needs.

**Evolution**  
Changing software after delivery in response to new requirements, defects, platforms, or environments.

**Waterfall model**  
A plan-based process with sequential stages such as requirements, design, implementation, testing, and maintenance.

**V-model**  
A plan-based model that links development stages with corresponding testing/validation stages.

**Iterative development**  
Development through repeated cycles, producing and improving versions of the software.

**Spiral model**  
An iterative, risk-driven process model involving planning, risk analysis, development, validation, and review each cycle.

## Requirements

**Requirement**  
Something stakeholders need the system to do, or a constraint/quality the system must satisfy.

**Requirements engineering**  
The process of discovering, analysing, documenting, and validating requirements.

**Requirements elicitation**  
Finding requirements by working with stakeholders, using methods such as interviews, observation, surveys, workshops, personas, and use cases.

**Stakeholder**  
Anyone with an interest in the system, such as users, clients, managers, developers, testers, regulators, or maintainers.

**Primary stakeholder**  
A person/group who directly uses or is directly affected by the system.

**Secondary stakeholder**  
A person/group indirectly affected or involved, such as managers or support staff.

**Tertiary stakeholder**  
A wider party affected by the system, such as regulators or society.

**Persona**  
A fictional representative user type used to reason about user goals, motivations, knowledge, and needs.

**Use case**  
A description/model of a goal-oriented interaction between an actor and the system.

**Actor**  
A user, role, or external system that interacts with the system in a use case.

**Functional requirement**  
A requirement describing what the system should do.

**Non-functional requirement**  
A requirement describing qualities or constraints, such as performance, security, usability, reliability, accessibility, or maintainability.

**Requirements validation**  
Checking requirements for correctness, consistency, completeness, feasibility, and testability.

**Requirements inspection/review**  
A structured check of requirements to find ambiguity, conflict, missing assumptions, or errors early.

**Requirements change management**  
The controlled process for assessing, approving, documenting, and tracing changes to requirements.

**Scope creep**  
Uncontrolled expansion of project requirements or features.

## Specifications, Modelling, and Prototyping

**Specification document**  
A document describing how the system should behave or be built, usually derived from requirements.

**Functional specification**  
A specification of system behaviour and features.

**UML**  
Unified Modeling Language, a notation for modelling systems, processes, interactions, and designs.

**Activity diagram**  
A UML diagram for modelling workflows, business processes, use-case logic, decisions, and parallel activity.

**Sequence diagram**  
A UML diagram showing ordered interactions/messages between actors, systems, objects, services, or classes.

**Class diagram**  
A UML diagram showing classes, attributes, methods, and relationships.

**Prototype**  
A simplified or partial version/design used to explore, communicate, or test ideas.

**Low-fidelity prototype**  
A rough, cheap prototype such as a sketch or wireframe.

**High-fidelity prototype**  
A more realistic or interactive prototype closer to the final product.

**Throwaway prototype**  
A prototype built to learn something and then discarded.

**Evolutionary prototype**  
A prototype gradually developed into the final system.

## Implementation and Maintainability

**Implementation**  
Turning design/specification into working code.

**Maintainability**  
How easily software can be understood, changed, fixed, extended, and tested.

**Technical debt**  
Future cost created by shortcuts such as weak tests, poor structure, missing documentation, or rushed code.

**Refactoring**  
Improving internal code structure without changing external behaviour.

**Coding convention**  
A team/project rule about code style, naming, layout, structure, or formatting.

**Code review**  
Developers inspecting code to find errors, improve quality, and share understanding.

**Pair programming**  
Two developers work together at one workstation/task, often as driver and navigator.

**Driver**  
In pair programming, the person currently writing the code.

**Navigator/observer**  
In pair programming, the person reviewing, thinking ahead, and guiding the approach.

**Debugging**  
Finding and removing the cause of a defect.

**Defect/bug**  
A fault in software that can cause incorrect behaviour.

**Traceability**  
The ability to link requirements, specifications, tasks, code, tests, and documentation.

## Testing

**Testing**  
Running/checking software to find defects and provide evidence of quality.

**Unit testing**  
Testing individual units, functions, classes, or components.

**Integration testing**  
Testing how units/components work together.

**Release testing**  
Testing the complete system internally to decide whether it is ready to release/show to the client.

**Acceptance testing**  
Testing with/for the client to decide whether the system satisfies requirements and can be accepted.

**User testing**  
Testing with real users in realistic use, often after or near release.

**Alpha testing**  
Early user testing, often internal or with selected users.

**Beta testing**  
Wider pre-release user testing with external users.

**Test plan**  
A document describing what will be tested, why, how, and with what expected results.

**Test case**  
A specific input/action, expected result, and pass/fail criterion.

**TDD**  
Test-driven development: write a small failing test, write just enough code to pass, refactor, repeat.

**Code coverage**  
A measure of how much code is executed by tests. Useful evidence, but not proof of good testing by itself.

**Automated testing**  
Tests run automatically by tools/scripts.

## Version Control, CI, and Deployment

**Version control**  
Tools/processes for tracking and coordinating changes to files over time.

**Repository**  
A stored project history, often containing code, documentation, tests, and branches.

**Clone**  
Download a repository copy to your machine.

**Commit**  
Save a snapshot of staged changes to version history.

**Push**  
Upload local commits to a remote repository.

**Pull**  
Download/integrate remote changes into your local copy.

**Branch**  
A separate line of development.

**Feature branch**  
A branch used to develop one feature or fix before merging back.

**Merge**  
Combine changes from one branch into another.

**Merge conflict**  
A situation where version control cannot automatically combine changes.

**Merge request / pull request**  
A request to review and merge changes into another branch.

**Tag**  
A named marker for a specific commit, often a release version.

**`.gitignore`**  
A file listing files/folders Git should not track.

**Continuous integration (CI)**  
Frequent integration of code with automated builds/tests to detect problems early.

**Continuous delivery/deployment (CD)**  
Automation that prepares or deploys software releases.

**Build**  
The process/output of turning source code into runnable software.

**Configuration management**  
Managing versions, dependencies, settings, builds, and platform-specific configurations.

**Deployment**  
Putting software into an environment where it can be used or tested.

## Maintenance and Evolution

**Maintenance**  
Changing software after delivery to fix, adapt, or improve it.

**Corrective maintenance**  
Fixing faults/bugs.

**Adaptive maintenance**  
Changing software for new platforms, environments, laws, APIs, or dependencies.

**Perfective maintenance**  
Improving features, performance, usability, maintainability, or adding functionality.

**Preventative maintenance**  
Changes that reduce future maintenance cost, such as refactoring.

**Emergency change**  
A rapid fix made under urgency; should be documented and revisited later if needed.

**Legacy system**  
An older system still in use, often hard to change or replace.

## Quality and Risk

**Software quality**  
The degree to which software satisfies requirements, user needs, and quality attributes.

**Quality assurance (QA)**  
Process-focused work to plan, define standards, and check that projects follow quality practices.

**Quality control**  
Product-focused checking, testing, or inspection of outputs.

**Quality plan**  
A project document defining quality goals, standards, process, risks, and acceptable quality.

**Inspection**  
A structured review of artefacts such as requirements, specifications, designs, or code.

**Software risk**  
A risk affecting the product itself, such as security, privacy, reliability, performance, or dependability.

**Project risk**  
A risk affecting delivery, such as staffing, schedule, cost, unclear requirements, or coordination problems.

**Risk analysis**  
Identifying and assessing risks and their likelihood/impact.

**Risk monitoring**  
Continuing to watch risks during the project.

**Risk avoidance**  
Changing the plan to remove a risk.

**Risk mitigation/minimisation**  
Reducing the likelihood or impact of a risk.

**Contingency plan**  
A backup plan used if a risk happens.

## Project Planning

**Work breakdown**  
Dividing a project into tasks.

**Dependency**  
A relationship where one task must happen before another can start.

**Milestone**  
A significant checkpoint or deliverable in a project.

**Deliverable**  
Something the project produces, such as a document, prototype, test plan, or software release.

**PERT chart**  
A diagram showing tasks and dependencies.

**Gantt chart**  
A chart showing tasks over time, including duration and dependencies.

**Critical path**  
The longest dependency path through a project; delays here delay the whole project.

**Slack/float**  
Time a task can be delayed without delaying the whole project.

**Staff allocation chart**  
A plan showing which people are assigned to which tasks and when.

## Agile

**Agile**  
An approach valuing adaptability, working software, customer collaboration, and responding to change.

**Agile Manifesto**  
Four values: individuals/interactions, working software, customer collaboration, responding to change.

**Scrum**  
An agile framework using sprints, backlog, product owner, Scrum Master, daily scrum, review, and retrospective.

**Sprint**  
A fixed-length period for completing selected work.

**Product backlog**  
A prioritised list of desired work/features.

**Sprint planning**  
Selecting and planning work for a sprint.

**Daily scrum / stand-up**  
A short regular meeting to coordinate work and blockers.

**Sprint review**  
A meeting to inspect the increment and gather feedback.

**Retrospective**  
A meeting to improve the team's process.

**Scrum Master**  
The role helping the team follow agreed Scrum practices and remove blockers.

**Product owner**  
The role responsible for product priorities and backlog value.

**User story**  
A short requirement-like statement of user need, often used in agile planning.

**XP / Extreme Programming**  
An agile method focused on technical practices such as TDD, pair programming, small releases, simple design, refactoring, CI, and collective ownership.

**Kanban**  
An agile/lean method using a visual board and work-in-progress limits to manage flow.

**Work in progress (WIP) limit**  
A limit on how many tasks can be active at once.

**Incremental delivery**  
Delivering useful parts of the system in stages.

**Hybrid approach**  
Combining agile and plan-based practices according to project needs.

## Usability, Security, and Authorization

**Usability**  
How easily and effectively users can achieve goals with a product/system.

**User experience (UX)**  
The overall experience of using a product, including usability, accessibility, satisfaction, and context.

**Accessibility**  
Designing software so people with disabilities can use it.

**Authentication**  
Proving identity.

**Authorization**  
Deciding what an authenticated user/application is allowed to do.

**Role-based access control**  
Granting permissions according to roles such as admin, manager, or user.

**Least privilege**  
Giving users/applications only the permissions they need.

**Gatekeeper**  
A point where authorization is checked before access/action continues.

**Identity flow**  
Passing identity information through application tiers so authorization can be checked correctly.

