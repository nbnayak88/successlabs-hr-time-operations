# Interview Stream 06 — Time-Off & Absence Management

## Outcome
Demonstrate how to translate approved absence policy into a reliable time-off process, covering employee eligibility, requests, balances, approvals, cancellations, effective dates and cross-process dependencies.

## Scope boundary
This stream focuses on absence requests, balances, eligibility, approvals and policy behavior. Keep distinct **absence policy**, **absence type/category**, **employee eligibility**, **request workflow**, **time account/balance**, **planned schedule**, **recorded time**, **evaluated time** and **downstream payroll results**. These concepts can interact, but their exact relationships must be verified for the relevant product release and tenant configuration.

**Primary focus:** absence types, requests, balances, eligibility, accrual dependencies, approvals, cancellations, cross-process interactions.

## STAR response standard
- **Situation:** Describe the real business context, affected population, policy issue, constraints and impact.
- **Task:** State your personal accountability and decision authority.
- **Action:** Explain policy discovery, process design, configuration dependencies, exception handling, controls and validation.
- **Result:** Use evidence such as an approved absence-policy matrix, reconciled balances, passed scenario tests, UAT approval, resolved defects or a documented control. Do not invent metrics.
- **SME probe:** Be ready to justify policy interpretation, boundary behavior, alternatives and evidence.
- **Integrity rule:** These are practice scenarios, not claims about your personal history. Label unexperienced scenarios as lab/design exercises.

## Core absence-design checklist
1. Who is eligible for each absence policy, and who owns that decision?
2. What are the request rules, required data, duration rules and allowed increments?
3. How are planned working time, non-working days, holidays and partial-day requests treated?
4. What approval, delegation, escalation and correction processes apply?
5. Is a balance involved? If so, what are the approved accrual, usage, carryover, expiry and adjustment rules?
6. How are cancellations, amendments, retroactive requests and overlapping absences handled?
7. What are the effective-date, country, employee-group and collective-agreement variations?
8. Which downstream time, payroll, reporting or integration processes depend on the outcome?
9. How are privacy, auditability and employee/manager visibility controlled?
10. What positive, negative, boundary, regression and end-to-end evidence is required?

## 20 structured STAR practice scenarios

### 1. An absence request is rejected unexpectedly
**Situation:** Employees report that a request they believe is valid is rejected or cannot be submitted.

**Task:** Determine whether the cause is policy interpretation, eligibility, request data, balance, workflow, schedule dependency or configuration.

**Action:**
1. Capture the exact employee population, absence dates, request duration and expected policy outcome.
2. Confirm the approved policy and eligibility rules with the accountable owner.
3. Trace the request through relevant prerequisites and configured rules; compare with a known-good case.
4. Check effective dates, available balance if applicable, non-working days and workflow conditions.
5. Reproduce the case, correct the evidenced root cause and test both valid and invalid requests.

**Result:** A defect record, approved rule interpretation and regression evidence demonstrate the outcome.

**SME probe:** Why not simply approve the request manually?  
**Answer outline:** Manual approval may be a legitimate controlled exception, but it does not prove the rule is correct. Diagnose the cause and preserve authorization and audit evidence.

### 2. A global absence template conflicts with local policy
**Situation:** A global design covers common leave processes but local laws, agreements or company policies introduce different eligibility, entitlement or request rules.

**Task:** Keep common process elements standardized while preserving approved local policy differences.

**Action:** Establish the global principles; obtain authoritative local policy inputs; map eligibility, entitlement, duration, documentation and approval differences; distinguish legal/policy variation from preference; document owners and effective dates; verify supported configuration and test each approved variation.

**Result:** A signed-off global/local policy matrix and test coverage provide evidence of controlled variation.

**SME probe:** Who decides whether a local rule is legally required?  
**Answer outline:** The authorized policy/legal owner determines the rule. The architect translates it into a testable design and flags ambiguity rather than independently interpreting law.

### 3. Absence duration does not match planned working time
**Situation:** A request spanning several dates consumes a duration that differs from the employee's expectation, especially for part-time or non-standard schedules.

