# COMP1003 / Foundations of Software Engineering — Exam-Focused Mark-Scheme Notes

These notes are rebuilt around the uploaded **exam.pdf** and **mak scheme.pdf**. The goal is not to memorise every slide; it is to learn the answers in the style the exam rewards.

---

## 0. What the exam is really testing

The sample paper has three sections:

1. **Section A — Software Engineering Activities**: core lifecycle activities, requirements/specifications, prototyping, testing, continuous integration and deployment.
2. **Section B — Project Management & Risks**: software risk, project risk, pair programming, critical path decisions, quality assurance.
3. **Section C — Agile Methodologies**: Agile Manifesto values, user stories across the SE process, and choosing agile vs plan-driven methods from a scenario.

The marking style is usually: **1 mark per correct named point + brief explanation**. So do not waffle. Give named terms, then explain them in one sentence.

Golden exam rule:

> For every answer, say **what it is**, **why it matters**, and **where it fits in the software engineering process**.

---

## 1. The core Software Engineering process

### The four fundamental activities

These are extremely likely because they appear directly in the sample exam.

| Activity | Exam definition |
|---|---|
| **Specification** | Defining what the system should do and what constraints it must satisfy. |
| **Development** | Designing and implementing the software system. |
| **Validation** | Checking that the software meets what the customer/user wanted. |
| **Evolution** | Changing the software after delivery in response to new needs, faults, environments, or constraints. |

### Model answer for a 4-mark question

**Specification** identifies the required services and constraints of the system. **Development** is the design and implementation of the software. **Validation** checks that the software satisfies the user/customer needs. **Evolution** modifies the software after release as requirements, faults, or environments change.

### Common mistake

Do not replace these with random lifecycle stages like “coding, testing, deployment, maintenance” unless the wording clearly allows similar names. The expected set is **Specification, Development, Validation, Evolution**.

---

## 2. Requirements vs Specifications

This is one of the biggest exam themes.

### Core distinction

| Term | Meaning | Audience | Level |
|---|---|---|---|
| **Requirement** | What the user/stakeholder needs to achieve. | Users, stakeholders, developers. | Broad/high-level. |
| **Specification** | How the system/software will meet those requirements. | Developers, testers, engineers. | Detailed/precise. |

### Simple example

| Type | Example |
|---|---|
| Requirement | A student needs to view their coursework deadlines. |
| Specification | The system shall display all upcoming coursework deadlines in date order on the dashboard. |

### Functional vs non-functional

| Type | Requirement example | Specification example |
|---|---|---|
| **Functional** | Users need to log in. | The system shall allow login using university credentials. |
| **Non-functional** | Login must be secure. | Passwords shall be stored using a salted hash and failed logins shall be limited. |

### UML diagrams at requirement level vs specification level

The exam asks how the **same type of UML diagram** can be used differently.

| UML diagram | Requirement-level use | Specification/design-level use |
|---|---|---|
| **Sequence diagram** | Shows high-level user interaction with the system, e.g. user requests password reset. | Shows software objects/classes calling each other’s methods to implement password reset. |
| **Use case diagram** | Shows what actors want to do with the system. | Can help define system services that must be implemented. |
| **Class diagram** | Shows important domain concepts/entities. | Shows actual software classes, attributes, methods, and relationships. |
| **Activity diagram** | Shows the user/business workflow. | Shows system/control flow in the proposed implementation. |

### Model answer for a 4-mark question

A **requirement** describes what the user or stakeholder needs the system to do. A **specification** describes how the system will be built or what exact software behaviour will satisfy the requirement. A sequence diagram can be used at requirements level to show a user’s high-level interaction with the system. The same sequence diagram type can be used at specification level to show the classes/objects calling each other’s methods inside the software.

### Common mistake

Do not say requirements are “less important” or specifications are “the code”. Specifications are still documents/models, not necessarily implementation.

---

## 3. Requirements engineering and validation

### Requirements engineering process

| Stage | Purpose |
|---|---|
| **Feasibility study** | Decide whether the project is realistic and worth doing. |
| **Elicitation and analysis** | Discover and understand stakeholder needs. |
| **Requirements specification/documentation** | Record requirements clearly. |
| **Requirements validation** | Check that requirements are good before development. |

