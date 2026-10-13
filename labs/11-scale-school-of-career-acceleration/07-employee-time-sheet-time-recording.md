# Interview Stream 07 — Employee Timesheet & Time Recording

## Outcome
Demonstrate how to design and troubleshoot the employee time-recording journey from entering time through validation, saving, submission, review and correction, while protecting data quality, usability and downstream processing.

## Scope boundary
This stream focuses on the employee recording experience, recording period, entry validation, save/submit behavior, corrections, manager review and usability.

Keep distinct **entered/recorded time**, **submitted time**, **approved time**, **evaluated time** and **downstream payroll or reporting outputs**. These are separate process states or outcomes whose exact behavior must be verified for the relevant product edition/release and tenant configuration.

## STAR response standard
- **Situation:** Describe the workforce, user journey, issue, constraints and business impact.
- **Task:** State your personal responsibility and decision authority.
- **Action:** Explain requirement discovery, recording design, validation, exception paths, workflow dependencies, usability and test strategy.
- **Result:** Use authentic evidence such as approved user journeys, successful UAT, reconciled test entries, defect resolution or support evidence. Never invent metrics.
- **SME probe:** Be ready to explain the trade-off, a boundary case, the control and how you proved the outcome.
- **Integrity rule:** These are practice scenarios, not claims about your personal history. Label unexperienced cases as lab/design exercises.

## Core recording-journey checklist
1. Who is eligible to record time, and what is the relevant recording period?
2. Which entry units and permitted time categories are required?
3. What validation occurs during entry, save, submission and review?
4. What is the expected handling of incomplete, duplicate, overlapping or out-of-range entries?
5. How do schedules, time types, recording profiles and absence processes affect the journey?
6. Who can edit, submit, approve, reject or correct a record?
7. How are corrections and audit history preserved?
8. What does the user see when processing is pending, unsuccessful or incomplete?
9. What happens at period boundaries, for overnight work or after a policy change?
10. What evidence demonstrates the full journey and its downstream dependencies are correct?

## 20 structured STAR practice scenarios

### 1. Employees repeatedly enter incorrect time
**Situation:** A workforce reports repeated errors when entering time, leading to corrections, support tickets or delayed completion of the recording period.

**Task:** Determine whether the problem comes from policy ambiguity, user experience, eligibility, entry validation, schedule assumptions or training.

**Action:**
1. Observe representative users completing the actual journey.
2. Categorize errors by population, time category, period, entry step and root cause.
3. Compare expected behavior with approved policy and configured validation.
4. Separate usability improvements from rule/configuration changes; assess effects on integrations and downstream processing.
5. Test the revised journey with normal, invalid and boundary entries.

**Result:** Use validated user journeys, defect evidence and UAT results to demonstrate improvement.

**SME probe:** How do you avoid solving a policy defect with training alone?  
**Answer outline:** Compare actual system behavior with approved requirements and observe where users fail. If the interface or validation contradicts policy, fix the design as well as communicating it.

### 2. Recording periods do not match employee expectations
**Situation:** Employees are unsure which dates belong to a timesheet or attempt to enter time outside the expected period.

**Task:** Define the correct period behavior and make it understandable to users.

**Action:** Confirm the business-defined recording cadence and period boundaries; verify the configured period and eligibility; test first/last day, period rollover, late entries and corrections; document the treatment of open or closed periods; validate user messages and support instructions.

**Result:** An approved period matrix and boundary-test evidence establish predictable behavior.

**SME probe:** What should happen when an employee tries to enter time into a closed period?  
**Answer outline:** The response must follow the approved correction and authorization policy. Verify supported product behavior and communicate the allowed exception route.

### 3. Time entries fail validation unexpectedly
**Situation:** An employee enters what appears to be a valid record, but validation blocks saving or submission.

**Task:** Identify the exact failing rule and its intended purpose.

**Action:** Capture the input, employee population, date, time category and error; reproduce the case; check required fields, allowed values, eligibility, schedule and relevant policy; compare with a known-good case; correct the evidenced issue and test both valid and invalid inputs.

**Result:** A reproducible defect record and regression evidence show the rule now behaves as approved.

**SME probe:** Would you remove the validation to unblock employees?  
**Answer outline:** Not before confirming its business/control purpose. Correct the rule or source data where appropriate; any temporary exception must be authorized, scoped and auditable.

### 4. A global timesheet experience does not fit every population
**Situation:** A standard entry journey works for most employees but not for shift workers, part-time employees or another distinct population.

**Task:** Identify the genuine requirement and avoid unnecessary customization.

**Action:** Compare population needs, entry units, schedules, categories and review processes; identify what can remain common and what needs an approved variation; verify supported product options; document design rationale and regression impact; test each population with representative cases.

**Result:** A signed-off population-to-journey matrix and test results provide evidence of controlled variation.

