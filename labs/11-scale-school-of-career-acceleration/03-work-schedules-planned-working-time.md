# Interview Stream 03 — Work Schedules & Planned Working Time

## Outcome
Demonstrate that you can translate an approved working-time policy into a reliable, maintainable planned-time design; assign the right schedule to the right employee population; and validate how schedules interact with time recording, time valuation, absence and downstream processes.

## Scope boundary
This stream focuses on planned hours, work patterns, schedule assignment and schedule-driven behavior. It does not replace the dedicated streams for recording profiles, time types, time valuation, time off, or CICO. Refer to those streams when explaining dependencies.

**Primary focus:** work schedules, planned hours, part-time patterns, shift patterns, holiday calendars, employee eligibility and schedule changes.

## STAR answer standard
- **Situation:** Describe the actual workforce, operating model, schedule challenge, constraints and impact.
- **Task:** State what you personally owned and what was outside your authority.
- **Action:** Explain policy discovery, employee segmentation, schedule analysis, assignment logic, exception handling, design choices and validation. Separate your contribution from the team's.
- **Result:** Use evidence such as an approved schedule matrix, reconciled planned hours, test results, resolved assignment defects, UAT sign-off or support trends. Never invent metrics.
- **SME probe:** Be ready to justify the schedule design, explain a boundary case and identify its dependencies.
- **Version check:** Verify product behavior against the SAP SuccessFactors edition/release and actual tenant configuration in scope.

## 20 structured STAR practice scenarios

These are model structures for rehearsal, not claims about your personal work history. Replace the context with authentic evidence. If you have not delivered a scenario, describe it honestly as a lab, design exercise or proposed approach.

### 1. Employees receive the wrong planned hours
**Situation:** Employees report that their expected hours do not match their agreed work pattern. The issue may be caused by policy interpretation, schedule assignment, effective dating or source data.

**Task:** Determine whether the schedule definition or its assignment is wrong and establish the correct planned-time expectation.

**Action:**
1. Select representative affected employees and compare their approved working pattern, employment attributes and effective dates.
2. Confirm the business rule with the schedule/policy owner instead of assuming the employee's reported hours are authoritative.
3. Trace the assigned schedule and its planned daily/weekly hours in the relevant configuration.
4. Compare expected and system-derived planned time across normal days, non-working days and period boundaries.
5. Correct the root cause through the approved process, then test affected and unaffected populations.

**Result:** Use a validated employee-to-schedule reconciliation and approved test evidence to show the issue is resolved.

**SME probe:** How do you distinguish a wrong schedule definition from a wrong assignment?  
**Answer outline:** Compare the intended pattern, configured schedule, employee assignment/effective dates and observed result independently.

### 2. A global schedule model does not fit all countries
**Situation:** A global template is proposed for a workforce with different local workweeks, public holidays, contractual hours and shift patterns.

**Task:** Preserve global design consistency while representing approved local requirements.

**Action:** Establish global principles; collect authoritative local policy inputs; create a country/population variation matrix; identify which differences are schedule patterns versus holiday-calendar or policy differences; verify supported configuration; document owners and regression tests.

**Result:** Present an approved template and controlled variation register, not an unverified claim that one schedule fits every location.

**SME probe:** Which differences justify a separate schedule versus a separate calendar or policy?  
**Answer outline:** Use the actual semantics of the requirement and supported product model; validate the distinction with the product documentation and policy owner before deciding.

### 3. Designing schedules for part-time employees
**Situation:** Part-time employees work fewer hours than full-time peers, with some working shorter days and others working fewer days per week.

**Task:** Ensure planned hours reflect the approved contract and do not infer a pattern from a simple percentage alone.

**Action:** Segment part-time patterns; confirm days and hours by employee group; model the agreed schedule options; validate weekly totals, non-working days, holidays and changes in contracted hours; test downstream calculations that depend on planned time.

**Result:** Evidence includes an approved pattern catalogue, reconciled hours and tests for each supported pattern.

