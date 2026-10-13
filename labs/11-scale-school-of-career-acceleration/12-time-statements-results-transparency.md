# Interview Stream 12 — Time Statements, Results & Employee Transparency

## Outcome
Demonstrate practical design judgment for making workforce time records and evaluated results understandable, reviewable, correctable and appropriately visible to employees, managers and support teams.

## Scope and operating model
**Primary focus:** time statements, recorded versus evaluated time, result explanation, disputes, employee transparency, manager review, corrected results and role-appropriate visibility.

Keep the discussion centered on workforce time management. Explain downstream payroll dependencies where relevant, without drifting into detailed payroll configuration. Verify product behavior for the actual SAP SuccessFactors edition/release, enabled capabilities and tenant configuration.

Use these concepts carefully:
- **Recorded time:** what was entered, captured or corrected as source evidence.
- **Evaluated result:** the result produced after applicable rules and dependencies are processed.
- **Statement/view:** a presentation of selected information to a user; it may not expose every internal processing detail.
- **Correction/dispute:** a governed path to challenge or amend a record or result.
- **Downstream outcome:** a dependent consumer's interpretation or use of an approved result.

These are conceptual distinctions. Confirm the actual product terminology, available statement capabilities and processing model for the target release and implementation.

## STAR response standard
- **Situation:** Describe the user population, transparency issue, business impact and constraints.
- **Task:** State your personal responsibility and boundaries.
- **Action:** Explain discovery, information design, role-based visibility, dispute/correction path, dependencies, test approach and stakeholder decisions.
- **Result:** Use only verified evidence, such as signed-off statement requirements, passing reconciliation tests, closed defects, improved comprehension feedback or approved controls. Do not invent metrics.
- **SME probe:** Defend the meaning of displayed fields, the source of truth, correction handling and access controls.
- **Practice integrity:** The scenarios are interview exercises, not claims about your personal history. Use authentic project evidence or label examples as lab/design exercises.

## 20 detailed scenario-based STAR interview practices

### 1. Employees repeatedly question their displayed time results
**Situation:** Employees see a time statement or summary but cannot understand why the displayed total differs from their own calculation. Support receives repeated questions, and managers give inconsistent explanations.

**Task:** Determine what the view must communicate and whether the issue is data, evaluation, presentation or policy.

**Action:**
1. Collect representative examples and ask users what they believe each displayed field means.
2. Trace the case from source records and schedule through the evaluated result to the displayed summary.
3. Distinguish a calculation discrepancy from a display, labeling or timing issue.
4. Define plain-language labels, period boundaries, units and a route to view relevant details or raise a dispute, subject to product capabilities.
5. Test examples with employees and managers and obtain business sign-off.

**Result/evidence:** An approved information requirement, reconciled examples and user feedback or test evidence.

**SME probe:** *Would you simply add more fields to the statement?*  
**Answer outline:** Not necessarily. More data can increase confusion or expose information unnecessarily. Identify the questions users need answered, show relevant context and provide a drill-down or support route where appropriate.

### 2. Recorded time and evaluated time are being confused
**Situation:** A manager believes an evaluated category proves what an employee originally entered, while the employee disputes a result after a correction or rule evaluation.

**Task:** Make the distinction explicit and preserve the ability to trace a result back to source evidence.

**Action:**
1. Define each term with the actual product's data model and terminology.
2. Select an example with a source entry, a relevant rule and an evaluated result.
3. Show what changed during processing and what remains the original evidence, without implying unsupported technical details.
4. Identify where authorized users can inspect corrections, approvals or history.
5. Test the explanation for a normal case and a corrected case.

**Result/evidence:** A glossary, traceable examples and validated guidance.

**SME probe:** *Can the evaluated result replace the original record?*  
**Answer outline:** Do not assume that. Establish how the product retains source evidence and history, then explain the relationship between the source record and its calculated result.

### 3. A global statement design fails a particular employee population
**Situation:** A common time statement works for the main population but omits context needed by a country, schedule type or employee group.

**Task:** Support necessary variation without creating an ungoverned set of custom views.

