# Interview Stream 04 — Time Recording Profiles & Employee Eligibility

## Outcome
Demonstrate how to translate workforce policy into clear, governed rules for who is eligible to record which time, through which supported process, under what conditions, and how those rules are validated and supported.

## Scope boundary
This stream covers eligibility, recording-profile assignment, employee populations, access and usability, exceptions, and assignment validation. Keep distinct the concepts of **eligibility**, **authorization/access**, **recording method**, **schedule**, **time type**, and **time valuation**. They may interact, but they are not interchangeable.

**Primary focus:** time recording profiles, employee groups, admissibility, eligibility checks, access and usability, exceptions, assignment validation.

Product behavior must be verified for the relevant SAP SuccessFactors edition/release, enabled capabilities and actual tenant configuration. Do not infer exact behavior from a generic scenario.

## STAR response standard
- **Situation:** Describe the real business context, affected employee population, recording problem, constraints and operational impact.
- **Task:** Define your personal responsibility and decision authority.
- **Action:** Explain policy discovery, population segmentation, profile/eligibility design, access controls, exception handling, dependencies and test strategy.
- **Result:** Use verifiable evidence such as an approved eligibility matrix, reconciled assignments, passed negative tests, reduced unresolved exceptions or UAT sign-off. Do not invent metrics.
- **SME probe:** Defend an edge case, rejected alternative, control and evidence trail.
- **Integrity rule:** These are practice scenarios. Do not present hypothetical outcomes as personal project achievements.

## Core distinction checklist
Before designing, establish the answers to these questions:
1. **Who is eligible?** Identify the policy-defined employee population and authoritative attributes.
2. **What may they record?** Confirm permitted recording categories and process rules.
3. **How do they record it?** Establish the supported user or device process for the population.
4. **Who may view, submit, approve or correct records?** Separate process eligibility from role-based authorization.
5. **When does the rule apply?** Confirm effective dates and how changes are handled.
6. **What if the rule cannot be applied?** Define exception ownership, evidence and escalation.
7. **How is it proven?** Define positive, negative, boundary, regression and end-to-end tests.

## 20 structured STAR practice scenarios

### 1. Eligible employees cannot record time
**Situation:** A group of employees reports that the expected time-recording option is unavailable, while other employees appear to use it successfully.

**Task:** Determine whether the cause is eligibility, assignment, access, user process or another dependency.

**Action:**
1. Establish the affected population, examples, dates and expected business behavior.
2. Compare employee attributes and relevant effective-dated assignments with a known-good employee.
3. Trace eligibility rules separately from authorization, recording method and profile assignment.
4. Verify the applicable product capability and tenant configuration.
5. Test the corrected rule with both affected and unaffected populations; document the root cause and preventive control.

**Result:** Present the defect evidence, approved correction and regression-test results.

**SME probe:** Why not immediately grant the affected users broader access?  
**Answer outline:** Broad access may mask an eligibility or assignment defect and violate least privilege. Establish the root cause before changing authorization.

### 2. A recording profile is assigned to the wrong population
**Situation:** Employees in a population receive a recording experience that does not match their approved work arrangement.

**Task:** Correct assignment logic and determine the scope of impact.

**Action:** Compare policy-defined populations with assignment criteria; inspect authoritative employee attributes and effective dates; identify all affected employees; define the correct mapping with the business owner; test intended and excluded groups; reconcile assignments after the correction.

**Result:** Use a signed-off employee-to-profile matrix and reconciliation results as evidence.

**SME probe:** What is the danger of fixing only the reported employee?  
**Answer outline:** The defect may be systemic. Check whether the same condition affects the wider population and create a repeatable control.

### 3. The business asks for one global eligibility rule
**Situation:** A global design seeks one eligibility model, but local policy and workforce arrangements differ.

**Task:** Balance standardization with justified employee-group variation.

**Action:** Define global principles; gather approved local rules; segment populations using authoritative attributes; distinguish true policy differences from naming or process preferences; document exception governance; verify supported configuration and test both shared and local cases.