**SME probe:** Why is “80% part-time” insufficient to determine a schedule?  
**Answer outline:** The percentage does not uniquely determine which days or hours are worked; the agreed pattern and applicable policy must be specified.

### 4. Supporting rotating and overnight shift patterns
**Situation:** A 24/7 operation uses rotating shifts, including work that starts on one calendar day and ends on the next.

**Task:** Represent the approved planned-time pattern and ensure tests cover date boundaries and the correct employee group.

**Action:** Document the rotation cycle and shift hand-offs; verify how the product represents the applicable schedule pattern; check time zones, day boundaries, breaks and calendar transitions; test a full representative cycle including weekends and holidays; validate expected planned hours with operations.

**Result:** A signed-off rotation matrix and boundary-test evidence demonstrate that the design represents the agreed pattern.

**SME probe:** What risks arise when a shift crosses midnight?  
**Answer outline:** Date attribution, planned hours, holiday/weekend classification, time recording and valuation may be affected; validate each behavior in the applicable product configuration rather than assuming one universal result.

### 5. A schedule change becomes effective mid-period
**Situation:** An employee changes from one working pattern to another during a time-recording period.

**Task:** Ensure the change is applied on the approved effective date and that old and new planned time are handled as intended.

**Action:** Confirm the effective date and responsible data owner; inspect schedule assignment history; test days before, on and after the change; assess time records, absences and any downstream results that reference planned time; define correction and regression steps if historical records are affected.

**Result:** Evidence should include an approved effective-date decision and tests proving the transition behavior.

**SME probe:** Should the change rewrite historical results?  
**Answer outline:** Never assume so. Establish the intended policy, product behavior and correction/audit implications; test and obtain approval before changing historical data or recalculating dependent results.

### 6. Holiday calendars and work schedules produce unexpected expectations
**Situation:** Employees in different locations see unexpected planned working time around public holidays.

**Task:** Identify whether the cause lies in schedule patterns, calendar assignment, employee population or a policy interpretation.

**Action:** Confirm the authoritative holiday calendar and covered population; compare assigned calendar and schedule; test ordinary weekdays, local holidays and substitute/observed days where relevant; validate how the configured process combines these elements; document any local exceptions.

**Result:** A calendar-to-population mapping and test evidence show the intended behavior for representative dates.

**SME probe:** Is a public holiday automatically a non-working day for every employee?  
**Answer outline:** No universal assumption should be made; treatment depends on the applicable policy, employee group and supported configuration.

### 7. Two employee populations appear to need the same schedule
**Situation:** A design team proposes reusing one schedule for different populations to reduce configuration count, but their contractual rules may differ.

**Task:** Decide whether reuse is appropriate without hiding semantic differences.

**Action:** Compare actual working days, daily hours, planned weekly totals, calendar dependencies and exception behavior; document shared and distinct requirements; assess maintenance and testing implications; use representative employee scenarios to validate equivalence before reusing the design.

**Result:** An evidence-backed reuse decision and a documented exception list support maintainability.

**SME probe:** Is fewer configuration objects always better architecture?  
**Answer outline:** No. Reuse is valuable only when semantics are genuinely equivalent and future changes can be governed without unintended cross-population effects.

### 8. A schedule assignment is missing or invalid
**Situation:** A subset of employees has no valid planned-time expectation, and downstream time processing or reporting behaves unexpectedly.

**Task:** Establish scope, fix the assignment cause and prevent recurrence.

**Action:** Identify affected employees and dates; verify required employee attributes and assignment rules; distinguish missing source data from configuration or effective-date problems; correct data through the approved process; validate representative records and introduce a monitoring/reconciliation control.

**Result:** Evidence includes an affected-population list, completed reconciliation and a control owner for future checks.

**SME probe:** Would you assign a default schedule to every employee to clear the issue?  
**Answer outline:** Only if a valid, approved default exists for that population. A blanket default can conceal data defects and create incorrect planned time.

### 9. Planned hours differ from employee expectations
**Situation:** The employee contract states one number of hours, while the schedule-derived expectation appears different.

**Task:** Resolve the discrepancy without assuming the contract, roster or system is automatically authoritative.