**Action:**
1. Identify the user task and authoritative requirements for each population.
2. Distinguish required policy or operational differences from preferences.
3. Compare a common statement with controlled variants or role-based views, considering maintenance, accessibility and privacy.
4. Define who owns each variant and how employees are assigned.
5. Test representative populations and ensure that differences in display do not mask differences in underlying calculation.

**Result/evidence:** An approved statement matrix and regression results across in-scope populations.

**SME probe:** *How do you prevent local statements from becoming inconsistent?*  
**Answer outline:** Use shared definitions and governance, justify variants with requirements, assign owners and test common fields consistently.

### 4. A statement displays a total without enough context
**Situation:** A summary displays a total or category but omits the period, unit, status or rule context users need to interpret it correctly.

**Task:** Define the minimum information required for accurate interpretation.

**Action:**
1. Identify the user decision the statement supports.
2. Define the period, unit, category, status and relevant as-of or update context.
3. Confirm the source and calculation meaning for each field.
4. Test totals against detailed records, including corrections and period boundaries.
5. Avoid implying that a time result is a final downstream pay outcome unless that is actually what the view represents.

**Result/evidence:** A field dictionary, reconciled sample and signed-off display requirement.

**SME probe:** *What is the risk of showing only a single total?*  
**Answer outline:** Users may not understand its scope or derivation, and cannot identify the source of a discrepancy. Provide enough context to interpret and investigate the value without overwhelming the view.

### 5. A boundary case makes the statement appear inconsistent
**Situation:** A time interval crosses a day, week, valuation period or policy effective date, and the statement's total appears inconsistent with the detailed rows.

**Task:** Establish consistent period semantics and validate aggregation.

**Action:**
1. Define which period the statement represents and the source of its start/end boundaries.
2. Trace the crossing interval and relevant evaluated result.
3. Compare detailed rows with the aggregate and check inclusion, exclusions, rounding and corrections.
4. Confirm the intended treatment with the policy owner and verify product behavior.
5. Add a boundary test and explain the result in user-facing guidance.

**Result/evidence:** A documented period convention and passing reconciliation tests.

**SME probe:** *Should a statement always use calendar days?*  
**Answer outline:** Not necessarily. The appropriate period may follow policy, schedule, workweek or another defined cycle. Make the basis explicit and validate it.

### 6. A displayed value does not match the underlying result
**Situation:** Testing shows that the detailed result and summary display disagree, or a recent correction is not reflected in the expected view.

**Task:** Locate the first point of divergence and determine whether the issue is calculation, refresh timing, mapping or presentation.

**Action:**
1. Preserve the exact employee, period, record status and observed values in a controlled test case.
2. Compare source records, evaluated output, statement data and any downstream transformation involved.
3. Check update timing, status eligibility, caching or refresh behavior only where applicable to the verified product design.
4. Identify the layer where the value first diverges; avoid changing valuation rules to fix a display defect.
5. Re-test the corrected case and neighboring scenarios.

**Result/evidence:** A reproducible defect, root-cause record and reconciled before/after test.

**SME probe:** *What would you inspect first?*  
**Answer outline:** Trace one record through the actual data path and identify the earliest mismatch. Do not assume the calculation is wrong simply because the display differs.

### 7. Employee and manager disagree about the meaning of a status
**Situation:** An employee sees a status as final, while the manager understands it to mean submitted or awaiting evaluation.

**Task:** Establish an unambiguous status vocabulary aligned to the real process lifecycle.

**Action:**
1. Inventory the statuses the product actually exposes and their transition rules.
2. Ask business owners what each status means to the user and what action is expected next.
3. Distinguish submission, validation, approval, evaluation and downstream consumption where those concepts exist separately.
4. Test transitions including rejection, correction and re-submission.
5. Use concise labels and guidance without claiming that a status guarantees a downstream outcome it does not guarantee.

**Result/evidence:** A status glossary, approved user wording and state-transition test results.