**SME probe:** When should the user experience vary by population?  
**Answer outline:** Only when a verified policy or work-context difference requires it and the supported design can represent it maintainably.

### 5. Save and submit behavior is misunderstood
**Situation:** Users believe that saving a timesheet means it has been submitted or accepted for the next process stage.

**Task:** Clarify state transitions and make the user journey transparent.

**Action:** Map each state and action in the actual process; confirm when validation occurs and what submission triggers; identify whether edits remain possible after submission; verify workflow and processing dependencies; test each transition, failure message and correction path; update guidance.

**Result:** A validated state-transition diagram and test evidence show what users can expect at each step.

**SME probe:** Is a submitted timesheet necessarily approved or evaluated?  
**Answer outline:** Do not treat these states as equivalent. Verify the actual workflow and processing model and explain each state separately.

### 6. Duplicate or overlapping entries appear
**Situation:** Users create duplicate entries or overlapping intervals, sometimes after retrying a failed save or correcting a record.

**Task:** Define the correct validation and recovery behavior.

**Action:** Confirm the policy on duplicates and overlaps; reproduce retry and correction scenarios; check the system's supported validation behavior; test exact duplicates, partial overlaps and legitimate adjacent intervals; define safe recovery and support instructions.

**Result:** An approved conflict matrix and negative/positive tests demonstrate consistent handling.

**SME probe:** Should every overlapping interval be blocked?  
**Answer outline:** Not necessarily. The rule depends on the approved recording model; distinguish invalid overlap from valid adjacent or policy-permitted records.

### 7. Overnight work is entered against the wrong date
**Situation:** Employees work across midnight and enter start/end times or durations that are interpreted differently from the expected work period.

**Task:** Clarify date attribution and validate the complete recording path.

**Action:** Confirm the approved overnight-shift policy and schedule; identify how entry date, start/end times and time zone are interpreted; test a shift crossing midnight, a week boundary and a holiday boundary where relevant; verify any downstream evaluation dependency; document expected results.

**Result:** Boundary-test evidence and an approved interpretation demonstrate reliable entry behavior.

**SME probe:** Can you infer the business date from a timestamp alone?  
**Answer outline:** Not safely. Use the approved shift/date attribution rule, employee assignment and configured behavior; validate the exact scenario.

### 8. A correction is needed after submission
**Situation:** An employee discovers an error after submitting a timesheet, and the team is unsure whether to edit, recall, reject or create a correction.

**Task:** Establish the supported correction lifecycle and preserve auditability.

**Action:** Confirm process ownership and permitted states; determine who may initiate the correction; verify the product's correction/recall/rejection behavior; assess approval and downstream processing impact; test the correction and audit trail; update the runbook.

**Result:** A documented correction decision and end-to-end test evidence demonstrate controlled recovery.

**SME probe:** Why not edit the record directly in the database or remove the original?  
**Answer outline:** That can bypass application controls and destroy traceability. Use supported correction paths with authorization and evidence.

### 9. Manager review creates a bottleneck
**Situation:** Submitted time records remain pending because the review queue, routing or manager responsibilities are unclear.

**Task:** Diagnose the workflow without bypassing required controls.

**Action:** Confirm the approval policy and decision rights; inspect routing, manager relationships and effective dates; categorize pending items by root cause; test approval, rejection, delegation and escalation; agree queue monitoring and ownership; validate the full process.

**Result:** Workflow evidence, an approved escalation model and a support procedure demonstrate readiness.

**SME probe:** Should all pending records be auto-approved after a fixed delay?  
**Answer outline:** Only if policy explicitly authorizes it and controls are designed and tested. A backlog alone is not sufficient justification to remove a review control.

### 10. A user changes employee group or eligibility mid-period
**Situation:** A transfer or employment change affects recording eligibility while the current period is open.

**Task:** Determine which rules apply before and after the effective date and how existing entries should be treated.

**Action:** Confirm the authoritative employee data and effective date; trace profile/eligibility assignment; test entries on either side of the boundary; assess pending/submitted records and related workflow; define approved correction/reassignment behavior; reconcile affected cases.

**Result:** Effective-date test evidence and an approved transition decision demonstrate predictable handling.

**SME probe:** Should the whole period be governed by the employee's current assignment?  
**Answer outline:** Do not assume so. The rule may depend on the relevant date and product model; obtain the approved policy and verify the actual behavior.

### 11. Timesheet data is inconsistent with a related process
**Situation:** A downstream consumer or time-evaluation process sees a result different from what a user entered.

**Task:** Trace the lifecycle without confusing the entered value with later processed outcomes.

**Action:** Preserve the original entry and state; compare the user-entered value, submitted record, relevant processing status and target result; verify mappings, transformations, period and effective dates; assign ownership across the chain; test normal, corrected and exception cases.

