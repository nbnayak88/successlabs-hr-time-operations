# Interview Stream 11 — Time Approval, Workflow & Corrections

## Outcome
Demonstrate practical design and delivery judgment for time review, manager approval, delegation, correction, rejection, escalation and auditability in SAP SuccessFactors Workforce Time & Operations.

## Scope and control principles
**Primary focus:** approval criteria, workflow routing, delegation, correction paths, rejected entries, accountability, escalation, segregation of duties and audit trail.

Keep the answer centered on workforce time management. Explain downstream payroll dependencies when they affect timing, recalculation or reconciliation, without drifting into detailed payroll configuration. Product behavior must be verified for the target edition/release, enabled capabilities and actual tenant configuration.

A reliable control model distinguishes:
- **Submission:** an employee or authorized source presents time data for review.
- **Validation:** required data and business rules are checked; validation is not the same as approval.
- **Approval:** an authorized role confirms the record or result under the approved policy.
- **Correction/rejection:** a record is returned or changed through a governed path with reason and evidence.
- **Re-evaluation and downstream disposition:** the changed record is checked again and any dependent result or consumer is addressed.
- **Audit:** the organization can reconstruct who did what, when, why and under which authority, to the extent supported by the product and retention policy.

These are conceptual distinctions, not a claim that every product release uses the same status model or workflow objects.

## STAR response standard
- **Situation:** State the real business context, population, workflow issue, constraints and impact.
- **Task:** Explain what you personally owned and what was outside your remit.
- **Action:** Explain discovery, decision rights, routing, controls, exceptions, dependencies, options and validation. Separate your actions from the team's.
- **Result:** Use only verified evidence such as approved workflow design, passed routing tests, reconciliation, closed defects, documented control gaps or user feedback. Do not invent metrics.
- **SME probe:** Defend authority, segregation of duties, exception paths, re-submission behavior and audit evidence.
- **Practice integrity:** The scenarios below are interview exercises, not claims about your personal history. Use authentic project evidence or label the answer as a lab/design exercise.

## 20 detailed scenario-based STAR interview practices

### 1. Time approvals are delayed and managers complain
**Situation:** Time records remain pending near a processing deadline. Managers report unclear queues, employees cannot see what needs action, and operations cannot tell whether delays are caused by routing, missing data or workload.

**Task:** Establish the approval service requirement and isolate the main bottleneck without weakening required controls.

**Action:**
1. Map the end-to-end process from submission through validation, manager review, rejection/correction and final disposition.
2. Define the approval SLA, business calendar, eligible approvers, escalation owner and treatment of incomplete submissions.
3. Analyze pending items by status, age, organizational unit and reason; distinguish routing failures from approver inactivity.
4. Test representative cases, including a missing approver, an employee/manager change and a rejected entry.
5. Agree operational monitoring, escalation and employee/manager guidance; validate the actual workflow capabilities in the target release.

**Result/evidence:** An approved workflow map, pending-item definitions, routing tests and an ownership/escalation model.

**SME probe:** *Would you auto-approve every item that exceeds the SLA?*  
**Answer outline:** Not without an explicit, authorized policy and risk assessment. Escalation and visibility are safer defaults than silently bypassing a required approval control.

### 2. Manager hierarchy changes leave items with the wrong approver
**Situation:** An employee changes manager or organizational assignment while time entries are pending, and the item is routed to a former manager or becomes orphaned.

**Task:** Define how approver determination and in-flight items should behave when organizational data changes.

**Action:**
1. Establish the authoritative manager/organizational source, effective dates and synchronization timing.
2. Clarify whether routing is determined at submission, at approval time or by another supported rule.
3. Test a manager change before submission, while pending and after rejection/re-submission.
4. Define reassignment, delegation or escalation handling for orphaned work and preserve the prior decision history.
5. Confirm data ownership and regression-test the relevant employee lifecycle events.

**Result/evidence:** A documented routing rule, effective-date tests and a governed orphaned-work procedure.

**SME probe:** *Should pending requests always move to the new manager?*  
**Answer outline:** That is a business/control decision, not a universal assumption. Determine the approved authority model and test the supported behavior for in-flight items.

