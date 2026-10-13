# Interview Stream 10 — Breaks, Rounding, Grace Periods & Exceptions

## Outcome
Demonstrate sound workforce-time design judgment for break treatment, rounding, grace/tolerance windows, admissible time, missing records and exception handling—while protecting policy intent, traceability and downstream accuracy.

## Scope and decision principles
**Primary focus:** break handling, paid/unpaid break definitions, rounding semantics, grace periods, admissibility, missing time, boundary conditions and exception governance.

Keep the discussion centered on workforce time management. Explain downstream payroll dependencies only where they affect validation or risk. Product behavior must be checked against the actual SAP SuccessFactors edition/release, enabled capabilities, country scope and tenant configuration.

Before proposing a rule, clarify:
1. **Policy:** What approved business, legal or collective-agreement rule applies?
2. **Population:** Which employees, schedules, locations and effective dates are in scope?
3. **Semantics:** Is the rule applied to a punch, a duration, a derived interval, a shift, or a period total?
4. **Exceptions:** What happens when records are missing, contradictory, late or outside tolerance?
5. **Evidence:** How will the result be explained, tested, approved and audited?

Do not assume that a grace period authorizes unpaid work, that rounding is always permitted, that every break is automatically deducted, or that a product supports a particular rule in every release. These require policy and product verification.

## STAR response standard
- **Situation:** Describe the business context, affected population, issue, constraints and impact.
- **Task:** State what you personally owned and what was outside your remit.
- **Action:** Explain discovery, policy interpretation, options, design/configuration, dependencies, controls, edge cases and validation. Distinguish your contribution from the wider team's work.
- **Result:** Use only verified evidence such as signed-off policy decisions, passing tests, reconciled examples, closed defects or documented controls. Do not invent metrics or client outcomes.
- **SME probe:** Defend the policy interpretation, boundary behavior, exception route and proof.
- **Practice integrity:** These scenarios are interview exercises, not claims about your personal history. Use authentic experience or label the answer as a lab/design exercise.

## 20 detailed scenario-based STAR interview practices

### 1. Break deductions create employee complaints
**Situation:** Employees say recorded work time is shorter than expected after breaks are considered. Some believe the system deducted a break they did not take; others expect a scheduled break to be deducted automatically.

**Task:** Determine the approved break policy and isolate whether the mismatch comes from schedule assumptions, recorded evidence, break eligibility, configuration or communication.

**Action:**
1. Collect representative cases with schedule, time entries/events, break records, employee group and expected result.
2. Ask the policy owner to define whether the break is scheduled, recorded, automatically deducted, paid or unpaid, and how missed or partial breaks are treated.
3. Map the source data to the calculated interval and final result; do not infer that a planned break proves a break was taken.
4. Test a full break, no break, partial break, multiple breaks and a shift that crosses a date boundary.
5. Document the decision, exception path and user-facing explanation; validate product support for the target release.

**Result/evidence:** A signed-off break decision matrix and reproducible tests showing actual versus expected outcomes.

**SME probe:** *Should the system always deduct a scheduled unpaid break?*  
**Answer outline:** Not as a universal rule. Establish the policy and evidence model first, then verify supported product behavior. Explicitly test missed and partial breaks and ensure the process does not silently create an inaccurate record.

### 2. Break rules vary by employee group or jurisdiction
**Situation:** A global template's break behavior fits most employees but conflicts with a local rule, collective agreement or particular worker population.

**Task:** Support justified variation without creating uncontrolled rule proliferation.

**Action:**
1. Identify the authoritative source, effective dates, covered populations and policy owner for each variation.
2. Separate mandatory legal/contractual differences from preferences and inherited legacy practices.
3. Compare a shared baseline with controlled variants or eligibility-driven rules, considering maintainability and auditability.
4. Define how employees are assigned, how transfers are handled and who approves changes.
5. Regression-test the baseline and every affected population, including effective-dated changes.

**Result/evidence:** A variation register, ownership model and approved regression results.

**SME probe:** *How do you stop every business unit from demanding its own exception?*  
**Answer outline:** Require an authoritative policy basis, documented impact and named approval. Prefer standard behavior unless a defensible requirement justifies variation.

### 3. A rounding request may distort time or create compliance risk
**Situation:** Operations asks to round clock-in and clock-out times to simplify administration, but the policy and potential employee impact are unclear.