### Requirement qualities

Good requirements should be:

- **Valid** — reflect real stakeholder needs.
- **Consistent** — do not contradict each other.
- **Complete** — cover the necessary system behaviour.
- **Realistic/feasible** — possible within constraints.
- **Verifiable/testable** — possible to check later.
- **Clear/understandable** — not ambiguous.
- **Traceable** — linkable to source, specification, tests, and code.

### Why this matters in exams

A lot of questions are secretly asking:

> How do we avoid discovering expensive problems too late?

Answer pattern:

> Validate early, review documents, involve stakeholders, prototype carefully, make specs testable, and link tests back to requirements/specifications.

---

## 4. Prototyping

### What prototyping is

A prototype is an early, partial version/model of a system used to explore ideas, clarify requirements, or get feedback.

### Benefits

- Helps stakeholders understand vague ideas.
- Reveals missing or misunderstood requirements.
- Allows early user feedback.
- Helps compare design options.

### Risks of prototyping — likely 3-mark answer

Any three strong points:

1. **Too much effort may be spent on the prototype**, so it becomes expensive compared with the decision it was meant to support.
2. **Prototype code may accidentally become production code**, even if it was rushed, poorly designed, or not maintainable.
3. **Prototype may replace proper documentation**, leaving unclear requirements/specifications.
4. **Wrong stakeholders may approve the prototype**, so the system is validated by people who are not representative users/customers.
5. **Users may think the prototype is almost finished**, causing unrealistic expectations about cost, time, or quality.

### Model answer

Three risks of prototyping are: too much effort may be spent building the prototype; prototype code may be reused in the final system even though it was not engineered properly; and stakeholders may treat the prototype as a replacement for proper requirements/specification documentation.

---

## 5. Testing phases

### The testing ladder

| Phase | What it checks | Usually based on | Performed by |
|---|---|---|---|
| **Unit testing** | Individual methods/classes/components. | Low-level specs/design. | Developers. |
| **Integration testing** | Components working together. | Interface/design specs. | Developers/dev team. |
| **System testing** | Whole system behaviour. | System specs. | Test/dev team. |
| **Release testing** | Whether the full system is ready to release. | High-level specifications. | Internal testing/QA team. |
| **Acceptance testing** | Whether the customer/user accepts it. | Requirements/user needs. | Customer/client/users with QA. |

### Release testing vs acceptance testing

This is directly tested in the sample exam.

| Difference | Release testing | Acceptance testing |
|---|---|---|
| Linked to | High-level specifications. | Requirements. |
| Main question | “Is this version ready to show/ship?” | “Does the customer accept this system?” |
| Who does it | Internal company/testing team. | Client/customer/users, often with QA. |
| If it fails | Goes back to developers/specification fixes. | May go back to requirements because the user need may not be met. |

### Model answer for a 4-mark question

The testing most closely linked to **requirements** is **acceptance testing**, because it checks whether the system satisfies the customer/user needs. The testing most closely linked to **high-level specifications** is **release testing**, because it checks whether the complete product meets the specified system behaviour before release. Release testing is usually internal, while acceptance testing involves the client/customer. If release testing fails, the work usually returns to developers; if acceptance testing fails, the problem may go back to requirements because the system may not satisfy what the customer wanted.

### Common mistake

Do not say acceptance testing is just “testing by developers”. Acceptance testing is about whether the **customer/user accepts** the system.

---

## 6. Test-driven development, automated tests, and good tests

### TDD cycle

**Red → Green → Refactor**

| Stage | Meaning |
|---|---|
| **Red** | Write a failing test first. |
| **Green** | Write the minimum code needed to pass. |
| **Refactor** | Improve the code while keeping tests passing. |

### Benefits

- Forces clear understanding of expected behaviour.
- Gives regression tests for future changes.
- Supports safer refactoring.
- Encourages modular, testable design.
- Helps developers notice faults early.

### Limitations

- Bad tests give false confidence.
- Unit tests do not prove the whole system works.
- Hard to test UI, usability, performance, or vague requirements with TDD alone.
- Still needs integration, release, and acceptance testing.