**SME probe:** *Can a “complete” status guarantee the downstream result is final?*  
**Answer outline:** Only if the documented status semantics explicitly support that meaning. Verify the actual lifecycle and clearly state any downstream dependency.

### 8. A user disputes a result but cannot identify the relevant record
**Situation:** An employee reports that a total is wrong but cannot point to the entry, date, interval or correction causing the discrepancy.

**Task:** Design a dispute path that helps the user provide actionable evidence.

**Action:**
1. Define the minimum information needed to investigate: period, category, relevant date/interval and observed versus expected value.
2. Provide a clear route to the underlying record or an approved support/correction process.
3. Make the distinction between a question, a correction request and a policy exception clear.
4. Test the journey for users with different access levels and for records that cannot be edited directly.
5. Assign ownership, expected response steps and escalation for unresolved cases.

**Result/evidence:** A dispute intake template, process map and sample cases demonstrating traceability.

**SME probe:** *Should employees be allowed to edit every disputed result directly?*  
**Answer outline:** No. Access should follow role and process controls. Some issues require source correction, approval or policy interpretation rather than direct editing of a calculated result.

### 9. A correction changes a previously viewed statement
**Situation:** A time record is corrected after the employee or manager has already reviewed a statement, creating confusion about why the value changed.

**Task:** Define how corrected results are communicated and reconciled while preserving the historical trail.

**Action:**
1. Determine which source record changed, why, who authorized it and which periods/results are affected.
2. Verify how the product exposes correction history and updated result timing.
3. Define whether a user needs a new notification, an updated statement, an explanation or a controlled dispute response.
4. Reconcile the before/after result and downstream dependencies where relevant.
5. Test repeated corrections and ensure the latest authorized state is clear without erasing necessary history.

**Result/evidence:** A correction communication rule, traceable before/after example and reconciliation record.

**SME probe:** *Should the old statement simply be overwritten?*  
**Answer outline:** The user-facing view may update, but required audit/history must be preserved according to product capability and policy. Confirm the actual retention and history model.

### 10. A product capability for statements is assumed but not verified
**Situation:** A design promises employee-specific statements, drill-down, export or historical views, but the team has not confirmed the exact capability in the target release and configuration.

**Task:** Validate feasibility before committing to a user experience or delivery date.

**Action:**
1. Describe the user need independently of a feature name.
2. Check official documentation for the applicable edition/release and confirm tenant-specific enablement and permissions.
3. Prototype a representative journey in a safe environment if available.
4. Compare supported standard capability, configuration, an approved alternative and any integration/custom approach.
5. Document the evidence, constraints, accessibility implications and maintenance ownership.

**Result/evidence:** A capability decision record and tested recommendation.

**SME probe:** *Can you rely on a demo from another release?*  
**Answer outline:** No. Treat it as a clue, not proof. Verify the release, scope and configuration, then test the required behavior.

### 11. Local policy changes what must be displayed
**Situation:** A country or collective agreement requires different information, explanation or treatment in a time statement.

**Task:** Translate the authoritative requirement into a compliant and maintainable presentation.

**Action:**
1. Obtain the policy source, effective date, covered population and decision owner.
2. Clarify what must be shown, what is optional and what must remain restricted.
3. Identify affected fields, terminology, time periods and supporting workflow.
4. Test examples before and after the effective date and across employee transfers where relevant.
5. Document the requirement trace and owner for future policy changes.

**Result/evidence:** A signed-off display requirement, population matrix and effective-date tests.

**SME probe:** *Can the architect decide what an ambiguous policy requires the statement to show?*  
**Answer outline:** The architect can surface options and impacts, but the authorized policy owner must resolve the interpretation. Record the decision and source.

### 12. Statement visibility exposes information to the wrong role
**Situation:** A statement or report could expose another employee's details, restricted notes or information beyond the user's legitimate need.

**Task:** Ensure role-appropriate visibility while preserving transparency for authorized users.

**Action:**
1. Classify the data and identify legitimate user purposes for employee, manager, HR/support and administrative roles.
2. Define least-privilege access and any required separation between employee-visible explanation and internal case notes.
3. Test direct navigation, list views, exports and delegated access where supported.
4. Check that organizational changes or temporary delegation do not leave inappropriate access.
5. Confirm privacy, retention and access-review requirements with responsible owners.