**Task:** Determine whether rounding is allowed, what it applies to and how fairness and compliance will be validated.

**Action:**
1. Ask for the approved policy and jurisdictional/legal review; do not treat operational convenience as sufficient authority.
2. Clarify the unit, direction, interval, tie-breaking semantics and whether rounding applies to each event, interval or aggregate.
3. Compare alternatives using actual sample patterns, including early/late punches and different shift lengths.
4. Test whether the rule systematically benefits or disadvantages a population and whether it changes overtime or premium thresholds.
5. Obtain approval, document limitations and establish a monitoring/review process before release.

**Result/evidence:** A policy-approved rounding specification, impact analysis and boundary-test evidence—or a documented decision not to implement the request.

**SME probe:** *Is rounding to the nearest five minutes always acceptable?*  
**Answer outline:** No universal answer is safe. Confirm applicable law and policy, then verify exact product semantics and test employee impact. Do not promise compliance based only on a common industry practice.

### 4. Grace periods are confused with rounding
**Situation:** Stakeholders use “grace period,” “tolerance” and “rounding” interchangeably, leading to conflicting expectations about late arrival or early departure.

**Task:** Separate the business concepts and define the intended outcome for each.

**Action:**
1. Ask what behavior the policy intends: an exception alert, an attendance classification, acceptance of a record, or alteration of the calculated time.
2. Define the start/end boundaries, inclusivity, units and population for each concept.
3. Draw examples inside, exactly at and outside the tolerance window.
4. Check whether a grace window changes the record or merely changes exception handling; do not assume one from the other.
5. Document distinct rules and test their interaction with schedule deviations, overtime and reporting.

**Result/evidence:** A glossary, decision table and signed-off test cases that distinguish tolerance from time calculation.

**SME probe:** *If a late punch is within grace, should the recorded time be changed?*  
**Answer outline:** Not automatically. First determine whether policy calls for a classification/exception decision or a change to time quantity. Preserve source evidence and verify the implemented behavior.

### 5. A boundary condition was missed in design
**Situation:** UAT passes for ordinary shifts, but a punch exactly at the grace-period boundary or rounding interval produces an unexpected result.

**Task:** Reproduce the issue, clarify boundary semantics and prevent regression.

**Action:**
1. Write the expected comparison precisely: inclusive or exclusive, and measured against which timestamp or duration.
2. Create minimal tests just before, exactly at and just after the boundary.
3. Trace the raw event, time zone, schedule and rule inputs before inspecting the final result.
4. Confirm whether rounding occurs before or after another evaluation step; verify rather than assume.
5. Add the scenario to regression coverage and obtain policy-owner confirmation of expected results.

**Result/evidence:** A reproducible defect or clarified requirement, passing boundary tests and updated traceability.

**SME probe:** *Why is an ordinary test not enough?*  
**Answer outline:** It cannot prove exact comparison semantics or sequencing. Boundary tests expose inclusive/exclusive conditions, rounding ties and order-of-operations errors.

### 6. A production-like result is wrong and the team proposes changing configuration immediately
**Situation:** A test shows a break deduction or rounded duration that appears incorrect, and the team wants to modify the rule before investigating the inputs.

**Task:** Find the cause without introducing unrelated regressions.

**Action:**
1. Preserve the exact test case and compare expected policy behavior with actual output.
2. Validate schedule, time zone, source events, approvals, break evidence and employee eligibility.
3. Trace the result step by step through supported processing stages and identify where the first divergence occurs.
4. Compare a passing case with a failing case, changing one relevant variable at a time.
5. Make a controlled change only after identifying the cause; run focused and regression tests.

**Result/evidence:** Root-cause analysis, approved correction and evidence that the original defect and adjacent cases behave as expected.

**SME probe:** *What is the risk of changing a rounding rule before checking source events?*  
**Answer outline:** The change can hide bad source data and alter valid cases across the population. Establish the earliest divergence first, then correct the responsible layer.

### 7. Policy owner and operations disagree about missed breaks
**Situation:** Operations wants to deduct the planned break even when an employee reports that it was missed; the policy owner is concerned about accuracy and compliance.

**Task:** Facilitate a policy decision and ensure the system reflects approved treatment rather than an informal compromise.