**Action:** Gather the approved contract/work pattern, schedule definition and observed output; confirm whether breaks are included or excluded in the relevant business definition; reconcile daily and weekly totals; get policy-owner confirmation; update the source or schedule and retest.

**Result:** A signed-off reconciliation defines exactly what “planned hours” means for the population.

**SME probe:** Why can daily hours and contractual weekly hours appear inconsistent?  
**Answer outline:** The work pattern may distribute hours unevenly, and the definition may treat breaks or non-working days differently; verify the contract and configuration semantics.

### 10. A shift rotation change must be introduced safely
**Situation:** Operations plans to change a rotation cycle while employees are already assigned to the current pattern.

**Task:** Plan the transition with correct effective dates, employee communication and regression coverage.

**Action:** Obtain the approved rotation and transition date; map impacted populations and schedule assignments; assess overlap, rest periods and policy constraints with the authorized owner; test the old-to-new transition, boundary days and downstream dependencies; agree rollout, communication and rollback criteria.

**Result:** A transition plan, approval record and successful representative tests show readiness.

**SME probe:** What if the rotation change is announced after time records have already been entered?  
**Answer outline:** Assess whether existing records or evaluated results are affected, preserve auditability, and follow the approved correction/reprocessing path; do not silently rewrite historical data.

### 11. Flexible working arrangements challenge fixed planned-time assumptions
**Situation:** Employees have flexible start and end times, but the business still needs reliable planned-time expectations and clear exception handling.

**Task:** Define what is fixed, what is flexible and how the system should interpret deviations.

**Action:** Clarify core hours, total duration, recording obligations, permitted flexibility and approval rules; separate policy from assumptions; verify which supported configuration concepts can represent the model; test early/late starts, breaks and incomplete records; document what remains a manager decision.

**Result:** An approved flexible-work policy matrix and test cases demonstrate that the design reflects actual policy.

**SME probe:** Does flexible work mean there is no planned time?  
**Answer outline:** Not necessarily. The business may still define core hours, expected duration or other constraints; the exact model must be agreed and verified.

### 12. Schedule changes affect time off or absence behavior
**Situation:** A schedule change or different employee work pattern appears to affect how an absence period is interpreted.

**Task:** Ensure the design correctly coordinates planned time and absence rules without conflating the two domains.

**Action:** Trace the employee's schedule, absence dates, relevant policy and expected treatment of non-working days; confirm the authoritative absence policy; verify supported interactions in the relevant product release; test full-day and partial-day cases across differing patterns; obtain process-owner sign-off.

**Result:** A cross-process test set and signed-off expected results demonstrate the dependency has been addressed.

**SME probe:** Should an absence always consume the same amount of time for every employee?  
**Answer outline:** Do not assume this. The result depends on the approved absence policy, schedule and product behavior; validate the actual case.

### 13. The business wants schedule patterns created through an uncontrolled spreadsheet
**Situation:** Local administrators maintain informal schedule spreadsheets, leading to inconsistent naming, duplicate patterns and unclear ownership.

**Task:** Establish a governed schedule catalogue and controlled change process.

**Action:** Inventory existing patterns; identify duplicates and obsolete entries; define naming, ownership, effective dating, approval and documentation standards; validate each pattern against approved working-time policy; migrate or rationalize only after impact assessment; introduce periodic review.

**Result:** A controlled catalogue, ownership model and reconciliation evidence improve supportability without claiming unmeasured savings.

**SME probe:** How would you decide whether two apparently similar schedules can be consolidated?  
**Answer outline:** Compare their complete semantics, dependencies, populations, effective-date history and future policy roadmap; consolidate only with owner approval and regression evidence.

### 14. Time zones and locations complicate schedule interpretation
**Situation:** A distributed workforce works across locations or time zones, and stakeholders disagree on which local date or schedule should govern a time event.

**Task:** Make the relevant location, time-zone and date interpretation explicit in the design.

**Action:** Identify the employee's assigned work location and applicable schedule; clarify whether the business rule uses local site time or another defined reference; check daylight-saving transitions where applicable; verify product handling and integration timestamps; test representative cross-time-zone and transition cases.