**Result/evidence:** A field/role access matrix, negative access tests and approved privacy controls.

**SME probe:** *Does transparency mean everyone can see every field?*  
**Answer outline:** No. Transparency means users can understand relevant information within authorized access. Minimize disclosure and verify all supported access paths.

### 13. Leadership wants a metric for statement accuracy or disputes
**Situation:** Leadership requests an accuracy or dispute metric, but the denominator, definition of a valid dispute and treatment of corrected records are unclear.

**Task:** Define a defensible metric that measures quality without hiding legitimate employee questions.

**Action:**
1. Define the event counted, population, period, denominator, exclusions and source of truth.
2. Separate questions, confirmed defects, policy disputes and user misunderstandings.
3. Specify how reopened cases, duplicate tickets and corrections are counted.
4. Validate a sample manually and reconcile the metric to underlying cases.
5. Pair the metric with resolution quality and ageing; avoid targets that discourage legitimate reporting.

**Result/evidence:** A metric definition, reconciled sample and named owner.

**SME probe:** *Why is a low dispute count not enough to prove accuracy?*  
**Answer outline:** Users may not know how to report problems, or the process may discourage disputes. Validate source calculations and resolution outcomes, not just ticket volume.

### 14. A late display change risks UAT or cutover
**Situation:** A stakeholder requests a new field, label or visibility rule near release, potentially affecting privacy, user guidance and test sign-off.

**Task:** Assess scope and risk and recommend a controlled decision.

**Action:**
1. Confirm the business requirement, authority, impacted population and effective date.
2. Analyze effects on data sources, role access, calculations displayed, accessibility, reports and training.
3. Define focused tests for correctness, role access, boundary cases and correction updates.
4. Present options to include with evidence, defer or use an approved interim explanation.
5. Document the decision, residual risk, rollback or contingency and communication.

**Result/evidence:** An approved change decision and updated test/sign-off evidence.

**SME probe:** *What if leadership asks to deploy an untested field visible to all managers?*  
**Answer outline:** Explain the privacy and interpretation risks, define affected users and tests, and escalate to the authorized decision-maker. Do not represent untested access as safe.

### 15. Support repeatedly explains the same result manually
**Situation:** Support teams spend time explaining common statement questions because labels, context or dispute guidance are insufficient.

**Task:** Identify whether the recurring issue is data accuracy, design comprehension, policy ambiguity or training.

**Action:**
1. Categorize inquiries by field, status, population, period and root cause.
2. Reproduce common cases and verify that displayed values match the source/evaluated results.
3. Improve terminology, contextual help, examples or drill-down only where supported and useful.
4. Create a support explanation that traces source record, applicable rule and outcome.
5. Monitor repeat inquiry categories and validate that a reduction does not come from making the dispute route harder to find.

**Result/evidence:** A categorized issue analysis, updated guidance and reviewable user feedback or support measures.

**SME probe:** *How do you distinguish a usability problem from a calculation defect?*  
**Answer outline:** Reconcile the underlying result first. If the calculation is correct but users misinterpret the display, improve presentation; if the value is wrong, correct the underlying cause.

### 16. Audit needs to reconstruct why a result was displayed
**Situation:** An auditor asks how a displayed result was produced, what source records it included and whether it reflected a correction or a particular policy version.

**Task:** Establish a traceable path from source evidence to displayed output.

**Action:**
1. Identify the relevant record, period, source inputs, correction history, effective policy and evaluated output available in the actual product.
2. Document which details are retained natively and which require an approved external evidence source.
3. Test whether an authorized reviewer can reproduce the explanation for a historical case.
4. Confirm access, retention and privacy constraints with control owners.
5. Define a repeatable audit response and evidence package.

**Result/evidence:** An audit trace example, evidence-source map and access/retention sign-off.