### 3. A proposed shortcut weakens segregation of duties
**Situation:** A manager requests permission to edit an employee's time record and approve that same change to reduce turnaround time.

**Task:** Assess the control risk and recommend a workable alternative.

**Action:**
1. Map roles for entry, correction, review, approval and administration.
2. Identify whether policy or audit controls require separate actors for any action.
3. Assess options such as employee resubmission, a separate approver, controlled exception role or documented emergency procedure.
4. Validate permissions and workflow behavior with negative tests, not only successful-path tests.
5. Document the approved role model, exception authority and periodic access review.

**Result/evidence:** A role/approval matrix and test evidence showing prohibited combinations are blocked or controlled.

**SME probe:** *Is segregation of duties always a strict two-person rule?*  
**Answer outline:** Not universally; requirements depend on policy and risk. Identify incompatible duties, authorized compensating controls and approval authority rather than imposing an unexamined pattern.

### 4. Approval criteria are vague or inconsistent
**Situation:** Different managers approve similar records using different standards, while employees receive little explanation for rejection.

**Task:** Make the criteria consistent, transparent and testable.

**Action:**
1. Interview policy owners and approvers to distinguish mandatory checks from personal preferences.
2. Define required evidence, validation outcomes, rejection reasons and escalation triggers.
3. Translate criteria into a decision table and role-specific guidance.
4. Test typical, incomplete, conflicting and policy-exception cases with representative approvers.
5. Obtain sign-off and establish a controlled process for future criterion changes.

**Result/evidence:** An approved criteria matrix, reason-code guidance and consistent test outcomes.

**SME probe:** *Should every rejection reason become an automated validation?*  
**Answer outline:** No. Deterministic data-quality checks may be automated, while judgment-based or disputed cases may need human review. Keep the distinction explicit.

### 5. Rejection causes the employee to lose context or repeat work
**Situation:** A manager rejects a time entry but the employee cannot see what must change, and resubmission creates confusion about which version is current.

**Task:** Design a clear correction and re-submission loop with traceability.

**Action:**
1. Define mandatory rejection reason, employee-visible explanation and any confidential internal notes.
2. Establish whether the rejected record is edited, replaced or resubmitted under the supported product model.
3. Test version history, status transitions, notifications and repeated rejection.
4. Confirm that approval applies to the current submitted version and that downstream processes do not consume a stale version.
5. Provide examples and operational guidance for both employees and managers.

**Result/evidence:** A correction-loop diagram, status-transition tests and clear ownership for unresolved rejections.

**SME probe:** *How do you prove the approved version is the version consumed downstream?*  
**Answer outline:** Trace record identity/version and status through the process, compare outbound data with the approved state and test that a later correction invalidates or supersedes prior output as designed.

### 6. A production-like workflow behaves unexpectedly
**Situation:** An approval routes to the wrong person, skips a required step or remains stuck even though the expected conditions appear satisfied.

**Task:** Find the first point of divergence rather than changing routing rules by guesswork.

**Action:**
1. Preserve the affected case, timestamps, employee/manager assignments, status and configuration context.
2. Reproduce with the same effective-dated data and identify the expected transition.
3. Trace the actual route and distinguish source-data issues, rule conditions, permissions, notification delivery and workflow-engine behavior.
4. Check the applicable release documentation and tenant setup before assuming a platform defect.
5. Make a controlled correction, run positive and negative routing tests, and document the root cause.

**Result/evidence:** A reproducible case, root-cause record and verified routing/permission tests.

**SME probe:** *What is the first thing you inspect: notifications or routing?*  
**Answer outline:** Establish whether the workflow transition and assigned approver are correct. Notification delivery may be a separate issue; inspect each layer independently.

### 7. Policy and operations disagree about emergency approval
**Situation:** Operations asks for a faster path during an urgent period, while policy owners insist on standard review and documented accountability.

**Task:** Facilitate a proportionate decision without inventing an exception authority.

**Action:**
1. Clarify the emergency, impacted population, deadline and consequence of delay.
2. Identify who is authorized to approve an exception and what policy constraints cannot be waived.
3. Present options: escalation, authorized delegate, controlled temporary process or documented deferral.
4. Define evidence, expiry, reconciliation and post-event review for any approved exception.
5. Record the decision, owner and residual risk; validate the operational steps before use.

