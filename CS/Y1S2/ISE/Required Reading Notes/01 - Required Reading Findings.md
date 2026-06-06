# Required Reading Findings

## Requirements Are Still The Biggest Reading Theme

- The readings strongly support the lecture message that requirements are often harder and riskier than coding. The Stack Overflow reading argues that software problems usually centre on what the software is supposed to do, not syntax or coding mechanics. `[RR-REQ-SO]`
- Requirements failures include unclear, inconsistent, wrong, missing, or ignored requirements; these create late defects, rework, and client disappointment. `[RR-REQ-SO]` `[RR-FAIL]`
- The Requiment reading frames poor requirements, poor planning, weak communication, scope creep, lack of user involvement, and unclear non-functional requirements as major project-failure causes. `[RR-FAIL]`
- The IEEE requirements-risk paper says the central risk is that requirements do not accurately represent user needs, meaning the project can execute well and still build the wrong software. `[RR-REQ-RISK p1]`
- Overlooking a critical user class, functional requirement, quality attribute, or performance attribute can force expensive rework or even re-architecture. `[RR-REQ-RISK p1]`
- Non-functional requirements are repeatedly emphasised: performance, reliability, robustness, security, scalability, usability, accessibility, browser/platform choices, and maintainability can make or break a project. `[RR-REQ-RISK p2]` `[RR-FAIL]`
- Requirements inspections are important because defects become much more expensive to remove later, especially once software is in the field. `[RR-REQ-RISK p2]`

Exam implication:
- Be able to explain why requirements engineering matters, why vague requirements cause failure, why non-functional requirements matter, and why requirements should be inspected/validated early.

## Good Specifications Must Be Readable

- The Joel Spolsky reading reinforces that specifications only help if people actually read and understand them. `[RR-SPEC]`
- A specification should be technically correct and understandable; writing dense, academic-style prose defeats the point. `[RR-SPEC]`
- Good specs should provide the big picture before details, use stories/examples, avoid unexplained jargon, and be written for human readers. `[RR-SPEC]`
- Simple language, short sentences, whitespace, lists, tables, pictures, charts, and screenshots/mockups make specifications more usable. `[RR-SPEC]`
- Specs should be reviewed and reread so unclear parts can be rewritten. `[RR-SPEC]`

Exam implication:
- If asked what makes a good specification, mention clarity, readability, concrete examples/scenarios, visuals/mockups, review, and stakeholder usability.

## Usability Means Users Can Achieve Goals

- Digital.gov defines usability around how easily and effectively people can accomplish goals with a product/system while having a positive experience. `[RR-USE]`
- Usability testing measures how easily users achieve goals, using methods such as success rates and satisfaction. `[RR-USE]`
- Usability is part of wider UX; UX covers the overall experience, while usability focuses on whether the product works well for users. `[RR-USE]`
- Accessibility and assistive-technology findings are relevant to requirements and user testing because different user groups experience systems differently. `[RR-USE]`

Exam implication:
- If a scenario involves users, accessibility, public-facing systems, or acceptance testing, include usability/user testing and user-centred feedback.

## UML Models Support Requirements And Design

- Activity diagrams model business processes, the logic of a use case/scenario, or business rules. `[RR-ACT]`
- Activity diagram notation includes start/end nodes, activities, flows, decisions, merge points, forks/joins for parallel work, conditions/guards, notes, and swimlanes/partitions. `[RR-ACT]`
- Swimlanes help show who or what performs each activity, which makes the model easier to validate with stakeholders. `[RR-ACT]`
- Agile modelling keeps models "just barely good enough"; models are useful when they help understanding and can be discarded/updated when their value changes. `[RR-ACT]`
- Sequence diagrams model the flow of logic in a system and can be used for analysis and design. `[RR-SEQ]`
- Sequence diagrams can model usage scenarios, method logic, and service logic. `[RR-SEQ]`
- System-level sequence diagrams can help stakeholders visualise and validate a usage scenario; object/service-level diagrams help developers design internal interactions. `[RR-SEQ]`
- Sequence diagram order matters: messages are read from top to bottom to show the sequence of interactions. `[RR-SEQ]`

Exam implication:
- Be ready to explain how the same UML style can be used at requirements level and design/specification level.

## TDD Is A Tight Loop Of Test, Code, Refactor