**Action:**
1. Separate the facts (planned break, recorded evidence, employee report) from assumptions.
2. Confirm applicable law, agreement and organizational policy with the authorized owner.
3. Present options and consequences, including auditability, employee correction, manager approval and downstream effects.
4. Agree how missing or disputed break evidence is represented and who can resolve it.
5. Record the decision and create tests for missed, partial, disputed and corrected breaks.

**Result/evidence:** A documented policy decision, assigned exception ownership and approved test evidence.

**SME probe:** *What if the operational leader insists on automatic deduction?*  
**Answer outline:** Explain the evidence and risk, request the authorized policy decision, document the residual risk and escalate through governance. Do not encode an unapproved assumption as policy.

### 8. Manual exception handling is growing
**Situation:** Managers regularly edit time records to address missing punches, late arrivals, missed breaks or rounding disputes. Similar cases are handled inconsistently.

**Task:** Decide which exceptions should remain manual and which can be standardized or system-supported.

**Action:**
1. Categorize exceptions by frequency, risk, cause, affected population and resolution time.
2. Separate data correction from policy exception and approval; these may need different controls.
3. Define required evidence, reason codes, approval roles, time limits and escalation paths.
4. Automate only stable, policy-approved cases; retain human review where evidence or judgment is required.
5. Measure repeat incidents and sample correction records for completeness and unauthorized patterns.

**Result/evidence:** An exception taxonomy, workflow/ownership design and a control checklist.

**SME probe:** *Should all common exceptions be automated?*  
**Answer outline:** No. Automate predictable and authorized decisions. Exceptions involving disputed evidence, policy interpretation or compliance risk may require review.

### 9. Different schedules create inconsistent break or grace results
**Situation:** The same tolerance or break logic behaves differently for part-time, rotating, overnight or flexible schedules.

**Task:** Establish which schedule attributes are inputs to the policy and test each in-scope pattern.

**Action:**
1. Inventory schedule types, planned start/end, break placement, workday boundaries and employee assignments.
2. Clarify whether the rule is anchored to scheduled time, actual event time, shift start or a period total.
3. Test short shifts, long shifts, split shifts, overnight shifts and schedule changes.
4. Verify eligibility and effective dating when an employee changes schedule or population.
5. Document exclusions and avoid applying one schedule's assumptions globally.

**Result/evidence:** A schedule coverage matrix and passing tests for each in-scope pattern.

**SME probe:** *Why can the same grace interval produce different business outcomes?*  
**Answer outline:** The baseline schedule and policy context may differ. Identify the reference point and population explicitly, then test rather than infer behavior.

### 10. A product capability is assumed to support a complex rounding rule
**Situation:** A design proposal depends on a specific rounding mode or break-handling behavior, but the team has not verified that the target product release supports it as expected.

**Task:** Validate feasibility before making a delivery commitment.

**Action:**
1. State the required behavior in testable terms, avoiding a solution-led feature assumption.
2. Check official documentation for the relevant edition/release and confirm tenant configuration or enablement dependencies.
3. Prototype a minimal representative case in a safe environment where available.
4. Compare standard capability, supported configuration, integration/custom approach and a controlled process alternative.
5. Record evidence, constraints, upgrade implications and decision ownership before finalizing the design.

**Result/evidence:** A capability decision record with verified sources and a tested recommendation.

**SME probe:** *Would you rely on a feature description from a different release?*  
**Answer outline:** No. Confirm the release and scope, then validate the exact behavior. Distinguish documented capability from behavior proven in the target tenant.

### 11. Local policy or collective agreement changes break handling
**Situation:** A jurisdiction or agreement specifies different break duration, timing, eligibility or treatment from the current template.

**Task:** Ensure the implementation follows authoritative requirements and changes are governed.

**Action:**
1. Obtain the current policy text and effective date from the responsible HR/legal/employee-relations owner.
2. Translate it into precise conditions, including exceptions, partial shifts and employee coverage.
3. Identify impacted schedules, populations, valuation rules, interfaces and reports.
4. Test before/after effective dates and employees moving between covered groups.
5. Define review ownership so future policy changes trigger impact analysis and regression.

**Result/evidence:** An approved requirement trace, impacted-object list and effective-date test results.

**SME probe:** *Can the architect interpret an ambiguous agreement independently?*  
**Answer outline:** The architect can surface ambiguities and model options but should not substitute for the authorized legal/policy interpretation. Record the decision owner and evidence.

### 12. Downstream results differ after rounding or break treatment
**Situation:** The originating time process appears consistent, but a downstream consumer receives a different duration or category after mapping, aggregation or reprocessing.