**Result/evidence:** An approved contingency procedure and documented decision rights.

**SME probe:** *What if an executive asks you to bypass the workflow immediately?*  
**Answer outline:** Explain the control and operational risk, identify the authorized decision-maker, offer compliant alternatives and document the instruction and risk acceptance. Do not silently bypass controls.

### 8. A manual correction is being made without adequate evidence
**Situation:** Support or a manager edits a time record to resolve a complaint, but the reason, original value or approval is not captured consistently.

**Task:** Establish a correction path that is both operationally usable and auditable.

**Action:**
1. Define what constitutes a correction, who may request it, what evidence is required and who can approve it.
2. Preserve original values and the history of the change where supported; do not overwrite evidence without a governed mechanism.
3. Separate simple data-entry errors from policy exceptions or disputed time.
4. Test missing reason, unauthorized edit, rejected correction and correction after approval.
5. Provide a runbook and review samples to detect repeated or unusual correction patterns.

**Result/evidence:** A correction control checklist, role matrix and traceable test cases.

**SME probe:** *Can an administrator fix the record directly?*  
**Answer outline:** Only within approved authority and supported controls. Define the emergency or admin path, require rationale and evidence, and verify audit history and downstream reprocessing.

### 9. Different employee populations need different approval routes
**Situation:** Hourly, salaried, contingent, union or country-specific populations have different approvers, evidence needs or exception handling.

**Task:** Support required variation while maintaining a coherent global governance model.

**Action:**
1. Identify the authoritative population attributes and the policy basis for each route.
2. Compare a common workflow with controlled variants and define the criteria for assignment.
3. Check organizational changes, cross-entity transfers, delegation and fallback approvers.
4. Test each route plus negative cases where an employee must not enter another population's workflow.
5. Assign owners for local policy, global design and regression testing.

**Result/evidence:** A workflow variation matrix, owner register and route coverage report.

**SME probe:** *How do you prevent routing logic from becoming unmaintainable?*  
**Answer outline:** Use explicit criteria, minimize exceptions, document ownership and review usage. Add a variant only when an approved requirement warrants it.

### 10. Delegation or absence coverage creates approval risk
**Situation:** An approver is unavailable, and pending time records risk missing a deadline or being approved by someone without the required authority.

**Task:** Design controlled delegation and fallback behavior.

**Action:**
1. Define eligible delegates, scope, effective dates, duration and who authorizes the delegation.
2. Clarify whether delegation covers review, approval, correction or only specific actions.
3. Test start/end of delegation, overlapping delegations, unavailable delegate and expired assignment.
4. Verify access to the relevant employee population and whether the delegate can perform prohibited actions.
5. Monitor delegated actions and ensure the audit trail identifies the actual actor and delegated authority where supported.

**Result/evidence:** A delegation matrix, negative permission tests and a documented fallback process.

**SME probe:** *Should a delegate inherit every permission of the primary approver?*  
**Answer outline:** No assumption should be made. Grant the minimum required authority for a defined period and scope, subject to the product's supported controls and organizational policy.

### 11. Country or collective-agreement rules affect approval
**Situation:** A local policy requires a specific review or correction process, but the global workflow does not clearly reflect the requirement.

**Task:** Obtain an authoritative interpretation and implement controlled, testable variation.

**Action:**
1. Ask the designated policy/legal/employee-relations owner to clarify the requirement, coverage and effective date.
2. Translate the requirement into roles, approval criteria, deadlines, exception paths and evidence.
3. Identify affected populations and dependencies such as schedules, time types and downstream cutoffs.
4. Test before/after effective dates and employees whose assignments change.
5. Document governance, approval of the design and future policy-change ownership.

**Result/evidence:** A signed-off requirement trace, local variation record and passing workflow tests.

**SME probe:** *Can the architect decide what an ambiguous agreement means?*  
**Answer outline:** The architect should expose ambiguity and model options, but the authorized policy owner must resolve interpretation. Record the decision and its source.

### 12. Downstream processing receives a record before approval
**Situation:** A downstream interface or report includes a time record that was still pending, subsequently rejected or later corrected.

**Task:** Establish the status contract and prevent unapproved or stale data from being treated as final.