**Task:** Establish the correct duration under the approved policy and relevant schedule.

**Action:** Confirm the employee's assigned work pattern and the absence policy's duration definition; test working days, non-working days, holidays and partial days; verify the product's calculation behavior; reconcile expected and actual duration; document exceptions and obtain owner sign-off.

**Result:** A schedule-aware test matrix and signed-off expected results demonstrate the intended behavior.

**SME probe:** Should every calendar day in a multi-day absence count equally?  
**Answer outline:** Do not assume so. Treatment depends on policy, schedule and configured behavior; validate the exact population and dates.

### 4. A balance is insufficient for a requested absence
**Situation:** An employee requests a balance-based absence but the available balance is lower than the requested amount.

**Task:** Apply the approved policy without bypassing controls or making unsupported balance changes.

**Action:** Confirm the applicable balance rule, request duration, balance as-of date and eligibility; investigate pending requests, timing or source-data issues; identify whether negative balances or exceptions are permitted; agree any exception with the authorized owner; test permitted and prohibited outcomes and reconcile the balance.

**Result:** A documented decision and reconciled balance evidence show the request was handled according to policy.

**SME probe:** Should you manually increase the balance to allow the request?  
**Answer outline:** Not without a verified cause and authorized adjustment process. Establish whether the balance is wrong or the request is not permitted.

### 5. Accrual or entitlement behavior is disputed
**Situation:** Stakeholders disagree about how an entitlement is earned, made available, carried forward or adjusted.

**Task:** Translate the approved policy into an explicit lifecycle and testable rules.

**Action:** Create examples for hire dates, eligibility changes, periodic accrual, usage, carryover and expiry where relevant; obtain policy-owner decisions; distinguish policy from product options; verify the supported account model and timing; build boundary and reconciliation tests; record unresolved decisions.

**Result:** An approved lifecycle definition and test evidence establish the intended entitlement behavior.

**SME probe:** What if the policy is ambiguous about a mid-period eligibility change?  
**Answer outline:** Document the competing interpretations and example outcomes, escalate to the accountable policy owner and do not encode an assumption as approved policy.

### 6. A request crosses a policy or calendar boundary
**Situation:** An absence spans a year-end, policy effective date, holiday period or another boundary where rules may change.

**Task:** Determine which rules apply to each part of the request and how the system should handle the transition.

**Action:** Identify the relevant policy and calendar boundaries; clarify whether the request should be split or treated as one request under the configured model; verify effective-dated behavior; test dates immediately before, on and after the boundary; check balances and downstream dependencies; obtain sign-off.

**Result:** Boundary-test evidence and an approved interpretation demonstrate correct handling.

**SME probe:** Does a request submitted before a policy change always use the old policy?  
**Answer outline:** Not necessarily. Submission date, absence date and policy effective date may be different decision points. Confirm the approved rule and verify product behavior.

### 7. Part-day and hourly absence requests behave inconsistently
**Situation:** Employees can request a full day but encounter confusion or unexpected results when requesting part of a day or a specific number of hours.

**Task:** Define the permitted granularity and ensure duration is interpreted consistently.

**Action:** Confirm policy-approved units and increments; identify the relationship to planned working time and breaks; test start/end times, minimum increments and non-working periods; verify supported product behavior; document user instructions and exception paths.

**Result:** A set of approved examples and successful tests demonstrates how part-day requests should behave.

**SME probe:** Should an hourly request be accepted outside planned working hours?  
**Answer outline:** The policy and supported configuration determine the answer. Clarify the business rule and test it rather than assuming all time windows are valid.

### 8. Overlapping requests create inconsistent outcomes
**Situation:** An employee submits overlapping absence requests or a new request overlaps with an already approved request.

**Task:** Define conflict handling, user feedback and any allowed exceptions.

**Action:** Confirm policy on overlap and priority; identify whether partial overlap, different absence categories or concurrent processes are possible; verify product validation; test exact duplicates, partial overlaps and boundary-touching requests; document the correction and approval path.

**Result:** A conflict matrix and test evidence demonstrate predictable handling.