**Task:** Locate the discrepancy across the interface boundary and define reconciliation.

**Action:**
1. Agree the source-of-truth quantity, unit, precision, date semantics and mapping contract.
2. Compare source entries, calculated intervals, outbound payload, transformation and received result.
3. Test fractional units, boundary values, corrected entries and records crossing periods.
4. Confirm retry/idempotency and duplicate-handling behavior where relevant.
5. Assign ownership to the layer where the contract first diverges and reconcile affected records.

**Result/evidence:** A mapping specification, end-to-end test cases and a documented reconciliation result.

**SME probe:** *Should the source rounding rule be changed to match a downstream display?*  
**Answer outline:** Not without confirming the contract. A display/serialization issue may belong downstream; change the source rule only if the approved policy or source result is incorrect.

### 13. The business asks for a “fairness” metric without defining it
**Situation:** Leadership asks for a report on grace-period exceptions or break deductions, but stakeholders disagree about what should count as an exception and which population is comparable.

**Task:** Define a meaningful, reproducible measure before implementing a dashboard or operational target.

**Action:**
1. Specify the event counted, denominator, period, employee population and exclusions.
2. Separate occurrence counts from employee counts and from unresolved exception counts.
3. Define data sources, time zone, correction treatment and duplicate suppression.
4. Validate the metric against a manually reviewed sample and document interpretation limits.
5. Assign a business owner and review whether the metric could encourage unsafe behavior, such as suppressing legitimate break reports.

**Result/evidence:** A metric definition, sample reconciliation and named ownership.

**SME probe:** *Why can a lower exception count be a bad outcome?*  
**Answer outline:** It may reflect suppressed reporting or a changed denominator rather than better control. Pair counts with resolution quality, data completeness and employee/policy outcomes.

### 14. A late change arrives before UAT sign-off or cutover
**Situation:** A stakeholder asks to alter rounding, grace or break behavior late in delivery, potentially invalidating previously completed tests.

**Task:** Make a risk-based decision with clear evidence and approval.

**Action:**
1. Clarify urgency, policy authority, effective date and affected population.
2. Perform impact analysis across rules, schedules, exception flows, interfaces, reporting and training.
3. Identify minimum mandatory tests and regression scope; estimate the evidence required for safe release.
4. Present options: include with full validation, defer, or use an approved interim process where permitted.
5. Document the decision, residual risk, owner, rollback/contingency and communication plan.

**Result/evidence:** A controlled change decision and updated test/sign-off record.

**SME probe:** *What if leadership accepts the risk of an untested change?*  
**Answer outline:** Document the unvalidated scope, likely impact, mitigation and decision authority. Escalate material compliance or employee-impact risks and do not describe the change as validated.

### 15. Repeated incidents are resolved but keep returning
**Situation:** Support repeatedly fixes missing-punch, grace-period or break exceptions without reducing recurrence.

**Task:** Find and address the systemic cause.

**Action:**
1. Group incidents by schedule, device/source, rule, employee group, time zone and reason.
2. Reproduce a representative case and check whether policy, source data, assignment, configuration or user guidance is at fault.
3. Distinguish recurring training gaps from a design defect or integration/data-quality issue.
4. Add a preventive validation, monitoring control, runbook step or targeted regression test.
5. Track recurrence using an agreed definition and sample closure evidence.

**Result/evidence:** Root-cause analysis, a preventive control and a reviewable recurrence measure.

**SME probe:** *How do you prove that the solution prevents recurrence?*  
**Answer outline:** Demonstrate the old failure, show the control/test catches or prevents it, validate adjacent cases and review subsequent incidents.

### 16. Audit asks who changed a time record and why
**Situation:** An employee's record has been corrected or an exception overridden, and an auditor needs to understand the original evidence, reason, approval and resulting calculation.

**Task:** Ensure the process supports traceability and least-privilege access.

**Action:**
1. Identify required evidence: original record/event, changed value, reason, actor, timestamp, approval, relevant policy and resulting output where available.
2. Define which roles can view, edit, approve and administer exceptions.
3. Test unauthorized edits, missing reasons, incomplete approvals and audit retrieval.
4. Limit disclosure to the necessary employee and period; confirm retention requirements with control owners.
5. Provide a repeatable explanation linking the record change to the calculated result.

**Result/evidence:** An access matrix, audit evidence checklist and successful trace test.