### Good test case should include

- test name/purpose,
- input data or setup,
- expected output/result,
- actual result,
- pass/fail,
- link to requirement/specification where possible.

---

## 7. Continuous Integration and deployment across platforms

### What Continuous Integration means

Continuous Integration means developers integrate code into the mainline frequently, and automated builds/tests run so problems are found quickly and the software stays working.

### How CI helps deployment on multiple platforms

For a 5-mark answer, include:

1. **Definition of CI** — code is frequently integrated into the project mainline and checked automatically.
2. **Automated tests** — each change triggers tests to ensure the contribution has not broken the system.
3. **Configuration/build scripts** — separate scripts define how to compile/package the software for each platform or environment.
4. **Automated builds** — CI creates platform-specific builds consistently.
5. **Deployment to test machines/environments** — builds are deployed to real or virtual test machines to check they install and run correctly.
6. **Logs/feedback** — CI reports failures quickly so the team can fix them.

### Model answer for a 5-mark question

Continuous Integration is the practice of frequently integrating developers’ code into the main project version so that the software remains in a working state. A CI server can automatically build the project whenever code is pushed. It can run automated tests to check that new code has not broken existing functionality. It can use configuration scripts for different platforms, specifying libraries, build options, and environment settings. It can then deploy each compiled version to real or virtual test machines, so the team can check whether the software installs and runs correctly on each target platform.

### Common mistake

Do not answer only “CI runs tests”. For full marks, connect it to **build scripts/configuration** and **deployment to platform-specific test environments**.

---

## 8. Configuration management and deployment

### Configuration management

Configuration management controls and records the versions of:

- source code,
- libraries/dependencies,
- configuration files,
- build scripts,
- test data,
- documentation,
- releases,
- deployed environments.

It answers:

> What version is this? What changed? Who changed it? Can we rebuild it? Can we roll back?

### Deployment risks

Software can fail at deployment because:

- wrong configuration,
- missing dependencies,
- platform differences,
- database migration errors,
- environment variables/secrets missing,
- permissions/network issues,
- real user load is different from test conditions.

### Exam link

CI + configuration management + deployment testing = evidence that software is ready for release across different environments.

---

## 9. Software maintenance and evolution

### Maintenance/evolution definition

Maintenance/evolution is changing the software after delivery because faults are found, requirements change, users request improvements, platforms change, or laws/security needs change.

### Types of maintenance

| Type | Meaning | Example |
|---|---|---|
| **Corrective** | Fix faults. | Fix a crash or login bug. |
| **Adaptive** | Adapt to changed environment. | Update for a new OS/browser/API. |
| **Perfective** | Improve features, performance, or usability. | Add better search/filtering. |
| **Preventive** | Reduce future maintenance problems. | Refactor duplicated code. |

### Key exam point

Maintenance is often the most expensive part of the software lifecycle. Good requirements, specifications, tests, documentation, code quality, and configuration management reduce future maintenance cost.

---

## 10. Software risks vs project risks

### Software risks

Software risks are risks related to the software product itself, especially safety, security, dependability, privacy, or data protection.

Examples:

- user data may be leaked,
- system may allow unauthorised access,
- financial calculations may be wrong,
- system may fail under load,
- safety-critical behaviour may harm users.

### Project risks

Project risks affect the project’s schedule, budget, resources, or delivery.

Examples:

- key developer becomes unavailable,
- technology does not work as expected,
- requirements change late,
- team underestimates workload,
- external supplier is late,
- staff lack required skills.

### How software risk should affect the SE process

Likely 3-mark answer:

1. Software risks concern security, dependability, data protection, or similar product-level issues.
2. They should lead to extra requirements/specifications, including constraints and “shall not” behaviours.
3. They should lead to extra risk-based testing, especially release tests/security/dependability tests.

### Model answer

Software risks are product risks relating to issues such as security, dependability, privacy, or data protection. Considering these risks should affect specification because the system may need additional constraints, including behaviours it must prevent. It should also affect testing because high-risk behaviours need extra tests to check that the system is secure, reliable, and safe enough before release.