**Action:**
1. Define the status and authorization required for a record to be eligible for downstream consumption.
2. Map submission, approval, rejection, correction and re-approval states to the interface contract.
3. Test a pending record, approved record, rejected record, post-approval correction and retry/replay.
4. Compare source state, outbound payload and downstream result; assign ownership at the first divergence.
5. Define reconciliation and recovery steps for records already consumed before a status change.

**Result/evidence:** An agreed status contract, end-to-end tests and a reconciliation procedure.

**SME probe:** *Can an approved record later require a correction?*  
**Answer outline:** Yes, depending on policy and process. The design must govern the changed state, preserve history and determine what downstream reprocessing or correction is required.

### 13. The business wants a dashboard for approval performance
**Situation:** Leadership asks for an approval SLA report, but stakeholders disagree about when the clock starts, what counts as completion and whether rejected/resubmitted items reset the clock.

**Task:** Define a metric that is meaningful, reproducible and resistant to misleading interpretation.

**Action:**
1. Define the unit counted, start/end events, business calendar, pauses, denominator and exclusions.
2. Decide how delegation, reassignment, rejection and resubmission affect elapsed time.
3. Separate total elapsed time from time waiting on an approver versus waiting on an employee or system.
4. Reconcile the metric to a manually reviewed sample and document data-quality limitations.
5. Assign an owner and pair SLA results with quality/control indicators rather than rewarding speed alone.

**Result/evidence:** A metric definition, sample reconciliation and named business owner.

**SME probe:** *Why not measure only average approval time?*  
**Answer outline:** Averages can hide aged items and differences in complexity. Include a distribution or ageing view and distinguish wait states, while ensuring the metric does not incentivize bypassing required review.

### 14. A late workflow change threatens release readiness
**Situation:** A new approval step, delegate rule or correction requirement is requested just before UAT sign-off or cutover.

**Task:** Assess impact and support a risk-based decision with explicit evidence and ownership.

**Action:**
1. Confirm the policy basis, effective date, impacted populations and urgency.
2. Trace impacts across workflow conditions, roles, notifications, corrections, reporting, integrations and training.
3. Define minimum positive, negative, permission, delegation and regression tests.
4. Present options such as a validated change, a deferred release or an authorized interim process.
5. Record the decision, residual risk, rollback/contingency and communication plan.

**Result/evidence:** An approved change decision and updated test/sign-off record.

**SME probe:** *What if leadership accepts an untested approval change?*  
**Answer outline:** Explain the untested paths and possible control failure, document the risk and decision authority, and recommend mitigation. Do not label the workflow as validated without evidence.

### 15. Approval failures recur after incidents are closed
**Situation:** Tickets repeatedly report stuck items, missing notifications, wrong approvers or correction loops that never complete.

**Task:** Identify the systemic cause and establish preventive controls.

**Action:**
1. Categorize incidents by workflow state, routing attribute, role, source data, release and time of occurrence.
2. Reproduce one case and locate the first failing transition.
3. Separate notification issues from assignment, permission, configuration, data synchronization and user-process issues.
4. Add a targeted validation, monitoring alert, runbook or regression test.
5. Track recurrence and verify closure using actual evidence rather than ticket status alone.

**Result/evidence:** Root-cause analysis, a preventive control and a reviewable recurrence measure.

**SME probe:** *How do you know the incident is permanently fixed?*  
**Answer outline:** Reproduce the prior failure, prove the targeted control/test catches it, test adjacent routes and monitor recurrence after release.

### 16. Audit finds a user can approve their own correction
**Situation:** A control review discovers that one role may create or modify a time record and approve the same change without an explicit exception.

**Task:** Assess exposure, contain risk and remediate the role/workflow design.

**Action:**
1. Reproduce the access path and identify affected roles, populations, period and records.
2. Review the role design and applicable segregation-of-duties policy with control owners.
3. Apply an approved containment measure, such as permission adjustment or independent review, after impact assessment.
4. Review historical transactions for potential unauthorized changes and preserve evidence.
5. Test both allowed and prohibited paths and establish periodic access review.

**Result/evidence:** A documented finding, approved remediation, affected-record review and retest evidence.