**SME probe:** *What is the minimum convincing audit trail?*  
**Answer outline:** Enough to reconstruct the original state, authorized change, rationale, approver and resulting outcome, subject to actual product capabilities and retention policy.

### 17. Employee disputes a rounded or grace-adjusted result
**Situation:** An employee believes their actual time was altered or a tolerance rule was applied unfairly.

**Task:** Investigate objectively, explain the governing rule and provide an approved correction route.

**Action:**
1. Preserve the original source evidence and identify any subsequent edits or transformations.
2. Compare the case with the approved policy and similarly situated cases, checking schedule, population and effective date.
3. Explain what was recorded, what was calculated and what was classified, using plain language.
4. If the outcome is wrong, route a controlled correction and assess downstream impact; if it is correct, explain why and record the inquiry as required.
5. Feed recurring misunderstandings into guidance or policy clarification.

**Result/evidence:** A traceable case resolution and an understandable explanation.

**SME probe:** *Would you tell the employee that the system is correct because the rule ran?*  
**Answer outline:** No. Verify source data and policy first. System execution is not proof of correctness; explain evidence and use the approved correction process.

### 18. Migration reveals inconsistent legacy break and rounding rules
**Situation:** Historical records or balances differ between the legacy system and the target, partly because rounding or break semantics are not equivalent.

**Task:** Separate data defects from intentional policy/design differences and establish cutover criteria.

**Action:**
1. Build a sample by schedule, population, break type, rounding edge and period boundary.
2. Document legacy semantics and map them to the approved target behavior; identify non-equivalent cases explicitly.
3. Reconcile source events, calculated durations, balances and downstream quantities separately.
4. Classify each variance as defect, data issue, approved difference or unresolved risk; obtain business approval for accepted differences.
5. Define thresholds, owners, retest requirements and go/no-go criteria.

**Result/evidence:** A reconciliation pack, approved difference log and signed-off cutover decision.

**SME probe:** *Must every historical value match exactly?*  
**Answer outline:** Reconciliation must account for every variance, but exact equality may not be valid if semantics differ. Unexplained or unapproved differences must not be waived.

### 19. Rule complexity makes break and tolerance behavior hard to support
**Situation:** Many exceptions and custom rounding conditions have accumulated; support cannot predict the result or explain why one case differs from another.

**Task:** Improve transparency and maintainability without accidentally changing policy.

**Action:**
1. Inventory each rule's purpose, policy basis, input, output, owner and dependencies.
2. Convert logic into a decision table with explicit precedence, boundaries and exception paths.
3. Identify redundant or conflicting conditions and confirm any simplification with the policy owner.
4. Create isolated tests for each rule plus interaction tests for the highest-risk combinations.
5. Document diagnostics and support instructions; defer risky refactoring if release stability or regression capacity is inadequate.

**Result/evidence:** A reviewed rule map, targeted regression pack and prioritized simplification plan.

**SME probe:** *Would you simplify the logic immediately before a payroll-critical period?*  
**Answer outline:** Not without sufficient test capacity, approval and rollback options. Stabilize first when necessary, then execute a controlled simplification.

### 20. Defend the final design to a skeptical SME
**Situation:** An SME challenges whether the design handles missed breaks, grace boundaries, rounding ties, schedule variation, corrections and audit requirements.

**Task:** Explain the rationale and demonstrate that the design is policy-aligned, testable and appropriately controlled.

**Action:**
1. State the authoritative policy, population, assumptions and decisions still owned by the business.
2. Walk through a standard case, a boundary case and a disputed/missing-data case from source evidence to outcome.
3. Explain alternatives, trade-offs, supported product behavior and release/tenant constraints.
4. Present test evidence, reconciliation, access controls, known limitations and residual risks.
5. Separate personal contribution from team outcomes and cite authentic artifacts rather than invented metrics.

**Result/evidence:** A clear design rationale, traceable decisions, signed-off test evidence and documented residual risks.

**SME probe:** *What evidence would make you revise the design?*  
**Answer outline:** An authoritative policy change, reproducible test failure, release-specific limitation, material employee/compliance risk or a better-supported option. Explain how the change would be assessed and governed.

## Boundary and interaction test matrix