---

## 11. Risk management process

### Main stages

| Stage | Meaning |
|---|---|
| **Risk identification** | List what could go wrong. |
| **Risk analysis/prioritisation** | Estimate probability and impact. |
| **Risk planning** | Choose strategies for important risks. |
| **Risk monitoring** | Track indicators and respond if risk changes or occurs. |

### Risk strategies

| Strategy | Meaning | Example |
|---|---|---|
| **Avoidance** | Reduce chance of the risk happening. | Train junior developers early. |
| **Minimisation/mitigation** | Reduce impact if it happens. | Pair juniors with seniors so knowledge spreads. |
| **Contingency** | Plan what to do if it happens. | Reassign tasks if senior dev is absent. |
| **Monitoring** | Watch warning signs. | Track absence, velocity, unresolved defects. |

### Exam answer recipe for any risk question

Use this structure:

1. Identify the risk.
2. Say whether it is software risk or project risk.
3. Explain impact.
4. Suggest mitigation/avoidance/contingency.
5. Link it to a stage of the SE process.

Example:

> The senior developer being unavailable is a project risk because it may delay tasks and reduce team knowledge. Pair programming can mitigate it by transferring knowledge to junior developers and ensuring more than one person understands critical code. A contingency plan could reassign critical tasks if the developer is away.

---

## 12. Pair programming / paired coding

### What it is

Two developers work together on the same code/task, often with one writing code and the other reviewing/thinking/checking. They may swap roles.

### Benefits

- Built-in code review.
- Knowledge sharing.
- Junior developers learn from senior developers.
- Reduces “bus factor” because more than one person understands the code.
- Can improve code quality.
- Helps maintain consistency and standards.

### Risk mitigation answer from the sample exam

If the senior developer may be absent:

1. Pairing juniors with the senior developer transfers knowledge and skills.
2. Another person will understand the code/tasks if the senior developer is unavailable.

### Model answer

Pair programming mitigates this risk because junior developers can learn design and coding knowledge from the senior developer while working together. It also means knowledge is shared, so if the senior developer has to take leave, someone else understands the relevant code and can continue the work.

---

## 13. Critical path decisions

### What the critical path is

The critical path is the longest path through the project task network. It is the bottleneck route that determines the shortest possible project duration.

If a critical-path task is delayed, the whole project is likely delayed.

### How to answer “should this person be on critical path tasks?”

The exam accepts either side if argued well. You need:

- clear decision,
- two reasons,
- one counterargument.

### Option A: Do assign the senior developer to critical path tasks

**Decision:** Yes, assign them, but with pairing/backup.

Reasons:

1. Critical path tasks are the most important for keeping the project on schedule, so they may need the most experienced developer.
2. Pairing the senior developer on critical tasks helps junior developers learn the most important parts of the system.

Counterargument:

- If the senior developer is absent, critical path tasks may be delayed, so this is risky unless knowledge is shared.

### Option B: Do not assign the senior developer to critical path tasks

**Decision:** No, avoid assigning them as the sole owner of critical path tasks.

Reasons:

1. Their possible absence could directly delay the whole project if they own critical path tasks.
2. Critical tasks should have reliable coverage, ideally with multiple developers able to continue them.

Counterargument:

- The senior developer may be the best person for difficult critical tasks, so excluding them could reduce quality or speed.

### Best exam-safe answer

Choose **Option B with nuance**:

> I would not make the senior developer the sole owner of critical path tasks. Their possible absence is a project risk because delays on the critical path delay the whole project. Critical tasks should be paired or assigned with backup so junior developers can continue if needed. However, the senior developer should still support critical path tasks through pair programming and reviews because their experience is valuable.

---

## 14. Software Quality Assurance

### What software quality means

Software quality means the software is fit for purpose and meets both functional and non-functional expectations. Quality depends on the whole process, not just final testing.

Quality includes:

- correctness,
- reliability,
- usability,
- maintainability,
- security,
- performance,
- testability,
- clarity,
- consistency.

### QA is not just testing

Quality Assurance is about planning for quality, defining standards, inspecting work, using metrics, and improving the process.

### Why relying only on testers is a project risk