**Result:** A documented time-zone decision and test evidence support predictable interpretation.

**SME probe:** Can you infer the governing schedule from the device timestamp alone?  
**Answer outline:** Not safely. The employee assignment, event semantics, location policy and product/integration behavior must be confirmed.

### 15. Schedule design must account for weekends and non-working days
**Situation:** The same number of hours is distributed differently across five-day, six-day and rotating workweeks.

**Task:** Represent each approved pattern and ensure non-working days are handled consistently.

**Action:** Confirm the defined workweek and rest days for each population; model patterns with the right daily distribution; validate planned totals and holiday interaction; test events and absences on working and non-working days; document exceptions and the policy owner.

**Result:** A workweek matrix and boundary tests provide evidence of correct planned-time behavior.

**SME probe:** Is Saturday always a non-working day?  
**Answer outline:** No. It depends on the approved work pattern, location and employee population.

### 16. An acquired workforce brings legacy schedules
**Situation:** An organization acquires a workforce with many legacy schedule codes, incomplete documentation and inconsistent naming.

**Task:** Rationalize the legacy model without losing meaningful distinctions or corrupting historical interpretation.

**Action:** Inventory source patterns and employee assignments; profile usage and data quality; map each legacy code to an approved target or documented exception; confirm historical and effective-date needs; test migrated assignments and planned-hour totals; obtain business sign-off on unmapped or retired patterns.

**Result:** A reconciled mapping register, exception disposition and approved migration decision demonstrate readiness.

**SME probe:** Should unused legacy schedules be deleted immediately?  
**Answer outline:** First verify historical references, audit/reporting needs, dependencies and retention requirements; decommission through governance rather than deleting blindly.

### 17. Schedule-driven results fail a boundary test
**Situation:** A test near midnight, a week boundary or a schedule transition produces a result different from the expected planned hours.

**Task:** Isolate the cause and prove the correction without causing regressions.

**Action:** Preserve the test data and expected result; verify schedule definition, assignment, effective dates, calendar and relevant time-recording/valuation dependencies; reproduce the boundary case; correct the evidenced cause; run related positive, negative and regression tests.

**Result:** A defect record with root cause, corrected test evidence and regression coverage demonstrates resolution.

**SME probe:** What is your first step when a schedule-related test fails?  
**Answer outline:** Confirm the expected business rule and exact inputs, then trace the assigned schedule and dependencies; do not immediately change configuration.

### 18. Schedule data quality must be monitored after go-live
**Situation:** New hires, transfers and working-pattern changes create recurring risk that employees will retain outdated or invalid schedule assignments.

**Task:** Define an operational control that detects mismatches early.

**Action:** Identify authoritative employee attributes and schedule ownership; define valid assignment rules and change triggers; create a reconciliation between eligible employees and assigned schedules; define exception thresholds, owner, frequency and resolution SLA; test the control using known valid and invalid records.

**Result:** A repeatable control with documented ownership and evidence of exception resolution supports stable operations.

**SME probe:** What should the control report?  
**Answer outline:** Missing assignments, invalid combinations, stale assignments after effective-dated changes, unexpected duplicates and exceptions requiring policy-owner review.

### 19. A schedule design must support audit and compliance review
**Situation:** An auditor asks why an employee had a particular planned-time pattern on a historical date and who approved a change.

**Task:** Ensure the design and operating process preserve the evidence needed to explain the historical state.

**Action:** Confirm retention and audit requirements with the appropriate owner; document schedule ownership, approval, effective date and assignment history; test historical reporting or evidence retrieval using supported capability; restrict unauthorized changes; define how corrections and emergency changes are recorded.

**Result:** A traceable change record and repeatable evidence-retrieval procedure support audit readiness.

**SME probe:** Why is the current schedule not sufficient evidence for a historical question?  
**Answer outline:** The current assignment may differ from the historical state; the investigation needs the effective date, relevant history and approved change evidence.