**SME probe:** Should every overlap be blocked?  
**Answer outline:** Not automatically. Some overlaps may be invalid, while others may represent distinct policy-approved cases. The policy owner must define the rule.

### 9. Cancellation or amendment does not restore the expected state
**Situation:** An employee cancels or amends an approved absence, but the displayed balance or related process does not reflect the expected result.

**Task:** Trace the request lifecycle and define a controlled correction path.

**Action:** Preserve the original request and change history; confirm cancellation/amendment policy; inspect workflow status and any applicable processing dependencies; reproduce the scenario; verify timing and recalculation behavior; reconcile the balance and test both the corrected request and downstream result.

**Result:** A documented root cause, approved correction and before/after reconciliation demonstrate resolution.

**SME probe:** Is deleting the original request the best fix?  
**Answer outline:** Do not assume deletion is appropriate. Follow the supported amendment/cancellation process and preserve the audit trail.

### 10. Manager approval or delegation fails
**Situation:** Absence requests remain pending, route to the wrong approver or fail during a manager absence.

**Task:** Diagnose the workflow and ensure approvals follow the approved authority model.

**Action:** Confirm the approval matrix and delegation policy; inspect manager relationships, effective dates and workflow conditions; test normal approval, delegation, reassignment, escalation and rejection; verify access boundaries; document ownership and support steps.

**Result:** Workflow test evidence and an approved escalation/delegation rule demonstrate readiness.

**SME probe:** Should an administrator approve requests to clear a backlog?  
**Answer outline:** Only through an authorized exception process with traceability. Do not bypass the approved approval model to improve a queue metric.

### 11. Retroactive absence entry is requested
**Situation:** An employee or administrator needs to record an absence for a past period after time records or related results may already have been processed.

**Task:** Establish whether retroactive entry is permitted and assess its downstream impact.

**Action:** Confirm policy, approval and correction windows; identify affected dates, balances, time records and downstream consumers; verify product behavior for retroactive requests and recalculation; test in a controlled environment; obtain required approvals and reconcile before/after results.

**Result:** A documented impact assessment, approved correction path and reconciliation evidence support a controlled outcome.

**SME probe:** Should a retroactive request automatically trigger all downstream recalculations?  
**Answer outline:** Do not assume so. Identify the actual processing dependencies and supported reprocessing procedure, then confirm ownership and approval.

### 12. Eligibility changes during employment
**Situation:** A hire, transfer, leave of absence, contract change or other employment event may change eligibility for a specific absence policy.

**Task:** Ensure the right policy applies to the right person at the right time.

**Action:** Identify authoritative employee attributes and eligibility rules; confirm effective dates and source ownership; test the change before, on and after its effective date; validate balance or entitlement treatment where applicable; reconcile affected employees and document late-data exceptions.

**Result:** An eligibility matrix, effective-date tests and assignment reconciliation demonstrate the expected transition.

**SME probe:** What if the upstream employee change arrives late?  
**Answer outline:** Define the supported recovery path, reconcile affected employees and preserve audit evidence. Do not rely on manual fixes without ownership or prevention controls.

### 13. Country or employee-group absence rules are disputed
**Situation:** HR, operations and local stakeholders provide conflicting interpretations of entitlement or eligibility.

**Task:** Resolve the policy question before committing to technical behavior.

**Action:** Record each interpretation and its example outcomes; identify the authoritative owner; document the affected population and dates; clarify policy/legal questions with qualified owners; present implementable options and implications; record the final decision and derive tests.

**Result:** A signed decision log and approved scenario matrix provide a defensible outcome.

**SME probe:** What if the requested rule is technically possible but policy approval is missing?  
**Answer outline:** Technical feasibility is not policy authorization. Record the dependency and risk, and obtain approval before treating the rule as final.

### 14. Integration or payroll consumers interpret absence differently
**Situation:** A downstream consumer receives an absence code or duration but interprets it differently from the source process.

**Task:** Establish semantic alignment and end-to-end ownership without conflating absence management with detailed downstream configuration.