Likely 2-mark answer:

1. If quality problems are found only at testing time, it may be too late or expensive to fix them.
2. Testing cannot easily fix poor requirements, bad specifications, weak design, or missing standards created earlier.

### Model answer

Depending only on the testing team creates a project risk because problems are found late, when fixes are more expensive and may delay release. Also, testers may not be able to correct poor requirements or specifications because those mistakes were introduced much earlier in the process.

### Other QA activities at earlier stages

For a 4-mark answer, name four:

1. Requirements validation with stakeholders.
2. Inspection/review of specification documents.
3. Prototype reviews with clients/users.
4. Code conventions and naming standards.
5. Code reviews/inspections/pair programming.
6. Improved testing protocols and independent release testing.
7. Documentation standards.
8. Traceability between requirements, specifications, tests, and code.
9. Metrics collection, e.g. defects, test pass rates, review findings.

### Model 4-point answer

Other QA activities include validating requirements with stakeholders, inspecting specification documents before development, reviewing prototypes with clients to check the proposed design, and enforcing coding/documentation standards so the product is maintainable and consistent.

---

## 15. Agile Manifesto

### Four Agile values

Memorise these exactly enough:

1. **Individuals and interactions over processes and tools.**
2. **Working software over comprehensive documentation.**
3. **Customer collaboration over contract negotiation.**
4. **Responding to change over following a plan.**

Important nuance:

> Agile does not say the items on the right have no value. It says the items on the left are valued more.

### How to briefly describe each

| Value | Meaning |
|---|---|
| Individuals and interactions | Team communication matters more than blindly following tools/processes. |
| Working software | Real, running software is stronger evidence of progress than long documents. |
| Customer collaboration | Keep working with the customer instead of relying only on fixed contract terms. |
| Responding to change | Adapt to new information instead of rigidly following an outdated plan. |

### Common mistake

Do not list generic agile principles like “maintain simplicity” if the question asks for the **four original Agile Manifesto values**.

---

## 16. User stories across the SE process

### User story format

> As a **[type of user]**, I want **[goal]**, so that **[benefit]**.

Example:

> As a banking customer, I want to categorise my spending, so that I can understand where my money goes.

### How user stories can support different SE stages

| Stage | How user stories help |
|---|---|
| **Requirements definition** | Capture user goals and system uses. |
| **System design** | Explore designs from different actor/user viewpoints. |
| **Implementation planning** | Select/prioritise stories for a sprint or release. |
| **Testing** | Turn stories into acceptance/release test scenarios. |
| **Documentation** | Explain what the final system supports from the user’s perspective. |

### Model answer for 4 marks

User stories can be used in requirements definition to capture what different users want from the system. They can support system design by making designers consider the system from different actor viewpoints. They can be used in implementation planning by selecting stories for a sprint or release backlog. They can also support testing because each story can become a scenario or acceptance test showing whether the user goal has been met.

---

## 17. Agile vs traditional / plan-driven methods

### Traditional / plan-driven strengths

Plan-driven methods are useful when:

- requirements are stable,
- the domain is safety/security/regulation-heavy,
- formal documentation is needed,
- multiple specialist teams must coordinate,
- the organisation already has established processes,
- the customer expects fixed milestones/contracts.

### Agile strengths

Agile methods are useful when:

- requirements are vague or likely to change,
- user feedback is available,
- the product is exploratory or innovative,
- frequent working software helps learning,
- the team can collaborate closely,
- priorities may change.

### Scenario pattern from the sample exam

For the banking app scenario:

| Evidence for plan-driven | Evidence for agile |
|---|---|
| Handles important financial data. | The idea is vague. |
| Must meet legal/financial standards. | The bank wants to explore options. |
| Company has strong requirements/testing/QA teams. | Potential users are available for monthly discussions. |
| Company has experience using traditional methods for the bank. | Users are clients, so feedback matters. |

### Best hybrid answer

You can choose either primary approach if justified. A strong answer usually says:

> Use agile as the primary approach for exploring the vague customer-facing app, but integrate plan-driven controls for financial-data risk, legal standards, documentation, requirements validation, and formal testing.