### 20. Defending a schedule design in an architecture review
**Situation:** A reviewer challenges whether the proposed schedule model is too complex, fails to cover exceptions or will be difficult to maintain.

**Task:** Defend the model with policy evidence, explicit trade-offs and a testable operating plan.

**Action:** Present the employee-population matrix, schedule catalogue, assignment logic, holiday/calendar dependencies and effective-date approach; compare alternatives; walk through normal, non-working-day, cross-midnight and mid-period-change cases as relevant; show source/version checks and test evidence; disclose residual risks and operational ownership.

**Result:** A documented architecture decision, accepted conditions and a complete validation plan are the credible outcomes. Do not portray unresolved risks as closed.

**SME probe:** What evidence would make you redesign the schedule model?  
**Answer outline:** A verified policy gap, unsupported product behavior, failed boundary tests, uncontrolled complexity, recurring assignment errors or a changed workforce model should trigger a documented reassessment.

## SME follow-up bank
- How did you prove that an employee was assigned the correct schedule on the relevant date?
- How do planned working time and recorded time differ?
- How do you handle a schedule change that becomes effective mid-period?
- What is the distinction between a work schedule and a holiday calendar in the design you implemented?
- Which tests cover overnight shifts, non-working days and schedule transitions?
- How do you distinguish an assignment defect from an incorrect schedule definition?
- What evidence supports local or collective-agreement variations?
- How do you preserve historical traceability after a schedule change?
- What happens to related absence or time results when the schedule changes?
- What would you do if product documentation and observed tenant behavior differ?

## Rapid-fire revision
1. Why is an employee schedule assignment as important as the schedule definition?
2. Why is a part-time percentage insufficient to define a work pattern?
3. What is a boundary test for an overnight shift?
4. Why must effective dates be tested?
5. How can a holiday calendar affect planned-time expectations?
6. What is the risk of applying a blanket default schedule?
7. How do you govern local schedule exceptions?
8. What should be reconciled during schedule migration?
9. What evidence helps explain a historical schedule?
10. How do you test a schedule change without missing regressions?

## Design and testing checklist
Before sign-off, confirm:
- The approved work pattern and its policy owner are documented.
- Employee populations and assignment rules are explicit.
- Daily/weekly planned-hour expectations are reconciled.
- Calendar, holiday, location and time-zone assumptions are verified.
- Effective-date changes and historical implications are understood.
- Normal, non-working-day, cross-midnight and exception scenarios are tested where relevant.
- Dependencies with time recording, time off and valuation are validated.
- Schedule catalogue, access, auditability and operational ownership are defined.
- Product behavior is verified for the applicable release and configuration.

## Scoring rubric (0–2 per dimension)
1. Business context and population are clear.
2. Personal responsibility is explicit.
3. Schedule concepts and product claims are accurate and qualified.
4. Effective dates, exceptions, dependencies and tests are addressed.
5. Result is evidenced and the SME probe demonstrates judgment.

**Target:** 8/10 or better, with no critical technical accuracy or candidate-integrity issue.

## Anti-patterns to avoid
- Assuming every employee in a country shares the same schedule.
- Inferring a work pattern from a part-time percentage alone.
- Treating a public holiday as automatically non-working for every population.
- Changing schedule configuration before confirming the approved policy and expected result.
- Ignoring effective dating, historical state, overnight shifts or downstream dependencies.
- Inventing metrics or claiming a lab scenario as a real implementation.
- Confusing planned working time with actual recorded or evaluated time.

## Reusable practice worksheet
- **Workforce and schedule problem:**
- **My role and decision authority:**
- **Approved pattern/policy:**
- **Employee population and assignment logic:**
- **Options considered:**
- **Effective dates and exceptions:**
- **Dependencies and risks:**
- **How I tested the design:**
- **Verified result/evidence:**
- **SME challenge and answer:**
- **Lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) as the local reference for business-first discovery and the existing Time Management learning context. This module adds interview-practice structures; it does not assert that every described scenario is supported identically in every SAP SuccessFactors release. Verify product-specific behavior against applicable SAP documentation, best-practice workbooks and the actual tenant configuration.