**SME probe:** *What if the statement itself does not retain the rule version?*  
**Answer outline:** Do not claim it does. Identify the supported evidence sources needed to reconstruct the result and document any limitation or control gap.

### 17. The customer challenges the proposed statement design
**Situation:** Business stakeholders want a dense statement containing every internal field, while employees ask for a simpler explanation of their time.

**Task:** Balance transparency, usability, privacy and diagnostic depth.

**Action:**
1. Identify user tasks and questions for each audience.
2. Separate essential summary information from detailed diagnostic data and restricted internal information.
3. Compare a layered presentation, role-based views or other supported approaches.
4. Test comprehension with representative users and validate all displayed totals against source data.
5. Document the trade-off and agree who owns field definitions and content maintenance.

**Result/evidence:** A user-tested information design, field dictionary and business sign-off.

**SME probe:** *Why not display every available field?*  
**Answer outline:** More information is not always more transparent. Show what the user needs to interpret and act, with controlled access to additional detail when justified.

### 18. Migration creates historical statement discrepancies
**Situation:** Historical time statements in a legacy system differ from the target because categories, periods, rounding or correction histories are not equivalent.

**Task:** Reconcile the differences and define what can be shown as historical evidence in the target.

**Action:**
1. Sample records across populations, periods, corrections and boundary conditions.
2. Map legacy fields and semantics to target definitions; identify non-equivalent fields explicitly.
3. Reconcile source records, evaluated results and displayed aggregates separately.
4. Classify differences as data defects, approved semantic differences or unresolved issues and obtain business approval.
5. Define historical visibility, migration evidence and go/no-go criteria.

**Result/evidence:** A reconciliation pack, approved difference log and historical-display decision.

**SME probe:** *Should every historical statement match the target exactly?*  
**Answer outline:** Every variance needs an explanation, but exact equality may not be meaningful if definitions differ. Do not silently transform history or accept unexplained differences.

### 19. The statement design cannot explain exceptions clearly
**Situation:** Users see an unusual total or status but cannot tell whether it comes from missing input, a pending approval, a correction, an exception or a genuine evaluated outcome.

**Task:** Improve explainability without exposing internal configuration or presenting an unverified diagnosis.

**Action:**
1. Inventory common exception states and determine which are reliable and supported for user display.
2. Define concise messages, the responsible actor and the next action for each state.
3. Separate confirmed causes from generic “needs review” messages where the system cannot diagnose precisely.
4. Test language, role visibility, corrected cases and stale/pending states.
5. Maintain a mapping from user-facing messages to support diagnostics and policy ownership.

**Result/evidence:** An exception-message catalogue, role-aware guidance and test evidence.

**SME probe:** *Should the system tell the user the exact cause for every exception?*  
**Answer outline:** Only when the cause is reliably known and appropriate to disclose. Otherwise communicate the observed state and next step without inventing a diagnosis.

### 20. Defend the transparency design to a skeptical SME
**Situation:** A senior SME challenges whether the statement accurately represents source records, evaluated results, status, corrections, privacy and downstream dependencies.

**Task:** Demonstrate that the design is understandable, traceable and fit for its audience.

**Action:**
1. State the user groups, business questions, field definitions and policy assumptions.
2. Walk through a normal record, a corrected record and a disputed/boundary case.
3. Trace each displayed value to its verified source and explain status and update timing.
4. Present access tests, reconciliation evidence, product limitations and residual risks.
5. Distinguish personal contribution from team outcomes and use authentic artifacts.

**Result/evidence:** A defensible design decision, reconciled examples, signed-off access requirements and documented limitations.

**SME probe:** *What evidence would make you revise the design?*  
**Answer outline:** A reproducible mismatch, authoritative policy change, privacy/control gap, release limitation or user test showing material misunderstanding. Explain how the change would be assessed and governed.

## Statement and transparency test matrix

