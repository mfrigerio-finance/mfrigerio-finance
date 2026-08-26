# Architecture & Design Approach

**Business objective → Financial logic → Process → Controls → Data → Systems → Validation → Decision**

This page describes the approach I use when finance, operations, data and enterprise systems need to behave as one controlled operating model.

The objective is not architecture for its own sake. The objective is to make **financial meaning explicit, ownership clear, controls enforceable, data reconcilable and system behaviour explainable**.

## 1. Start with the decision and control objective

A finance or transformation design should begin with the business question it must answer.

Typical starting questions include:

- What decision or operating outcome is required?
- Which financial concepts must remain consistent?
- Which sources are authoritative?
- Who owns each input, transformation, approval and exception?
- What must reconcile before an output can be trusted?
- Which failures should stop the process rather than silently default?
- What evidence must remain for management, audit or recovery?

Technology selection comes after those boundaries are understood.

## 2. Model financial meaning explicitly

Financial systems should preserve the business meaning behind a number.

Important domain concepts commonly include:

- legal entity and management entity;
- chart of accounts and management mappings;
- cost centres, profit centres and other cost objects;
- period, effective date and reporting version;
- actual, budget, forecast and scenario;
- currency, FX basis and translation logic;
- intercompany relationships and eliminations;
- liquidity and cash-flow classification;
- CAPEX / OPEX treatment;
- approval state, ownership and override authority.

The design goal is to prevent financial meaning from being lost as information moves between people, files, systems and reports.

## 3. Treat process, data and systems as one chain

A typical finance-information flow can be represented as:

```text
Operational / Financial Sources
            |
            v
       Input Controls
            |
            v
   Mapping & Normalisation
            |
            v
 Reconciliation & Exceptions
            |
            v
 Finance / Management Logic
            |
     +------+-------+-------+
     |              |       |
     v              v       v
 Actual vs Plan   Cash    Entity /
 & Variance      Views   Intercompany
     |              |       |
     +------+-------+-------+
            |
            v
   Decision-Ready Reporting
            |
            v
     Management Action
```

The key principle is that reporting should remain connected to **source ownership, transformation logic, reconciliation status and exception evidence**.

## 4. Put controls where they can be enforced

A control written only in documentation is weaker than a control embedded in the operating process or system boundary.

Depending on the environment, control points can include:

- input validation;
- approval workflow;
- segregation of duties;
- entity and access scope;
- master-data ownership;
- posting and mapping rules;
- reconciliation thresholds;
- acceptance criteria;
- audit trails;
- change control;
- exception escalation.

The preferred design is **fail closed** when an unknown, stale or inconsistent state could create a misleading financial output.

## 5. Separate responsibilities without separating accountability

A controlled operating model normally has several layers:

```text
Business / Finance Requirement
            |
            v
 Process & Control Design
            |
            v
 Functional / Domain Logic
            |
            v
 Data & Integration Design
            |
            v
 ERP / EPM / Application Layer
            |
            v
 Validation & Reconciliation
            |
            v
 Reporting / Decision Support
```

Different specialists may own different layers, but hand-offs should not break the chain of accountability.

Finance should be able to explain the requirement. Technology should be able to explain the implementation. Management should be able to explain the resulting decision.

## 6. Design integrations around ownership and contracts

An integration is not complete merely because data moves successfully.

A controlled interface should make clear:

- source system of record;
- data owner;
- expected structure and grain;
- timing and effective date;
- validation rules;
- mapping responsibility;
- duplicate or replay behaviour;
- exception path;
- reconciliation back to source;
- downstream impact if the interface fails.

This applies whether the interface is an ERP integration, API, file exchange, data pipeline or reporting feed.

## 7. Reconcile before presentation

A polished dashboard cannot compensate for uncertain source data.

Before information is treated as decision-ready, the design should answer:

- Is the dataset complete?
- Does it reconcile to the relevant system of record?
- Are mapping differences understood?
- Are intercompany differences resolved or visible?
- Are late, missing or stale inputs identified?
- Can a reviewer trace a reported value back to its source and transformation logic?

Reconciliation is therefore part of architecture, not a final manual check added after reporting.

## 8. Make failure states explicit

Finance and control environments should distinguish between:

- valid zero;
- missing value;
- stale value;
- rejected value;
- unavailable dependency;
- inconsistent state;
- unapproved override;
- unknown state.

Collapsing these conditions into the same output creates false confidence.

A robust design keeps uncertainty visible until the responsible owner resolves or accepts it.

## 9. Build validation into transformation delivery

Transformation validation should cover both business meaning and technical behaviour.

Typical layers include:

- requirement traceability;
- acceptance criteria;
- representative business scenarios;
- calculation validation;
- integration testing;
- reconciliation;
- UAT;
- authorization and segregation-of-duties checks;
- exception and failure-path testing;
- cutover and operating-readiness validation.

The objective is not simply to prove that a system works. It is to prove that it produces the intended financial and operational result under realistic conditions.

## 10. Preserve auditability and explainability

A controlled design should make it possible to answer:

- Where did this value originate?
- Which rule or mapping transformed it?
- Which reporting version and period were used?
- Who approved or changed the relevant input?
- What exception occurred?
- What was unresolved at the time the report or decision was produced?

Auditability is part of the operating model, not a logging feature added at the end.

## 11. Use technology as an execution layer

Technical fluency helps make finance transformation more precise and testable.

Professional work includes technologies and patterns such as:

- SQL and relational data models;
- Python and workflow automation;
- REST APIs and typed interfaces;
- PostgreSQL and controlled persistence;
- data validation and reconciliation;
- authorization and entity isolation;
- automated verification;
- technical documentation.

The technology is not the proposition by itself. The proposition is the ability to use it while preserving financial logic, control requirements and operating accountability.

## Delivery model

The recurring delivery sequence is:

### 1. Frame
Define objective, decision, stakeholders, scope and control requirements.

### 2. Analyse
Understand current process, financial logic, data ownership, pain points and exceptions.

### 3. Design
Define target process, requirements, controls, data flows, system behaviour and acceptance criteria.

### 4. Deliver
Coordinate implementation across finance, operations, technology, vendors and management.

### 5. Validate
Execute UAT, reconciliation, scenario testing, defect analysis and operating-readiness checks.

### 6. Improve
Use defects, exceptions, cycle times and root causes to refine the operating model.

## Selected design principles

### Financial meaning before system convenience
System structures should serve the finance requirement rather than forcing uncontrolled workarounds around it.

### Explicit ownership before automation
Automating an unclear process usually makes the ambiguity faster, not better.

### Reconciliation before presentation
Decision-ready information should have an explainable path back to source evidence.

### Controls at enforceable boundaries
Approvals, access rules, validation and reconciliation should be placed where they can actually prevent or expose an invalid state.

### Visible exceptions over silent defaults
Unknown or inconsistent states should remain visible rather than being transformed into apparently valid outputs.

### Architecture that survives hand-off
Processes, controls, requirements and operating decisions should remain understandable after the transformation team leaves.

## Related professional evidence

- [Hiring Brief](./HIRING.md)
- [Professional Portfolio](./PORTFOLIO.md)
- [Capability Evidence Matrix](./EVIDENCE.md)
- [Sanitised Professional Case Studies](./CASE_STUDIES.md)

## Design principle

**Make the financial meaning explicit, assign ownership, put controls where they can be enforced, preserve the evidence needed to explain the result, and validate the behaviour that matters.**