**Action:** Compare source and target definitions, code mappings, dates, units and status semantics; identify owners for each transformation; define handling for cancellation, correction and unmapped codes; test representative end-to-end cases; reconcile the result with the receiving process owner.

**Result:** An approved mapping specification and end-to-end test evidence demonstrate the intended meaning is preserved.

**SME probe:** Should the absence source code be changed to match the consumer?  
**Answer outline:** Not automatically. Preserve approved source semantics and use a governed mapping unless an approved architecture decision justifies changing the source model.

### 15. Employees do not understand absence balances
**Situation:** Employees question their available balance or assume a displayed balance represents a different point in the process.

**Task:** Improve transparency and explain the balance's meaning, timing and limitations.

**Action:** Verify the configured balance lifecycle and data refresh timing; define plain-language terms such as available, pending, used and adjusted only as applicable; use worked examples; identify when a balance may lag or require processing; test examples with employees and support teams.

**Result:** A validated explanation and sample cases support consistent user understanding.

**SME probe:** Is the displayed balance always the final value for a future absence date?  
**Answer outline:** Do not generalize. Explain the actual calculation date, pending requests and configured lifecycle, and verify the source and refresh behavior.

### 16. Sensitive absence information requires privacy controls
**Situation:** Absence records may contain sensitive personal details, and managers or support staff should not all see the same information.

**Task:** Align the process with least-privilege access and approved privacy requirements.

**Action:** Identify which data is necessary for each role; separate operational status from sensitive details where supported; confirm role/access capabilities; test permitted and prohibited views and actions; define audit and retention requirements with the responsible owner; validate representative user journeys.

**Result:** An approved access matrix, negative tests and evidence-retention procedure demonstrate control design.

**SME probe:** Should managers see all information associated with an absence request?  
**Answer outline:** Not by default. Access should follow business need, policy and privacy requirements, verified against the product's actual capabilities.

### 17. A new policy arrives shortly before go-live
**Situation:** A late policy change affects absence eligibility, duration or entitlement shortly before release.

**Task:** Assess scope, risk and readiness and obtain a controlled decision.

**Action:** Clarify the approved rule and effective date; identify impacted populations, requests, balances, interfaces, communications and tests; assess historical versus prospective treatment; estimate the minimum safe validation scope; obtain change approval; document residual risks and go/no-go criteria.

**Result:** An approved impact assessment, regression evidence and recorded release decision demonstrate governance.

**SME probe:** What if leadership insists on release without complete regression testing?  
**Answer outline:** State the evidence gap, likely impact and residual risk; recommend a proportionate control or deferral; record risk acceptance by the accountable owner rather than presenting untested behavior as validated.

### 18. Migration reveals unclear legacy absence codes and balances
**Situation:** Legacy records include duplicate absence codes, inconsistent entitlement balances or unclear historical policy mappings.

**Task:** Define a controlled migration and reconciliation approach.

**Action:** Profile legacy codes and balances; identify authoritative policy and data owners; map each code to a target concept or explicit exception; define treatment of open, historical and pending requests; reconcile representative and full-population totals; set acceptance thresholds and go/no-go criteria.

**Result:** A signed mapping register, balance reconciliation and approved exception disposition demonstrate readiness.

**SME probe:** What should happen to an unmapped legacy absence code?  
**Answer outline:** Do not guess. Obtain a policy/data-owner decision, document its historical and operational impact, and resolve or explicitly exclude it under an approved rule.

### 19. Repeated absence incidents are treated as isolated cases
**Situation:** Support repeatedly fixes incorrect balances, failed requests or workflow issues, but the same patterns return.

**Task:** Determine whether the root cause is policy ambiguity, data quality, configuration, access, integration or user understanding.

**Action:** Categorize incidents by population, absence type, date and failure stage; compare each case with approved policy; trace upstream and downstream dependencies; prioritize systemic causes; test the proposed correction across affected and unaffected cases; update monitoring and the support runbook.

**Result:** A root-cause analysis, permanent-fix evidence and reviewed support procedure demonstrate a sustainable approach. Quantify improvement only when measured.