**Result:** An approved global rule set with explicit, owned exceptions provides a defensible design.

**SME probe:** When is a local exception justified?  
**Answer outline:** When a documented policy, legal, contractual or operational requirement materially changes the behavior and is approved by the accountable owner—not simply because a stakeholder prefers a different setup.

### 4. Eligibility depends on effective-dated employee data
**Situation:** A transfer, employment change or other employee-data update should change a person's time-recording eligibility, but the result appears stale or premature.

**Task:** Determine how the change should take effect and ensure the rule uses the correct data at the correct time.

**Action:** Confirm the authoritative attribute and effective date; map the change event to the relevant eligibility and assignment process; test before, on and after the effective date; inspect synchronization or processing dependencies; define exception handling for incomplete or late data; obtain business sign-off.

**Result:** Evidence includes an effective-date test matrix and a reconciled set of representative employee cases.

**SME probe:** Should eligibility change as soon as a manager submits a future-dated change?  
**Answer outline:** The expected timing must be defined from the business rule and verified against actual product processing. Do not assume submission date and effective date are equivalent.

### 5. Recording eligibility is confused with authorization
**Situation:** A stakeholder proposes granting broader permissions to solve a problem where users cannot complete a recording task.

**Task:** Determine which control layer is failing without weakening security.

**Action:** Reproduce the user journey; confirm the employee is eligible for the process; inspect the relevant role/access path separately; check whether the feature is supported and enabled; use least-privilege test identities; validate both permitted actions and prohibited actions.

**Result:** The defect is classified and addressed at the appropriate control layer, with positive and negative test evidence.

**SME probe:** How do you prove that a solution did not over-authorize users?  
**Answer outline:** Test representative roles against both allowed and denied actions, and retain the approved access matrix and test evidence.

### 6. Different populations use different recording methods
**Situation:** Office staff, mobile employees and operational workers may use different approved recording processes.

**Task:** Provide a coherent eligibility model without assuming every method is available to every group.

**Action:** Identify the business need, device/work context and supported process for each group; document who may use each method; verify product, licensing, configuration and integration prerequisites as relevant; test complete journeys and failure paths; define support ownership.

**Result:** An approved population-to-method matrix and end-to-end test evidence show the intended process for each group.

**SME probe:** Should one method be enabled for everyone to simplify support?  
**Answer outline:** Only if it satisfies policy, usability, security and technical constraints for every population. Simplicity alone is insufficient.

### 7. A temporary worker or contingent population has unclear eligibility
**Situation:** The organization onboards a non-standard workforce population, but policy owners have not agreed which recording rules apply.

**Task:** Prevent assumptions from becoming production policy.

**Action:** Identify the legal/employment classification and authoritative policy owner; record unanswered questions; compare the population with existing approved groups; assess access and downstream implications; agree a documented interim decision only if authorized; create explicit tests for inclusion and exclusion.

**Result:** A signed-off eligibility decision or a clearly controlled unresolved-decision log provides evidence.

**SME probe:** What do you do if the go-live date arrives before policy is confirmed?  
**Answer outline:** Escalate the decision and risk to the accountable owner. Do not silently classify the population based on convenience; proceed only under an approved, controlled decision.

### 8. An employee is eligible but lacks the required assignment
**Situation:** Policy says an employee may record time, but the required profile or related setup is missing.

**Task:** Separate the eligibility decision from the configuration or data-assignment failure.

**Action:** Verify the approved eligibility rule; inspect assignment completeness and effective dating; check the upstream employee-data source; identify whether the issue is isolated or systematic; correct it through the approved route; test both the recording journey and future assignment prevention.

**Result:** A reconciliation and root-cause record demonstrate resolution and prevention.

**SME probe:** Is adding a missing assignment always the correct fix?  
**Answer outline:** Only after confirming that the employee is eligible and the assignment is genuinely missing. Otherwise, the change could create unauthorized or incorrect behavior.