| Dimension | Minimum cases |
|---|---|
| Data meaning | Recorded entry; evaluated result; displayed aggregate; downstream outcome clearly distinguished |
| Period semantics | Start/end boundaries; overnight interval; period-crossing record |
| Status | Submitted/pending; approved; rejected; corrected; re-evaluated, where supported |
| Reconciliation | Detail equals defined aggregate; rounding and exclusions documented |
| Correction | Before/after values; history; updated statement; downstream disposition |
| Access | Employee self-view; authorized manager; restricted fields; unauthorized access attempt |
| Population | Different schedules, countries, employee groups and effective dates |
| Exception explanation | Missing data; pending action; disputed result; confirmed versus unknown cause |
| Migration | Legacy field mapping; non-equivalent semantics; historical view |
| Metrics | Dispute definition; denominator; duplicate/reopened cases; manually checked sample |

For every test, record the user role, source inputs, expected display and rationale, actual result, evidence, defect reference and approver. Validate expected values against the approved policy and real data model.

## SME follow-up bank
- What exactly is the source of truth for each displayed field?
- How do you distinguish recorded time from evaluated time?
- What does each status mean in the actual product lifecycle?
- How is a corrected record reflected in the statement?
- How do you prove that a displayed total reconciles to detail?
- Which period and time-zone semantics apply?
- What information should be visible to an employee versus a manager or support user?
- How do you handle restricted notes and historical evidence?
- What if the product does not expose the exact diagnostic detail users request?
- How did you test accessibility and user comprehension?
- How are disputes, reopened cases and corrections counted in metrics?
- How do you explain a legitimate difference between legacy and target statements?
- Which behavior is release-specific and how was it verified?
- What was your personal contribution and what evidence supports it?
- Which residual risk did you communicate and to whom?

## Rapid-fire revision
1. Explain recorded time versus evaluated result.
2. Name three fields needed to interpret a displayed total.
3. Explain why a status label must match actual lifecycle semantics.
4. Give one test for a correction after a statement was viewed.
5. Name one privacy test for employee/manager visibility.
6. Explain how you would investigate a display mismatch.
7. State why a lower dispute count does not prove accuracy.
8. Explain how to handle non-equivalent legacy statement fields.
9. Name one audit artifact that helps reconstruct a result.
10. State one product claim that must be verified for the target release.

## Scoring rubric (0–2 per dimension)
1. **Conceptual clarity:** distinguishes source records, evaluated results, statements and downstream outcomes.
2. **User-centered design:** identifies audience, questions, terminology and next actions.
3. **Traceability:** demonstrates reconciliation, correction history and audit evidence.
4. **Controls:** addresses privacy, role access, exceptions and migration differences.
5. **Evidence and communication:** explains trade-offs and uses authentic, release-aware evidence.

**Target:** 8/10 or better, with no critical issue involving misleading displays, unauthorized disclosure, untraceable corrections or candidate integrity.

## Anti-patterns to avoid
- Treating a displayed total as proof of what was originally recorded.
- Presenting evaluated time as a final payroll outcome without evidence.
- Adding fields without defining their meaning, source or audience.
- Assuming all statuses mean the same thing across product releases.
- Hiding calculation defects behind a user-experience explanation.
- Claiming a statement retains a history or rule version without verifying it.
- Exposing internal or personal data merely in the name of transparency.
- Treating a low dispute count as proof of accuracy.
- Silently changing historical values to force migration equality.
- Presenting hypothetical scenarios as personal project achievements.

## Reusable practice worksheet
- **Problem and audience:**
- **User question the statement must answer:**
- **Source of truth for each field:**
- **Recorded/evaluated/status distinction:**
- **Period and update semantics:**
- **Access and privacy requirements:**
- **Correction/dispute path:**
- **Boundary and reconciliation tests:**
- **Verified result and evidence:**
- **SME challenge and answer:**
- **Residual risk / lesson learned:**

## Success criteria
A strong answer explains what the statement means, where its values come from, which statuses and corrections affect it, who may see each field and how a user can challenge a result. The design should increase understanding without disguising errors, overstating downstream finality or exposing unnecessary information.

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for its business-first discovery philosophy and workforce-time boundaries. It is repository context, not a substitute for release-specific SAP documentation, tenant testing, approved policy or the candidate's authentic project evidence.