- Test-driven development interweaves coding, unit testing, and design/refactoring. `[RR-TDD]`
- The TDD cycle is: write a small unit test, run it and see it fail, write just enough simple code to pass, refactor, and repeat. `[RR-TDD]`
- Reported TDD benefits include lower defect rates, some initial overhead, reduced effort in final phases, and improved internal/technical quality. `[RR-TDD]`
- Common TDD mistakes include not running tests often, writing too many tests at once, writing tests that are too coarse, writing trivial tests, or omitting assertions. `[RR-TDD]`
- Team-level TDD failure modes include partial adoption, slow/poorly maintained test suites, and abandoned test suites. `[RR-TDD]`
- Evidence of TDD can include test code committed alongside product code and meaningful code coverage, though coverage alone does not prove good TDD. `[RR-TDD]`

Exam implication:
- Know TDD as a process, its benefits, and its failure modes. It links implementation, unit testing, maintainability, CI, and agile methods.

## Maintainability Is The Big Implementation Reading Theme

- Maintainable software is easy to fix, extend, improve, adapt to new environments, and hand over to new developers. `[RR-MAINT]`
- Maintainability depends on software being easy to understand, easy to change, and easy to check after change. `[RR-MAINT]`
- Technical debt builds when teams skip comments, refactoring, warnings, tests, documentation, and rationale because they are under time pressure. `[RR-MAINT]`
- Software written without maintainability in mind can take far more effort to maintain than it took to develop. `[RR-MAINT]`
- Maintainability practices include designing for maintainability, iterative development, regular reviews, readable code, refactoring, documentation, automated builds, automated tests, CI, and version control. `[RR-MAINT]`
- Code reviews can find errors before testing and are cheaper than finding errors later. `[RR-MAINT]`
- Pair programming reviews code while it is written and spreads knowledge through the team. `[RR-MAINT]`
- Code reviews and pair programming reduce key-person risk by spreading codebase knowledge. `[RR-MAINT]`
- The code-conventions paper treats convention adherence as a maintainability proxy and links coding conventions with readability, understandability, and maintainability. `[RR-CODE p1]`
- Developers know conventions matter but may abandon them when deadlines are tight. `[RR-CODE p2]`

Exam implication:
- If asked about implementation quality, coding conventions, pair programming, or maintenance, focus on maintainability: readable, understandable, changeable, testable code.

## Authorization Adds A Security/Non-Functional Requirements Angle

- The Microsoft authorization reading distinguishes authentication from authorization: authentication proves identity, authorization decides whether the authenticated principal can perform an operation. `[RR-MS]`
- Application authorization protects high-level functionality and business rules, not just files/tables/resources. `[RR-MS]`
- Authorization should happen as early as practical at "gatekeepers" so unauthorized requests do not proceed until failure. `[RR-MS]`
- Authorization can happen in the UI tier, business tier, and data tier, with different checks at each layer. `[RR-MS]`
- UI checks can hide/disable controls, but business/data-tier checks are still needed because UI checks alone are not secure. `[RR-MS]`
- Data-tier authorization is the last line of defence for sensitive data and unauthorized modifications. `[RR-MS]`
- Identity flow matters in multi-tier systems because downstream components may need to know the authenticated user's identity to authorize correctly. `[RR-MS]`

Exam implication:
- Treat authorization as a non-functional/security requirement and a design/testing concern. If a scenario involves sensitive data, mention authentication, authorization, roles, least privilege, and checks at more than one tier.

## Industry Experience Reading Connects The Theory To Practice

- The industry-experience PDF describes a small remote team using collaborative tools such as Teams, Jira, and GitHub. `[RR-IND p1]`
- The team uses agile workflow ideas, daily stand-ups, and feature branching to coordinate work. `[RR-IND p1]` `[RR-IND p2]`
- Feature branching lets developers work on isolated changes before merging into the main branch, improving collaboration and code stability. `[RR-IND p2]`
- Jira tickets map to features or bugs, which supports traceability between work items and code changes. `[RR-IND p2]`
- Rubber-duck explanation can expose inconsistencies/gaps in understanding and create a lightweight narrative of work for others. `[RR-IND p3]`
- CI/CD and automated tests improve speed, efficiency, coverage, and accuracy before live deployment. `[RR-IND p3]`

Exam implication:
- For applied questions, use practical examples: feature branches, Jira/issues, stand-ups, CI/CD, automated testing, and documentation/communication.