### Model answer for the scenario

There are reasons to use a plan-driven approach because the app handles important financial data, must comply with legal/financial standards, and the company already has requirements, testing, and QA teams. There are also reasons to use agile because the idea is vague, the bank wants to explore different options, and potential users are available for monthly feedback sessions. I would use agile as the primary approach because the product idea is uncertain and user feedback is available. However, I would integrate plan-driven elements by doing an initial formal requirements/risk analysis for financial-data and legal constraints, and by using formal release/acceptance testing against those standards before deployment.

### Common mistake

Do not say “Agile means no documentation”. In a regulated financial project, agile still needs documentation, security requirements, and formal testing.

---

## 18. Project planning: PERT, Gantt, critical path, agile planning

### PERT chart

A PERT chart shows tasks and dependencies. It helps identify which tasks must happen before others and which paths determine project duration.

### Critical path

The critical path is the longest path through the task network. It is the bottleneck route. If a task on the critical path slips, the whole project duration may slip.

### Gantt chart

A Gantt chart shows tasks over time, including start dates, end dates, overlap, and schedule.

### Agile planning

Agile planning often uses:

- product backlog,
- user stories,
- sprint planning,
- sprint backlog,
- daily meetings,
- sprint review,
- retrospective,
- velocity/burndown measures.

### Exam link

Planning questions usually want you to connect schedule decisions to **risk**. Example: do not put one unavailable person as sole owner of critical path tasks.

---

## 19. High-yield answer templates

### Template A: “Define and describe”

Use:

> **[Term]** means **[definition]**. It matters because **[reason]**. In the SE process it is used during **[stage]**.

Example:

> Acceptance testing checks whether the system satisfies the user/customer requirements. It matters because it determines whether the customer accepts the system. It occurs near the end of validation, after release testing.

### Template B: “Compare two things”

Use:

> A is about **X**, whereas B is about **Y**. A is usually done by **...**, while B is usually done by **...**. If A fails, **...**; if B fails, **...**.

Example:

> Release testing checks the full system against high-level specifications and is usually internal. Acceptance testing checks the system against requirements and involves the customer. Release test failure usually returns work to developers, while acceptance test failure may indicate the original requirements were not met.

### Template C: “Scenario decision”

Use:

1. Identify evidence for option A.
2. Identify evidence for option B.
3. Choose one.
4. Add two ways to integrate the other.

Example:

> Agile is suitable because requirements are vague and users are available for feedback. Plan-driven methods are suitable because the system handles financial data and needs legal compliance. I would choose agile as the main approach, but add formal risk analysis and formal release/acceptance testing to satisfy legal/security requirements.

### Template D: “Risk answer”

Use:

> This is a **[project/software] risk** because **[impact]**. It can be managed by **[avoidance/mitigation/contingency]**. It should be monitored by **[indicator]**.

---

## 20. Most likely short-answer facts to memorise

### Must know cold

- Four SE activities: **Specification, Development, Validation, Evolution**.
- Requirement = **what users/stakeholders need**.
- Specification = **precise description of how the system/software will satisfy requirements**.
- Acceptance testing ↔ **requirements/customer acceptance**.
- Release testing ↔ **high-level specifications/internal readiness**.
- CI = **frequent integration + automated build/test/deploy feedback**.
- Software risk = **product risk**, e.g. security/data protection/dependability.
- Project risk = **delivery risk**, e.g. staff absence, delays, underestimation.
- Critical path = **longest/bottleneck path; delay delays project**.
- QA = **whole-process quality planning/inspection**, not just testing.
- Agile values = **Individuals, Working software, Customer collaboration, Responding to change**.
- User stories can support **requirements, design, planning, testing, documentation**.

### Easy marks phrases

Use these words in exam answers:

- traceability,
- validation,
- stakeholder needs,
- high-level specification,
- client/customer acceptance,
- automated testing,
- configuration scripts,
- deployment to test machines,
- risk mitigation,
- critical path,
- quality assurance activities,
- legal/financial standards,
- user feedback,
- vague requirements.

---

## 21. Practice questions based on the sample exam style

### Section A style