### 9. The organization changes its recording policy
**Situation:** A new policy changes which employee groups must record time or which recording options they may use.

**Task:** Translate the approved policy into controlled configuration and rollout activities.

**Action:** Obtain the signed policy and effective date; map impacted populations and existing assignments; assess access, training, interfaces and downstream dependencies; define transition and historical-data rules; build positive, negative and regression tests; plan communications and rollback criteria.

**Result:** A traceable change package with approved requirements and successful tests demonstrates readiness.

**SME probe:** What must be decided about historical records?  
**Answer outline:** Determine whether the policy is prospective or requires an approved historical correction. Preserve auditability and avoid changing prior records without a defined rule.

### 10. The product capability is assumed rather than verified
**Situation:** A design proposal depends on a specific profile behavior or eligibility option that the team has not verified.

**Task:** Validate feasibility before committing to the solution.

**Action:** Capture the business requirement without embedding an assumed implementation; consult documentation for the relevant edition/release; inspect the configured tenant or a controlled test environment; record prerequisites and limitations; test a representative case; present alternatives if unsupported.

**Result:** A documented feasibility decision with evidence and caveats avoids an unsupported design commitment.

**SME probe:** What if documentation and observed tenant behavior differ?  
**Answer outline:** Capture the exact release, configuration and reproducible case; investigate with authoritative product support/documentation; do not generalize from one observation or silently choose whichever source is convenient.

### 11. Country or collective-agreement rules change eligibility
**Situation:** Eligibility varies by country, contractual arrangement or employee group, and stakeholders provide conflicting interpretations.

**Task:** Establish a source of truth and a controlled decision model.

**Action:** Identify the accountable policy/legal/HR owner; capture the rule and effective date; distinguish eligibility from the details of recording and valuation; document scope, exceptions and approval; verify the product mapping; test included and excluded populations and boundary dates.

**Result:** An approved rule matrix with accountable owners and traceable tests supports a consistent implementation.

**SME probe:** Should a consultant interpret ambiguous legal or collective-agreement language independently?  
**Answer outline:** No. Clarify the technical implications, document ambiguity and obtain a decision from the authorized policy/legal owner.

### 12. Integration data causes incorrect eligibility
**Situation:** Employee attributes arrive from an upstream HR source or interface, and some employees receive an incorrect recording setup.

**Task:** Trace the issue across source data, mapping, processing and target assignment.

**Action:** Select affected records and compare source values with target values; inspect mapping and transformation rules; verify effective dates and processing timing; agree field ownership; test valid, missing and unexpected values; add reconciliation and error handling.

**Result:** Source-to-target evidence and end-to-end retests show whether the integration or target rule caused the mismatch.

**SME probe:** How do you prevent a target-side workaround from hiding an upstream defect?  
**Answer outline:** Track the field to its authoritative source, assign ownership, correct the mapping or source issue where appropriate, and keep a control for residual exceptions.

### 13. Stakeholders disagree about who should record time
**Situation:** Operations expects a population to record time, while HR or policy owners believe the population is exempt.

**Task:** Resolve the policy decision before designing eligibility.

**Action:** Document the competing interpretations and affected roles; identify authoritative policy and decision rights; quantify operational and compliance implications using available evidence; facilitate a decision; record assumptions and exceptions; configure and test only against the approved outcome.

**Result:** A signed decision record and testable eligibility rules prevent unresolved policy debate from being disguised as a technical choice.

**SME probe:** What if stakeholders refuse to decide?  
**Answer outline:** Escalate the unresolved decision, record the risk and delivery impact, and avoid representing an assumption as approved policy.

### 14. Exception handling has become a manual workaround
**Situation:** Support staff repeatedly adjust employee assignments or help users bypass a recording limitation.

**Task:** Decide whether the exception is valid, preventable or a candidate for a controlled system-supported process.

**Action:** Categorize exceptions by cause and population; identify policy versus data versus access issues; assess frequency, risk and control requirements; validate any proposed automation; define approvals and audit evidence; test both the standard path and exception path.