**Result:** A source-to-target reconciliation and end-to-end retest demonstrate where the discrepancy arose.

**SME probe:** Which value is the source of truth?  
**Answer outline:** It depends on the business question and lifecycle stage. Identify the authoritative record for that stage, document lineage and reconcile the downstream result.

### 12. A user cannot record a required time category
**Situation:** A user can open the timesheet but cannot select a required category or submit the entry.

**Task:** Distinguish eligibility, category availability, authorization and validation issues.

**Action:** Reproduce the journey with the affected and a known-good user; check employee eligibility, recording profile, available categories, required attributes and access; verify the product behavior; correct the evidenced cause; test both allowed and denied cases.

**Result:** Root-cause evidence and regression tests demonstrate the correct option availability.

**SME probe:** Should all time categories be made visible to everyone?  
**Answer outline:** No. Category availability should reflect approved policy and eligibility; broad visibility can create invalid entries or confusing choices.

### 13. Mobile or remote users struggle with time entry
**Situation:** Employees recording time away from a desktop face usability or connectivity issues, increasing incomplete or duplicated entries.

**Task:** Improve the supported user journey while preserving accurate records and controls.

**Action:** Observe the actual device and process; confirm supported capabilities and access requirements; test interrupted sessions, retries, validation messages and duplicate prevention; define safe recovery and support guidance; ensure the proposed experience respects privacy and policy.

**Result:** A device-specific test set and user feedback provide evidence that the supported journey meets the requirement.

**SME probe:** What is the risk of blindly retrying after a timeout?  
**Answer outline:** The first request may have succeeded even if the user saw no confirmation. Check record state and supported idempotent/recovery behavior before repeating the action.

### 14. The organization changes a recording policy near release
**Situation:** A late change alters required fields, allowed categories, period rules or submission requirements.

**Task:** Assess impact and protect release readiness.

**Action:** Obtain the approved policy and effective date; identify affected populations, forms, validation, integrations, workflows and training; define test scope and data impact; obtain change approval; update regression and cutover plans; record unresolved risks.

**Result:** An impact assessment, approved decision and test evidence demonstrate controlled change management.

**SME probe:** What if leadership wants to release without testing all affected populations?  
**Answer outline:** State the evidence gap and risk, propose a proportionate mitigation or deferral, and record accountable risk acceptance. Do not claim untested behavior is validated.

### 15. Repeated incidents have no clear root cause
**Situation:** Support repeatedly resolves incomplete or incorrect timesheets, but the same incidents return.

**Task:** Determine whether the issue is data, policy, user experience, validation, assignment or workflow.

**Action:** Classify cases by error, population, date, recording category and journey stage; reproduce common patterns; compare with approved requirements; identify systemic causes; test the permanent fix and regression cases; update support diagnostics and monitoring.

**Result:** A root-cause record, tested correction and updated runbook demonstrate a sustainable response; quantify improvement only if measured.

**SME probe:** How do you prove the issue is resolved permanently?  
**Answer outline:** Reproduce the original defect, test the fix against relevant edge cases, monitor the same failure category and confirm that the preventive control is operating.

### 16. Access and audit requirements affect timesheet corrections
**Situation:** Different roles should have different permissions to create, submit, approve or correct records.

**Task:** Align role access and process controls with least privilege and audit requirements.

**Action:** Map role-to-action permissions; confirm segregation-of-duties rules; distinguish process eligibility from authorization; verify supported access controls; test allowed and denied actions; inspect audit evidence for corrections and approvals.

**Result:** An approved access matrix, negative-test results and sample audit trail demonstrate control effectiveness.

**SME probe:** Can a manager correct every employee record in their team?  
**Answer outline:** Not by assumption. The allowed action must follow policy, role authorization and the supported product model.

### 17. A timesheet is incomplete at period close
**Situation:** Some employees have missing entries or incomplete submissions as a recording period closes.

**Task:** Define a controlled close process that identifies exceptions without fabricating records or bypassing approval.

**Action:** Agree completeness criteria and cut-off; identify missing, saved-but-unsubmitted and rejected records; assign employee/manager follow-up; define authorized exception handling; test period-close reporting and recovery; communicate downstream implications and owners.

**Result:** A documented close checklist, exception register and reconciliation evidence support a controlled period close.

**SME probe:** Should missing hours be filled with planned hours automatically?  
**Answer outline:** Only if an approved policy and supported process explicitly allow it. Planned time is not automatically proof of actual time worked.

### 18. Migration brings inconsistent legacy timesheet records
**Situation:** Legacy data contains missing categories, inconsistent dates or uncertain statuses.

**Task:** Define the target mapping, preserve meaningful history and establish migration acceptance criteria.

**Action:** Profile legacy entries and statuses; identify authoritative mappings and unresolved values; define treatment of open, submitted, approved and corrected records; reconcile sample and full-population totals; test boundary dates and target user journeys; obtain business sign-off on exceptions.