**SME probe:** *Is fixing the permission enough?*  
**Answer outline:** No. Assess historical exposure, determine whether transactions require review or correction, preserve evidence and validate the control end-to-end.

### 17. The customer challenges a rejected time entry
**Situation:** An employee disputes a rejection, believes the record was complete and cannot understand the manager's decision.

**Task:** Resolve the case fairly while preserving policy, evidence and the employee's correction route.

**Action:**
1. Compare the submitted record, required criteria, schedule/source evidence and rejection reason.
2. Determine whether the rejection was policy-based, caused by missing data or was an incorrect decision.
3. Explain the issue in plain language and identify the exact evidence or action needed.
4. If disputed, use the authorized escalation or second-review route; preserve both the original and subsequent decisions.
5. Identify whether unclear criteria or training caused similar cases.

**Result/evidence:** A traceable resolution, clear employee guidance and any required policy/process improvement.

**SME probe:** *What if the manager refuses to reconsider?*  
**Answer outline:** Follow the approved escalation and dispute process, present the evidence neutrally and preserve accountability. Do not bypass the workflow or decide policy outside your authority.

### 18. Migration introduces pending or rejected records with ambiguous state
**Situation:** Historical records are migrated while some are pending, rejected or corrected, and the target design has a different workflow or status model.

**Task:** Define a controlled mapping that preserves meaning and prevents accidental approval or loss of audit context.

**Action:**
1. Inventory source statuses, original/subsequent values, timestamps, actors, reasons and approval history available.
2. Map each legacy state to an approved target disposition; flag states that have no equivalent.
3. Decide with the business owner whether records should be migrated as pending, held for review, closed historically or treated through another governed path.
4. Reconcile record counts and samples by status and population; test that migration does not trigger unintended notifications or downstream processing.
5. Define exception ownership, cutover criteria and treatment of records updated during the migration window.

**Result/evidence:** A status-mapping specification, exception log and signed-off reconciliation.

**SME probe:** *Can every legacy approval state be mapped automatically?*  
**Answer outline:** Only where semantics are understood and the target supports the intended state. Ambiguous or non-equivalent states need explicit business disposition, not a guessed mapping.

### 19. Workflow design has too many branches and special cases
**Situation:** The workflow contains many nested conditions, manual overrides and inconsistent route rules, making support and change impact analysis difficult.

**Task:** Simplify the design while preserving approved policy and control requirements.

**Action:**
1. Inventory each branch, policy basis, owner, population and exception.
2. Build a decision table with explicit conditions, outcomes, fallbacks and prohibited combinations.
3. Identify duplicate or contradictory branches and review proposed consolidation with policy and control owners.
4. Create test coverage for every decision and high-risk interaction, including permission negatives.
5. Document the support diagnostic path and schedule simplification only when regression capacity and release controls permit.

**Result/evidence:** A reviewed workflow map, reduced ambiguity and a regression suite tied to the decision table.

**SME probe:** *Would you remove a branch because it is rarely used?*  
**Answer outline:** Not solely on frequency. Establish whether it represents a legal, contractual or control requirement, then assess evidence and obtain approval before removal.

### 20. Defend the approval and correction architecture to an SME
**Situation:** A senior SME challenges the workflow's authority model, correction semantics, delegation, segregation of duties and downstream handling.

**Task:** Explain the design choices, alternatives, evidence and residual risks.

**Action:**
1. State the business policy, role model, status lifecycle and decision owners.
2. Walk through a normal submission, a rejection/resubmission, a delegated approval and a post-approval correction.
3. Explain how permissions, audit history and downstream status controls behave in the actual release/tenant.
4. Present tests, traceability, known limitations and unresolved risks; distinguish documented capability from assumptions.
5. Separate personal contribution from team outcomes and use authentic evidence only.

**Result/evidence:** A defensible architecture decision, signed-off test evidence and an explicit residual-risk record.

**SME probe:** *What evidence would cause you to change the design?*  
**Answer outline:** An authoritative policy change, reproducible permission/routing failure, release limitation, material audit risk or a better-supported alternative. Explain how you would reassess and govern the change.

## Workflow state and control test matrix