| Dimension | Minimum cases |
|---|---|
| Grace/tolerance | Just before; exactly at; just after the boundary |
| Rounding | Below midpoint; exact midpoint/tie; above midpoint; negative/invalid input where relevant |
| Breaks | Planned and taken; missed; partial; multiple; corrected record |
| Shift pattern | Short; long; split; overnight; schedule change |
| Eligibility | Eligible; ineligible; employee changes group or schedule |
| Time boundaries | Shift start/end; day/week boundary; time-zone or daylight-saving transition if in scope |
| Rule interactions | Break plus grace; rounding plus threshold; correction plus prior evaluation |
| Data quality | Missing; duplicate; late; unapproved; inconsistent timestamps |
| Audit | Authorized edit; unauthorized edit attempt; missing reason; approval and history retrieval |
| Downstream | Initial result; correction/reprocessing; mapping; reconciliation and duplicate-delivery handling |

For each test, record the source input, policy reference, expected outcome and rationale, actual outcome, evidence, defect reference and approver. Do not fill expected outcomes from assumptions.

## SME follow-up bank
- Is the break planned, recorded, automatically deducted or otherwise policy-defined?
- What is the authoritative policy source, and who approves its interpretation?
- What does “grace” mean in this design: tolerance, classification, exception suppression or time alteration?
- What is the exact rounding unit, direction and tie-breaking rule?
- At what processing stage is rounding applied?
- Which schedule and employee attributes control eligibility?
- What happens when a break is missed, partial or disputed?
- How are source evidence and later corrections preserved?
- How do you prove the rule is fair and does not create systematic bias?
- What happens at the day, week, time-zone or effective-date boundary?
- Which product behavior was verified for the target release and tenant?
- How do you reconcile downstream results after a correction?
- Which alternative did you reject and why?
- What was your personal contribution, and what evidence supports it?
- What residual risk did you communicate and who accepted it?

## Rapid-fire revision
1. Distinguish a planned break from evidence that a break occurred.
2. Explain rounding versus a grace/tolerance window.
3. Give one test immediately below, at and above a boundary.
4. Name the authoritative owner for break policy.
5. Explain how to handle missing or disputed evidence.
6. State why source data should be checked before changing rules.
7. Explain one audit control for manual corrections.
8. Name one schedule or employee-group variation to test.
9. Explain how a correction can affect downstream results.
10. Identify one product-specific claim requiring release verification.

## Scoring rubric (0–2 per dimension)
1. **Policy clarity:** identifies authoritative policy, population and decision owner.
2. **Technical precision:** distinguishes breaks, rounding, grace and exceptions.
3. **Edge-case reasoning:** tests boundaries, schedule variation, missing data and corrections.
4. **Controls and validation:** includes audit, reconciliation and regression evidence.
5. **Communication and integrity:** explains trade-offs clearly and uses only authentic evidence.

**Target:** 8/10 or better, with no critical issue involving unsupported policy assumptions, inaccurate product claims, auditability or candidate integrity.

## Anti-patterns to avoid
- Assuming scheduled breaks were actually taken.
- Treating a grace period as automatic permission to alter recorded time.
- Assuming a rounding convention is lawful or supported everywhere.
- Using configuration changes to hide missing or contradictory source events.
- Ignoring exact boundary and tie-breaking semantics.
- Applying one schedule's assumptions to every employee group.
- Allowing manual exceptions without reasons, approval and traceability.
- Treating a lower exception count as proof of better outcomes without validating the metric.
- Claiming a hypothetical case as personal project experience.
- Making product claims without checking the relevant release, tenant and documentation.

## Reusable practice worksheet
- **Problem and affected population:**
- **Authoritative policy / decision owner:**
- **My responsibility:**
- **Break / rounding / grace concept involved:**
- **Source evidence and schedule inputs:**
- **Boundary and interaction cases:**
- **Options and trade-offs:**
- **Exception, approval and audit controls:**
- **How I validated the outcome:**
- **Verified result and evidence:**
- **SME challenge and answer:**
- **Residual risk / lesson learned:**

## Success criteria
A strong answer explains the policy before the configuration, distinguishes source evidence from calculated behavior, handles exact boundaries and exceptions, and proves that records remain explainable and auditable. The candidate should be able to demonstrate why the chosen approach is appropriate without presenting assumptions as policy or hypothetical work as personal experience.

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for its business-first discovery philosophy and workforce-time domain boundaries. It is repository context, not a substitute for release-specific SAP documentation, tenant testing, authorized policy interpretation or the candidate's authentic project evidence.