**Result:** A documented exception taxonomy, ownership and control design provides evidence of a sustainable approach.

**SME probe:** When should an exception remain manual?  
**Answer outline:** When it is rare, judgment-dependent or unsafe to automate without additional controls. Manual handling still needs ownership, authorization and traceability.

### 15. Users can record time but cannot complete the expected workflow
**Situation:** The recording action appears available, but users cannot submit, correct or complete the expected process.

**Task:** Map the complete user journey and isolate the failing step.

**Action:** Observe the journey with a representative user; verify eligibility, access, workflow prerequisites and relevant data; capture the exact state and error; distinguish usability confusion from a control or configuration defect; test the corrected journey with permitted and prohibited actions.

**Result:** Journey-level test evidence confirms the user can complete the intended process without bypassing controls.

**SME probe:** Why is testing only the initial recording action insufficient?  
**Answer outline:** The business outcome may depend on later submission, approval, correction or processing steps; validate the full journey.

### 16. Privacy requirements restrict visibility or correction
**Situation:** The organization needs employees, managers, administrators and support staff to have different levels of access to time records.

**Task:** Design and validate least-privilege access without confusing role permissions with eligibility.

**Action:** Identify data sensitivity and role responsibilities; map allowed view/create/submit/approve/correct actions; confirm segregation-of-duties needs; verify supported access controls; test authorized and unauthorized scenarios; document approvals and evidence-retention requirements.

**Result:** An approved access matrix and negative-test results demonstrate that the process supports the intended privacy controls.

**SME probe:** Can eligibility rules replace role-based access controls?  
**Answer outline:** No. They answer different questions. Validate each control independently and test their combined effect.

### 17. A late change threatens the release
**Situation:** Shortly before release, a stakeholder asks to include another employee population or change the eligibility rule.

**Task:** Assess the change transparently and protect delivery quality.

**Action:** Clarify the requested behavior and business rationale; identify affected profiles, populations, interfaces, training and access; estimate test and migration implications using evidence; document risk and options; obtain the required change approval; update regression and cutover plans.

**Result:** An approved go/no-go decision with recorded impact and test evidence is a credible outcome.

**SME probe:** What if leadership insists on proceeding with incomplete testing?  
**Answer outline:** Explain the evidence gap, impact and residual risk; recommend the proportionate control or deferral; record the accountable risk acceptance rather than presenting untested behavior as validated.

### 18. Migration exposes inconsistent employee eligibility data
**Situation:** Legacy records contain overlapping, missing or obsolete indicators that were previously used to decide who could record time.

**Task:** Map the legacy logic to approved target rules and establish migration readiness.

**Action:** Profile the source data; identify authoritative fields and data owners; map legacy values to target eligibility; classify unmapped records; reconcile expected target populations; test boundary cases and effective dates; define defect thresholds and business sign-off criteria.

**Result:** A reconciled mapping, exception disposition and approved go/no-go criteria demonstrate control.

**SME probe:** What do you do with an unmapped legacy code?  
**Answer outline:** Do not guess. Assign it to the data/policy owner, document its impact, and obtain a controlled mapping or explicit exclusion before migration approval.

### 19. Support cannot explain why a user is ineligible
**Situation:** The help desk receives repeated eligibility complaints but has no consistent method to identify the rule or assignment involved.

**Task:** Create a diagnostic process that is repeatable, secure and useful for root-cause analysis.

**Action:** Define a troubleshooting sequence covering employee attributes, effective date, approved population, profile/assignment, access and dependencies; specify what evidence support may access; establish escalation criteria; capture root cause and resolution categories; validate the runbook against representative cases.

**Result:** A reviewed support runbook and traceable case classification improve diagnosis consistency; quantify improvements only when measured.

**SME probe:** What information should support collect first?  
**Answer outline:** Employee/population identifier according to policy, affected date, expected versus actual behavior, relevant assignment state and error evidence—using only approved access and data-handling practices.