**SME probe:** How do you prove a fix addressed the root cause?  
**Answer outline:** Reproduce the original case, show the causal evidence, retest relevant boundaries and regression scenarios, and monitor the same failure category after release.

### 20. Defending an absence solution in an architecture review
**Situation:** An architect or process owner challenges whether the absence design is maintainable, compliant, testable or aligned with workforce policy.

**Task:** Defend the design using approved policy, supported product behavior and end-to-end evidence.

**Action:** Present the policy matrix, eligibility rules, request lifecycle, balance assumptions, approval model, effective dates, exception handling, access controls and dependencies; compare alternatives; demonstrate normal, partial-day, boundary, cancellation and retroactive cases where relevant; disclose unresolved decisions and residual risks.

**Result:** A documented architecture decision, accountable owners, approved conditions and validation evidence demonstrate readiness.

**SME probe:** What evidence would make you redesign the solution?  
**Answer outline:** A verified policy gap, unsupported capability, incorrect balance behavior, privacy weakness, recurring failures or unmanageable local variation should trigger a controlled review.

## SME follow-up bank
- How do you distinguish absence policy from product configuration?
- Which owner approves eligibility, entitlement and country-specific rules?
- How do schedules and non-working days affect absence duration in the actual design?
- How do you test partial-day, overlapping and boundary-date requests?
- What is the approved process for cancellation, amendment and retroactive entry?
- How do you reconcile a disputed balance?
- What happens when employee eligibility changes mid-period?
- How do you preserve source semantics across integrations?
- How do you protect sensitive absence information?
- Which product claims require release-specific verification?

## Rapid-fire revision
1. Name the main inputs to an absence request.
2. Why must policy ownership be explicit?
3. Give one schedule-related boundary test.
4. How do you investigate an unexpected balance?
5. What should happen when an absence is cancelled?
6. Why is retroactive entry a cross-process risk?
7. How do you test manager delegation?
8. What is the risk of a global rule that ignores local policy?
9. How do you reconcile legacy absence balances?
10. What evidence belongs in a strong STAR answer?

## Validation checklist
- Approved policy and accountable owner are documented.
- Employee eligibility and effective dates are explicit.
- Absence types, units, durations and request rules are defined.
- Schedule, holiday and non-working-day behavior is tested.
- Balance lifecycle and exception rules are approved where applicable.
- Approval, delegation, cancellation and amendment paths are validated.
- Retroactive requests and downstream effects are assessed.
- Country/employee-group variations are governed.
- Integration mappings and downstream semantics are reconciled where relevant.
- Privacy, access, audit and support ownership are verified.
- Product-specific behavior is checked against the applicable release and tenant configuration.

## Scoring rubric (0–2 per dimension)
1. Business and policy context are clear.
2. Personal responsibility and decision rights are explicit.
3. Absence concepts and dependencies are technically distinguished.
4. Exceptions, privacy, effective dates and validation are addressed.
5. Results are evidence-backed and the SME probe demonstrates judgment.

**Target:** 8/10 or better, with no critical technical accuracy or candidate-integrity issue.

## Anti-patterns to avoid
- Treating policy decisions as technical assumptions.
- Assuming all calendar days or all employee groups are treated identically.
- Changing balances without tracing the cause and preserving approval evidence.
- Ignoring cancellations, retroactive requests and effective-date boundaries.
- Conflating absence requests, time accounts, evaluated time and payroll outputs.
- Broadening access to resolve workflow problems.
- Claiming hypothetical scenarios or unmeasured improvements as personal achievements.
- Assuming product behavior is identical across releases and tenant configurations.

## Reusable practice worksheet
- **Business problem and affected population:**
- **My responsibility and authority:**
- **Approved policy and owner:**
- **Eligibility and effective-date rules:**
- **Request/balance/approval lifecycle:**
- **Dependencies and alternatives:**
- **Exceptions and controls:**
- **Test and reconciliation evidence:**
- **Verified result:**
- **SME challenge and response:**
- **Lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for the local business-first discovery context. These are interview-practice structures, not claims that all absence rules or product behaviors are universal. Verify release-specific behavior against the relevant SAP documentation and actual tenant configuration.