| Dimension | Minimum cases |
|---|---|
| Lifecycle | Draft/submitted; pending; approved; rejected; corrected; resubmitted |
| Routing | Correct manager; manager change; missing manager; fallback/escalation |
| Delegation | Active; expired; overlapping; delegate lacks permission |
| Segregation | Authorized submitter/approver; prohibited self-approval; admin exception |
| Correction | Before approval; after approval; rejected correction; repeated correction |
| Data integrity | Missing required data; duplicate submission; stale version; late update |
| Downstream | Pending excluded as required; approved consumed; corrected record reconciled |
| Audit | Actor; timestamp; reason; approval history; unauthorized attempt |
| Migration | Each source status; non-equivalent status; pending during cutover |
| Operational measures | SLA start/stop; aged items; resubmission; escalated and unresolved cases |

For every test, record the expected state transition, authorized actor, evidence, actual result, defect reference and approver. Base expected behavior on signed-off policy and verified product behavior.

## SME follow-up bank
- Who owns the approval policy and decision rights?
- What exact event makes a record eligible for approval?
- What happens to in-flight items after a manager or assignment change?
- How are rejection reason and correction history retained?
- Can the same user submit, correct and approve the same record?
- What does delegation authorize, for whom and for how long?
- How are missing approvers and expired delegations handled?
- What prevents pending or stale records from reaching downstream consumers?
- How are post-approval corrections re-evaluated and reconciled?
- Which status transitions and audit fields were tested?
- How were source and target statuses reconciled during migration?
- How do you distinguish a notification issue from a routing failure?
- What metric definition prevents an SLA report from hiding aged work?
- What product behavior was verified for the actual release and tenant?
- What was your personal contribution and what evidence supports it?

## Rapid-fire revision
1. Distinguish validation from approval.
2. Name one control that prevents unauthorized self-approval.
3. Explain how a manager change can affect in-flight items.
4. State the minimum information needed for a correction.
5. Explain the risk of an expired delegate.
6. Name one negative permission test.
7. Explain how rejected entries should return to the employee.
8. State how a downstream consumer should treat pending records under the approved contract.
9. Explain why migration status mapping needs business sign-off.
10. Name one authentic artifact that supports a STAR answer.

## Scoring rubric (0–2 per dimension)
1. **Business process:** explains status lifecycle, policy and accountable roles.
2. **Technical reasoning:** explains routing, delegation, correction and downstream dependencies.
3. **Control design:** addresses segregation, permissions, exception handling and auditability.
4. **Validation:** includes positive/negative paths, state transitions and reconciliation.
5. **Evidence and communication:** uses clear trade-offs, authentic evidence and release-aware claims.

**Target:** 8/10 or better, with no critical issue involving unauthorized approval, untraceable correction, unsupported product claims or candidate integrity.

## Anti-patterns to avoid
- Treating validation and approval as interchangeable.
- Auto-approving solely because an SLA elapsed without authorized policy.
- Allowing ungoverned self-approval or unrestricted delegation.
- Editing records without a reason, evidence or appropriate authority.
- Assuming a manager change will automatically reroute every in-flight item.
- Treating a notification failure as proof that the workflow failed.
- Allowing pending or stale records to be consumed as final without a defined contract.
- Mapping ambiguous legacy statuses by guesswork.
- Optimizing approval speed while ignoring accuracy and controls.
- Presenting hypothetical scenarios as personal project achievements.

## Reusable practice worksheet
- **Problem and affected population:**
- **Authoritative policy / decision owner:**
- **My responsibility:**
- **Status lifecycle and routing:**
- **Roles and segregation-of-duties constraints:**
- **Correction/rejection path:**
- **Delegation and escalation behavior:**
- **Downstream dependencies:**
- **Positive/negative tests and audit evidence:**
- **Verified result and artifact:**
- **SME challenge and answer:**
- **Residual risk / lesson learned:**

## Success criteria
A strong answer explains who may act, under what conditions, what happens after rejection or correction, how delegated and exceptional cases are controlled, and how the organization proves the right version was approved and consumed. The candidate should show clear personal accountability and evidence without inventing outcomes.

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for its business-first discovery philosophy and workforce-time boundaries. It is repository context, not a substitute for release-specific SAP documentation, tenant testing, authorized policy interpretation or the candidate's authentic project evidence.