**Result:** A signed mapping register, reconciliation report and approved exception disposition demonstrate readiness.

**SME probe:** What should happen to a record whose status cannot be mapped confidently?  
**Answer outline:** Do not guess. Escalate to the data/process owner, document the operational and audit impact, and obtain a controlled mapping or explicit exclusion.

### 19. The user experience hides why a record is blocked
**Situation:** Error messages say only that an entry is invalid, leaving users unable to determine what must be corrected.

**Task:** Improve actionable feedback without exposing sensitive information or weakening controls.

**Action:** Map validation rules to user-understandable messages; distinguish missing data, invalid category, period restriction and authorization problems; verify that messages reveal no restricted information; test usability with representative users; ensure support can trace the underlying error.

**Result:** A validated message catalogue, user testing and support evidence demonstrate clearer recovery paths.

**SME probe:** Should error messages expose the complete technical rule or backend details?  
**Answer outline:** No. Provide enough information to correct the issue while respecting security and usability; keep diagnostic detail in authorized support channels.

### 20. Defending the recording journey in an architecture review
**Situation:** An architect challenges whether the proposed timesheet design is accurate, maintainable, accessible and operationally controlled.

**Task:** Defend the design with business requirements, supported behavior and end-to-end evidence.

**Action:** Present the user journey and state transitions; explain eligibility, period rules, validations, corrections, approvals and exceptions; show dependencies with schedules, time categories and downstream processing; demonstrate normal, negative, boundary and recovery tests; disclose version constraints and unresolved risks.

**Result:** A documented architecture decision, approved process ownership and test evidence demonstrate readiness.

**SME probe:** What evidence would make you redesign the journey?  
**Answer outline:** Recurring data errors, ambiguous states, unsupported requirements, poor recovery behavior, weak access controls or unmanageable support effort should trigger a controlled review.

## SME follow-up bank
- How do you distinguish entered, saved, submitted, approved and evaluated time?
- What defines the recording period and how are boundaries tested?
- How do you investigate a validation failure?
- How do you handle duplicate or overlapping entries?
- What is the supported correction path after submission?
- How do schedules, eligibility and time categories affect entry?
- What is the risk of retrying after a timeout?
- How do you prove period-close completeness?
- How do you preserve auditability for corrections and approvals?
- Which product behaviors require release-specific verification?

## Rapid-fire revision
1. What is the difference between saving and submitting?
2. Name three timesheet validation cases.
3. Give one overnight or period-boundary test.
4. How do you investigate a blocked category?
5. Why is planned time not proof of actual time worked?
6. How should post-submission corrections be controlled?
7. What do you check after a timeout?
8. How do you distinguish a user issue from a policy/configuration issue?
9. What should a period-close exception report show?
10. What evidence supports a strong STAR answer?

## Validation checklist
- Recording policy and population are defined.
- Period boundaries and eligibility are verified.
- Required fields, permitted categories and validation rules are documented.
- Save, submit, review, reject and correction states are understood.
- Schedule, time type, absence and downstream dependencies are assessed where relevant.
- Duplicate, overlap, timeout and incomplete-entry scenarios are tested.
- Access, privacy and audit requirements are validated.
- Period-close controls and support ownership are documented.
- Migration mappings and reconciliation criteria are approved where relevant.
- Product-specific behavior is verified against the applicable release and tenant configuration.

## Scoring rubric (0–2 per dimension)
1. Business problem and user journey are clear.
2. Personal accountability is explicit.
3. Process states and technical concepts are distinguished accurately.
4. Exceptions, controls and validation are addressed.
5. Result is evidence-backed and the SME probe demonstrates judgment.

**Target:** 8/10 or better, with no critical technical accuracy or candidate-integrity issue.

## Anti-patterns to avoid
- Treating entered, submitted, approved and evaluated time as interchangeable.
- Assuming planned hours equal actual hours worked.
- Removing validation without understanding its business purpose.
- Retrying a failed submission without checking whether it succeeded.
- Editing or deleting records outside supported correction paths.
- Ignoring period boundaries, overnight work, effective dates or population differences.
- Claiming hypothetical outcomes or unmeasured improvements as personal achievements.
- Assuming product behavior is identical across releases and tenant configurations.

## Reusable practice worksheet
- **Business problem and affected population:**
- **My responsibility and decision authority:**
- **Approved recording rule:**
- **User journey and state transitions:**
- **Validation and exception cases:**
- **Dependencies and alternatives:**
- **Access/audit controls:**
- **Test and reconciliation evidence:**
- **Verified result:**
- **SME challenge and response:**
- **Lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for the local business-first discovery context. These scenarios are interview-practice structures, not claims that all timesheet behaviors are universal. Verify product-specific behavior against relevant SAP documentation and the actual tenant configuration.