1. Name and describe the four generic software engineering activities.
2. Explain the difference between a requirement and a specification using an example.
3. Explain how a sequence diagram could be used at both requirements level and specification level.
4. Give three risks of prototyping.
5. Explain the difference between release testing and acceptance testing.
6. Explain how continuous integration supports deployment to multiple platforms.

### Section B style

7. Define software risk and give an example related to data protection.
8. Explain how software risk affects specification and testing.
9. Explain how pair programming reduces the risk of key staff absence.
10. Should an unreliable/possibly absent senior developer be placed on critical path tasks? Give two reasons and a counterargument.
11. Explain why relying only on the testing team for quality is risky.
12. Give four QA activities outside the testing phase.

### Section C style

13. List and briefly explain the four Agile Manifesto values.
14. Explain how user stories support requirements definition, design, sprint planning, and testing.
15. Given a regulated but vague financial app scenario, give two reasons for agile and two for plan-driven.
16. Choose agile or plan-driven for the scenario and explain how to integrate the alternative approach.

---

## 22. Mini quiz with answers

### Q1. What are the four fundamental SE activities?

**Answer:** Specification, Development, Validation, Evolution.

### Q2. What is the difference between requirement and specification?

**Answer:** A requirement describes what the stakeholder/user needs; a specification describes precise system/software behaviour that will satisfy the requirement.

### Q3. Which testing phase links most directly to requirements?

**Answer:** Acceptance testing.

### Q4. Which testing phase links most directly to high-level specifications?

**Answer:** Release testing.

### Q5. Give three risks of prototyping.

**Answer:** Too much work may be spent on it; prototype code may enter production; it may replace documentation; wrong stakeholders may approve it; users may get unrealistic expectations.

### Q6. What should CI include for deployment across platforms?

**Answer:** Frequent integration, automated tests, configuration/build scripts per platform, automated builds, deployment to test machines/environments, and failure feedback/logging.

### Q7. What is a software risk?

**Answer:** A product-level risk involving security, dependability, privacy, data protection, safety, or similar software qualities.

### Q8. What is a project risk?

**Answer:** A risk affecting schedule, budget, staffing, resources, or delivery.

### Q9. Why does pair programming help if a senior developer may be absent?

**Answer:** It transfers knowledge to junior developers and ensures someone else understands the code/tasks.

### Q10. What is the critical path?

**Answer:** The longest path through the task network; it determines the shortest possible project duration and delays on it delay the whole project.

### Q11. Why is quality assurance more than testing?

**Answer:** Because quality depends on requirements, specifications, design, coding standards, reviews, documentation, traceability, metrics, and testing throughout the process.

### Q12. What are the four Agile Manifesto values?

**Answer:** Individuals and interactions over processes and tools; working software over comprehensive documentation; customer collaboration over contract negotiation; responding to change over following a plan.

---

## 23. Last-night revision plan

### 30 minutes: Memorise definitions

- Four SE activities.
- Requirement vs specification.
- Release vs acceptance testing.
- Software risk vs project risk.
- Agile values.
- Critical path.

### 45 minutes: Practise model answers

Write answers for:

- prototyping risks,
- CI for multiple platforms,
- QA activities,
- pair programming risk mitigation,
- agile vs plan-driven scenario.

### 30 minutes: Scenario drilling

For any scenario, underline:

- uncertainty/vague idea → agile,
- user feedback available → agile,
- legal/security/safety/financial data → plan-driven controls,
- existing formal teams/process → plan-driven,
- change/exploration → agile,
- high-risk data → formal specs/tests.

### 15 minutes: Do not confuse list

- Acceptance ≠ release.
- Requirement ≠ specification.
- Software risk ≠ project risk.
- QA ≠ only testing.
- Agile ≠ no documentation.
- Critical path ≠ shortest path.

---

## 24. Ultra-compressed final memory sheet

If stuck in the exam, write from this:

> Software Engineering reduces failure by turning vague user needs into validated requirements, precise specifications, planned development, tested software, controlled deployment, and maintainable evolution. Quality and risk are managed throughout the process using validation, reviews, testing, CI, configuration management, pair programming, QA standards, and project planning.