### 20. Defending the eligibility model in an architecture review
**Situation:** An architect or process owner challenges the model as too complex, insecure or difficult to maintain.

**Task:** Demonstrate that the model follows approved policy, uses supported capabilities and can be operated reliably.

**Action:** Present the population matrix, rule ownership, effective-date handling, profile assignment, access boundaries, exception process and test evidence; compare alternatives; explain negative and boundary tests; disclose unresolved assumptions, version constraints and residual risks.

**Result:** A documented decision, approved conditions and testable operational controls demonstrate design readiness. Do not claim unresolved risks are closed.

**SME probe:** What evidence would make you redesign the eligibility model?  
**Answer outline:** Verified policy gaps, unsupported behavior, excessive exception volume, recurring assignment failures, access-control weaknesses or a changed workforce model should trigger a formal review.

## SME follow-up bank
- How do you distinguish eligibility from authorization?
- Which employee attributes are authoritative for eligibility, and who owns them?
- How do you handle effective-dated changes and late-arriving source data?
- What is the difference between recording-profile assignment and a recording method?
- How do you test that an ineligible employee cannot use a restricted process?
- How do you test that an eligible employee is not blocked by an unrelated access defect?
- How are country, contractual and employee-group exceptions approved?
- What evidence proves the target population matches the approved policy?
- How do you investigate a source-to-target eligibility mismatch?
- What do you do when the requested capability cannot be verified for the target release?

## Rapid-fire revision
1. Define eligibility in one sentence.
2. Name three data or policy inputs that can affect eligibility.
3. Explain eligibility versus authorization.
4. Why must effective dates be tested?
5. Give one positive and one negative eligibility test.
6. How do you prove a profile assignment is correct?
7. What is the risk of a blanket default?
8. How do you govern local exceptions?
9. What should be included in an eligibility reconciliation?
10. What evidence supports a strong STAR result?

## Validation checklist
- Policy owner and authoritative rule are identified.
- Employee populations and exclusions are explicit.
- Required attributes and their source ownership are documented.
- Effective dates, transfers and late data are covered.
- Eligibility is distinguished from authorization and recording method.
- Profile/assignment behavior is verified in the target release and configuration.
- Positive, negative, boundary, regression and end-to-end tests are defined.
- Exception handling, support ownership and audit trail are documented.
- Privacy and least-privilege controls are tested.
- Reconciliation evidence and sign-off criteria are retained.

## Scoring rubric (0–2 per dimension)
1. Business problem and affected population are clear.
2. Personal ownership and decision rights are explicit.
3. Eligibility, assignment and access concepts are technically distinguished.
4. Exceptions, dependencies and validation are addressed.
5. Result is evidence-backed and the SME probe demonstrates sound judgment.

**Target:** 8/10 or better, with no critical technical accuracy or candidate-integrity issue.

## Anti-patterns to avoid
- Treating eligibility, profile assignment, recording method and authorization as the same concept.
- Granting broad access to compensate for a data or assignment defect.
- Assuming all employees in a country or job group share one rule.
- Turning an unresolved policy interpretation into a configuration assumption.
- Ignoring effective dates, source-data ownership and downstream dependencies.
- Claiming product capabilities without release/configuration verification.
- Presenting a hypothetical scenario or unmeasured improvement as personal project history.

## Reusable practice worksheet
- **Eligibility problem and affected population:**
- **My role and authority:**
- **Approved policy and owner:**
- **Authoritative employee attributes:**
- **Eligibility/assignment/access distinction:**
- **Options and trade-offs:**
- **Effective dates and exceptions:**
- **Tests and reconciliation evidence:**
- **Verified result:**
- **SME challenge and response:**
- **Lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for business-first discovery and domain boundaries. The scenarios are interview-practice structures, not claims that a particular configuration behaves identically across SAP SuccessFactors releases. Validate product-specific behavior against the relevant SAP documentation and actual tenant configuration.
