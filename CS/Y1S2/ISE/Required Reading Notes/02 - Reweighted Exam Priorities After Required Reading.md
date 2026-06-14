# Reweighted Exam Priorities After Required Reading

This is the revised view after combining:
- lecture slides `01-19`;
- exam briefing, practice questions, and past papers;
- required online readings;
- the three added reading PDFs.

## What Moved Up In Importance

### 1. Requirements Engineering

This is now the highest-priority theme.

Know:
- Why requirements are hard and project-critical.
- Why bad requirements cause rework, delays, budget overruns, and failure.
- Requirements elicitation, stakeholder analysis, personas, use cases, and validation.
- Functional vs non-functional requirements.
- Why missing non-functional requirements can be severe.
- Requirements inspections/reviews and early validation.

Core answer shape:
- Requirements are the foundation for design, implementation, testing, acceptance, planning, and quality.
- If they are wrong, the team may build the wrong product even if coding is technically good.

Sources:
- Lectures `03-06`.
- Practice/past papers.
- Stack Overflow requirements article.
- Requiment failure article.
- IEEE requirements risks PDF.

### 2. Maintainability And Implementation Quality

This is stronger than the past papers alone made it look.

Know:
- Maintainable software is easy to understand, change, verify, and hand over.
- Technical debt comes from skipping tests, documentation, refactoring, warnings, comments, and rationale.
- Coding conventions support readability, understandability, and maintainability.
- Code reviews and pair programming improve quality and spread knowledge.
- Refactoring is preventative maintenance.

Core answer shape:
- Implementation quality is not just "code works"; good code remains changeable during evolution and can be understood by other developers.

Sources:
- Lectures `10`, `15`, `16`.
- Software Sustainability Institute maintainability reading.
- Code conventions PDF.
- Industry experience PDF.

### 3. Testing, TDD, CI, And Evidence

TDD is specifically required reading, so it deserves sharper revision.

Know:
- Unit, integration, release, acceptance, and user testing.
- TDD cycle: small failing test, minimal passing code, refactor, repeat.
- TDD benefits and pitfalls.
- CI/CD as automated build/test/deployment support.
- Evidence of good practice: tests committed with code, code coverage, CI logs, issue/branch/merge-request traceability.

Core answer shape:
- Testing supports validation and quality, but testing alone is too late; combine early requirements validation, TDD, automated tests, CI, release testing, and acceptance/user feedback.

Sources:
- Lectures `11-14`.
- Agile Alliance TDD reading.
- Industry experience PDF.

### 4. Specifications And Human-Readable Documentation

The required reading makes this more than a dry definition.

Know:
- Requirements say what is needed; specifications say how the system will be built or behave in enough detail to guide implementation.
- A spec must be readable and reviewed, otherwise it will not guide development.
- Use simple language, examples, stories, screenshots/mockups, diagrams, lists, and whitespace.
- Explain the big picture before detail.

Core answer shape:
- A good specification is not just precise; it is understandable to the people who must approve, build, test, and maintain the software.

Sources:
- Lectures `07-09`.
- Joel on Software functional specifications reading.
- Agile Modeling UML readings.

### 5. UML Models As Communication And Validation Tools

The activity/sequence diagram readings reinforce this.

Know:
- Activity diagrams model workflows, use-case logic, business rules, decisions, parallel activities, and swimlanes.
- Sequence diagrams model the ordered flow of interactions across actors, systems, services, objects, or methods.
- UML can be used at requirements level and design/specification level.
- Agile models should be useful, not overproduced.

Core answer shape:
- Models help stakeholders/developers validate logic and communicate behaviour before implementation.

Sources:
- Lecture `05`, `09`.
- Agile Modeling activity and sequence diagram readings.

### 6. Usability, Accessibility, And User Involvement

This matters especially for scenario questions.

Know:
- Usability means users can achieve goals effectively and easily.
- Usability can be measured with user testing, success rates, satisfaction, and observation.
- Accessibility requirements are non-functional requirements.
- User involvement improves requirements, prototypes, acceptance testing, and final quality.

Core answer shape:
- If the scenario involves real users, public systems, accessibility, or uncertain workflows, involve users early and repeatedly.

Sources:
- Lectures `03`, `04`, `08`, `12`.
- Digital.gov usability reading.
- Practice scenario about blind users.

### 7. Security And Authorization

This is a smaller but distinct reading-only addition.

Know:
- Authentication proves identity; authorization decides permissions.
- Authorization can be role-based and should enforce least privilege.
- UI checks are not enough; business and data-tier checks may also be required.
- Sensitive-data scenarios require authorization as a non-functional requirement and testing/design concern.

Core answer shape:
- Security is not an afterthought. It affects requirements, specifications, architecture, testing, and deployment.

Sources:
- Microsoft authorization reading.
- Lecture `18` on software risks.

## What Stayed Important

### Agile vs Traditional

Still important because it appears in lectures, readings, and practice questions.

Know:
- Agile values and principles.
- Scrum, XP, Kanban.
- When agile fits and when plan-based methods fit.
- Why "we are agile so we do not need requirements" is wrong.
- Hybrid answers are often strongest.

### Project Planning And Risk

Still important because past papers/practice questions use it directly.

Know:
- Work breakdown, dependencies, PERT/Gantt, critical path, staffing, milestones.
- Software vs project risks.
- Avoidance, mitigation/minimisation, contingency.
- Risk monitoring.

## What Is Less Likely To Need Deep Memorisation

- Detailed Microsoft/.NET-specific authorization APIs/classes.
- Exact syntax of UML notation beyond common elements.
- Exact statistics from articles.
- Vendor/product-specific details such as Cypress setup details.
- Exact named sources/authors unless your lecturer expects reading citation.

You should know the principles and be able to apply them to scenarios.

## New Short Priority List

If revising under time pressure:

1. Requirements: failures, elicitation, stakeholders, personas, use cases, validation, non-functional requirements.
2. Testing: testing stages, TDD, acceptance throughout, CI/CD.
3. Maintainability: coding conventions, reviews, pair programming, refactoring, technical debt.
4. Specs/UML/prototyping: clear specs, activity/sequence diagrams, prototypes, requirements vs design use.
5. Agile: values, Scrum, XP, Kanban, agile vs plan-based, hybrid reasoning.
6. Quality/risk/project planning: QA beyond testing, software/project risk, critical path/Gantt/staffing.
7. Usability/security: user goals, accessibility, authorization, sensitive data.

