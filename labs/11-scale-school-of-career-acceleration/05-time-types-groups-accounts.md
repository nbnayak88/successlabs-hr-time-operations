# Interview Stream 05 — Time Types, Time Type Groups & Time Accounts

## Outcome
Demonstrate how to design understandable, governed time concepts that reflect approved workforce policy, support correct recording and balance behavior, and remain testable across employee populations and downstream processes.

## Scope boundary
This stream covers semantic design and assignment of time recording and balance concepts. Keep distinct the concepts of **time type**, **time type group**, **time account type**, **time account/balance**, **recorded time**, **evaluated time**, and downstream payroll or reporting outputs. Their precise semantics and relationships must be verified for the relevant product edition/release and tenant configuration.

**Primary focus:** time types, time type groups, time account types, semantic consistency, configuration dependencies, naming standards, balance behavior.

## STAR response standard
- **Situation:** State the business context, affected population, policy question, constraints and impact.
- **Task:** Clarify your personal ownership and decision authority.
- **Action:** Explain policy discovery, semantic modelling, assignment rules, design alternatives, dependencies, exception handling and validation.
- **Result:** Use authentic evidence: an approved concept catalogue, reconciled balances, test results, signed-off policy mappings, resolved defects or audit evidence. Do not invent metrics.
- **SME probe:** Defend a design choice, boundary case, exception, alternative and control.
- **Integrity rule:** These are practice scenarios, not claims about personal history. Label unexperienced cases as lab/design exercises.

## Core semantic design checklist
Before creating or changing a concept, ask:
1. What business meaning does it represent, and who owns that definition?
2. Is it a recording category, grouping/selection concept, balance-account concept, or downstream result?
3. Which employee populations and policies use it?
4. What are the eligibility, validity, effective-date and exception rules?
5. What other concepts or processes depend on it?
6. How should it behave for corrections, missing data, boundary dates and historical records?
7. What source documentation confirms the intended product behavior?
8. How will the design be tested, reconciled, named, governed and retired?

## 20 structured STAR practice scenarios

### 1. Similar time types confuse employees and support
**Situation:** Employees and administrators choose between several time types with overlapping or unclear labels, causing incorrect entries and repeated clarification.

**Task:** Improve semantic clarity without changing policy behavior inadvertently.

**Action:**
1. Review the approved policy, existing catalogue, usage patterns and reported errors.
2. Ask process owners to define each concept in plain business language, including inclusions, exclusions and examples.
3. Identify duplicates, ambiguous labels and genuine policy distinctions.
4. Propose consistent names and descriptions; preserve required distinctions and assess dependent processes before consolidation.
5. Validate with representative users and regression tests.

**Result:** Use an approved catalogue, user validation and test evidence to demonstrate clearer choices.

**SME probe:** Can two concepts be merged because their names sound similar?  
**Answer outline:** No. Compare policy meaning, behavior, population, reporting and dependencies; merge only with owner approval and regression evidence.

### 2. A global catalogue does not fit local policies
**Situation:** A global time-type catalogue covers common needs but different countries or employee groups have approved variations.

**Task:** Standardize common semantics while allowing controlled variation.

**Action:** Establish global naming and governance principles; collect authoritative local policy inputs; map shared and distinct concepts; distinguish semantic differences from labels; document ownership and approval; validate each local variation against supported product behavior.

**Result:** A governed global catalogue with documented local exceptions and test coverage supports maintainability.

**SME probe:** What belongs in the global template?  
**Answer outline:** Shared semantics and controls that genuinely apply across populations. Local variations should be explicit, policy-backed and owned rather than hidden in informal workarounds.

### 3. A time type has downstream implications nobody considered
**Situation:** A requested recording category may influence valuation, balances, reporting, absence processing or downstream consumers, but the request focuses only on the user-facing label.

**Task:** Surface dependencies before approving the design.

**Action:** Trace the business meaning from policy to recording, grouping, relevant evaluation/balance behavior and downstream use; identify each dependency owner; document the expected end-to-end outcome; validate product-specific relationships; build tests across the affected process chain.

**Result:** An approved dependency map and end-to-end test evidence demonstrate that the design is not merely a label change.

**SME probe:** How do you avoid overengineering a simple request?  
**Answer outline:** Scope analysis to plausible dependencies and risk, confirm them with owners, and document what is out of scope rather than assuming every downstream process is affected.

### 4. Time type groups are being used as a catch-all
**Situation:** A configuration catalogue has broad groups that mix concepts with different business meanings, making assignment and maintenance difficult.

**Task:** Improve conceptual organization without relying on names alone to infer behavior.

**Action:** Inventory current membership and actual use; identify the purpose each group is intended to serve; compare that purpose with supported product semantics; propose a clearer grouping model; check assignment and user-selection effects; test representative employee journeys before migration.

**Result:** A reviewed grouping model and regression evidence show the rationale and impact of the change.

**SME probe:** Should a group be created only to reduce the number of items users see?  
**Answer outline:** Usability matters, but grouping must also preserve valid semantics and supported behavior. Confirm how the group is consumed before designing around its label.

### 5. Time account types and balances are misunderstood
**Situation:** Stakeholders refer to a time category, a balance account and a displayed balance as if they were the same object.

**Task:** Align the business vocabulary and establish the intended balance lifecycle.

**Action:** Facilitate a terminology session; define the business meaning and ownership of each concept; map the policy to the supported account/balance model; document accrual, usage, adjustment, expiry or carryover rules only where applicable; confirm configuration and test cases with the product/process owner.

**Result:** A signed-off concept glossary and lifecycle test matrix reduce ambiguity.

**SME probe:** What is the difference between an account type and an account balance?  
**Answer outline:** Explain the distinction using the actual configured model: the type defines the account category/rules, while the balance is the resulting quantity/state for a relevant employee and period. Verify the precise implementation semantics before making a product-specific claim.

### 6. A balance does not match the approved expectation
**Situation:** An employee or administrator reports that a time account balance differs from the policy-based expectation.

**Task:** Find the cause without applying an arbitrary manual adjustment.

**Action:** Confirm the policy, relevant period and expected calculation; inspect source events, effective dates, account lifecycle rules and any applicable processing dependencies; compare the system result with a controlled calculation; identify whether the issue is data, configuration, timing or interpretation; correct through the approved route and reconcile.

**Result:** A reproducible calculation, defect/root-cause record and reconciled retest provide credible evidence.

**SME probe:** Why not directly adjust the balance to the expected number?  
**Answer outline:** That may hide the root cause and break auditability. Establish why the balance differs, determine whether an adjustment is permitted, and preserve approval and evidence.

### 7. Naming conventions have become inconsistent
**Situation:** Similar concepts use inconsistent names, abbreviations and descriptions across modules or populations.

**Task:** Introduce a naming standard that helps administrators understand intent and impact.

**Action:** Inventory names and descriptions; agree naming principles with business and technical owners; distinguish user-facing labels from technical identifiers where applicable; document a glossary and ownership; assess dependencies before renaming; test user-facing and integration/reporting impacts.

**Result:** A governed naming standard and reviewed catalogue improve discoverability and maintenance.

**SME probe:** Is renaming a purely cosmetic change?  
**Answer outline:** Not always. Names or identifiers may be referenced by rules, interfaces, reports or user workflows; check the actual dependencies and supported change process first.

### 8. Employee populations require different time concepts
**Situation:** Two groups have different contractual rules, but the existing design assumes they use the same time concepts.

**Task:** Model the distinction explicitly and avoid unnecessary duplication.

**Action:** Confirm policy differences and population criteria; compare semantic requirements and downstream behavior; decide which concepts can be shared and which require separate treatment; document assignment and governance; test both groups plus transition cases when employees change group.

**Result:** An approved population-to-concept matrix and cross-population tests demonstrate the design.

**SME probe:** How do you avoid concept proliferation?  
**Answer outline:** Create a separate concept only for a meaningful, approved behavioral distinction. Use shared concepts when semantics are truly equivalent and the product model supports reuse safely.

### 9. Corrections and reversals create duplicate or inconsistent balances
**Situation:** Corrected or reversed records appear to leave an unexpected balance or duplicate effect.

**Task:** Trace the lifecycle and determine the supported correction path.

**Action:** Preserve the original and corrected event history; establish the intended policy; inspect how the configured process handles reversals and recalculation; reproduce the issue in a controlled environment; confirm dependencies and audit requirements; test correction, reprocessing and reconciliation paths.

**Result:** Evidence should include the defect reproduction, approved correction method and before/after reconciliation.

**SME probe:** Should administrators delete the original record to fix the balance?  
**Answer outline:** Do not assume deletion is appropriate. Follow the supported correction process, preserve audit history and verify downstream effects.

### 10. Effective dates change the meaning of a time concept
**Situation:** A policy changes on a specific date, and the team must decide how a time type or account rule applies before and after that date.

**Task:** Define the transition behavior and protect historical correctness.

**Action:** Obtain the approved policy effective date; identify impacted populations and periods; distinguish prospective change from historical correction; verify supported effective-dating behavior; test records on either side of the boundary; document reconciliation and approval requirements.

**Result:** A signed policy decision and effective-date test evidence establish the intended transition.

**SME probe:** Should a new rule automatically recalculate prior periods?  
**Answer outline:** Never assume that. Confirm policy intent, product behavior, audit implications and downstream effects before any historical recalculation.

### 11. A time account lifecycle rule is ambiguous
**Situation:** Stakeholders disagree about accrual, usage, carryover, expiry or adjustment for a balance-related concept.

**Task:** Prevent unresolved policy from being implemented as a technical guess.

**Action:** Document each disputed rule with an example; identify the accountable policy owner; clarify eligibility, timing, limits, exceptions and approval; separate policy decisions from implementation options; verify product capability; obtain signed approval and derive test cases.

**Result:** A decision log, approved lifecycle definition and executable test cases provide evidence.

**SME probe:** What do you do if the policy owner cannot decide before the sprint ends?  
**Answer outline:** Record the unresolved decision, risk and affected scope; escalate to the accountable owner; do not invent a rule or claim the design is complete.

### 12. Time concepts do not map cleanly to an integration
**Situation:** A downstream consumer expects a different code or meaning than the time-management configuration provides.

**Task:** Establish an explicit semantic mapping and end-to-end ownership.

**Action:** Identify source and target definitions; confirm field/code ownership and transformation rules; document one-to-one, one-to-many or unmapped cases where applicable; assess effective dates and error handling; test representative values and exceptions; reconcile source and target results with the receiving owner.

**Result:** An approved mapping specification and end-to-end reconciliation demonstrate the mapping's correctness.

**SME probe:** Should the source catalogue be redesigned to match the target system's codes?  
**Answer outline:** Not automatically. Preserve the source business meaning, use a governed mapping where appropriate, and change the source model only when justified by approved architecture and policy.

### 13. A reporting metric has no agreed definition
**Situation:** Leadership asks for totals by time category or balance, but stakeholders disagree about which concepts and exclusions belong in the measure.

**Task:** Define a reproducible metric before building the report.

**Action:** Agree the business question, population, period, inclusion/exclusion rules, treatment of corrections and data source; identify whether the metric uses recorded events, evaluated outcomes or balances; define reconciliation and ownership; test known cases and obtain sign-off.

**Result:** A metric definition, lineage note and reconciled sample provide evidence that the number is meaningful.

**SME probe:** Why is a report total not automatically the source of truth?  
**Answer outline:** It depends on the selected data, timing, filters and semantic definition. Reconcile to the authoritative process and explain limitations.

### 14. A late request introduces a new time category
**Situation:** Near release, a stakeholder requests a new time type or account-related concept to address an emerging requirement.

**Task:** Evaluate the change without compromising release readiness.

**Action:** Clarify the policy and desired outcome; check whether an existing concept already represents the same meaning; assess configuration, assignment, reporting, integration and support impact; identify required tests and data changes; obtain change approval; document go/no-go criteria.

**Result:** An approved decision with impact assessment and test evidence shows controlled change management.

**SME probe:** When would you reject the request for the current release?  
**Answer outline:** If policy is unresolved, dependencies are unknown, supported behavior is unverified, or critical validation cannot be completed safely, recommend deferral or an approved controlled alternative.

### 15. Repeated support incidents point to a semantic defect
**Situation:** Support repeatedly corrects entries or explains confusing balances, but each case is treated as an isolated incident.

**Task:** Identify whether a common concept-definition or assignment issue is driving the incidents.

**Action:** Categorize incidents by concept, population, dates and root cause; compare actual behavior with policy; identify confusing names, overlaps or missing rules; validate a systemic correction with owners; test affected and unaffected cases; update documentation and support diagnostics.

**Result:** A root-cause analysis, approved correction and post-change case review demonstrate prevention; quantify improvement only when measured.

**SME probe:** How do you distinguish a training issue from a design defect?  
**Answer outline:** Observe the user journey, compare system behavior with approved policy and inspect error patterns. If users consistently misinterpret ambiguous choices or system behavior diverges from policy, training alone may not be enough.

### 16. Privacy and audit requirements affect account maintenance
**Situation:** The organization must limit who can view, adjust or approve balance-related records and preserve evidence for changes.

**Task:** Design controlled maintenance and access boundaries.

**Action:** Identify sensitive information and role responsibilities; map view/create/adjust/approve actions; define segregation and approval needs; verify supported authorization and audit capabilities; test allowed and denied actions; document evidence retention and emergency access procedures.

**Result:** An approved access matrix, negative tests and sample audit trail support the control design.

**SME probe:** Can a business rule alone protect access to a balance?  
**Answer outline:** Do not rely on a single control layer. Verify role-based authorization, process rules and audit capabilities independently and test their combined behavior.

### 17. Migration contains duplicate or obsolete concepts
**Situation:** A legacy system has overlapping codes, unused types and balances whose meanings are poorly documented.

**Task:** Rationalize and map the legacy model without losing necessary historical meaning.

**Action:** Profile code usage and balances; identify authoritative policy owners; classify target mapping as direct, transformed, retired or unresolved; document how historical records and balances will be treated; reconcile sample and full-population totals; define exception ownership and go/no-go thresholds.

**Result:** A signed mapping register, reconciliation report and approved exception disposition demonstrate readiness.

**SME probe:** Can unused legacy concepts be dropped from migration scope?  
**Answer outline:** Only after checking historical reporting, audit, retention, open balances, interfaces and business requirements; record the decision and its rationale.

### 18. An administrator proposes manual balance adjustments as routine operations
**Situation:** Manual adjustments are increasingly used to compensate for unclear rules or recurring processing issues.

**Task:** Determine which adjustments are legitimate exceptions and which indicate a systemic defect.

**Action:** Review adjustment reasons, authorization, frequency and audit evidence; compare each case with the approved lifecycle rules; identify root causes; define permitted adjustment categories and approvals; validate correction paths; introduce monitoring and reconciliation.

**Result:** A controlled adjustment policy and exception register provide traceability and a basis for root-cause prevention.

**SME probe:** What makes a manual adjustment acceptable?  
**Answer outline:** A documented business reason, authorized approver, supported method, retained audit evidence and validated downstream impact. The exact control must follow the organization's policy and product capability.

### 19. Users cannot explain recorded time versus a balance
**Situation:** Employees see a recorded event and a balance value but assume one should directly equal the other.

**Task:** Improve transparency without implying a relationship that the configured model does not support.

**Action:** Map the lifecycle from entry to relevant processing and balance effect; confirm the actual rule and timing; create a plain-language explanation with examples; test normal, corrected and excluded cases; define when users should raise a query and what support should inspect.

**Result:** A validated explainer, sample scenarios and user feedback provide evidence of improved understanding.

**SME probe:** Does every recorded event immediately change a balance?  
**Answer outline:** Do not generalize. It depends on the concept, configured process and timing; verify the actual lifecycle and communicate it clearly.

### 20. Defending the time-concept model in an architecture review
**Situation:** An architect challenges the catalogue as too complex, semantically inconsistent or difficult to govern.

**Task:** Defend the design using approved business meaning, supported product behavior and evidence.

**Action:** Present the glossary, catalogue, ownership, population mapping, dependencies and lifecycle rules; compare alternatives; explain naming and reuse decisions; walk through correction, effective-date and integration cases; show tests and reconciliation; disclose unresolved risks and version constraints.

**Result:** A documented architecture decision with approved conditions, ownership and validation evidence demonstrates design readiness.

**SME probe:** What evidence would make you redesign the model?  
**Answer outline:** Duplicate semantics, unresolved policy conflicts, unsupported behavior, recurring errors, inconsistent balances, poor traceability or a changed business model should trigger a controlled review.

## SME follow-up bank
- What business meaning does each time concept represent?
- How do you distinguish a recording category, grouping concept and account/balance concept?
- Who owns the policy definition and approval?
- What is the lifecycle for creation, use, correction, expiry or retirement where applicable?
- How do effective dates affect historical records and balances?
- How do you prove a balance matches the approved rule?
- What happens when a correction or reversal is processed?
- How do you handle duplicate or unmapped legacy codes?
- How do you preserve semantic meaning across integrations and reports?
- Which claims require release-specific documentation or tenant validation?

## Rapid-fire revision
1. Why must concepts have clear business definitions?
2. Name three dependencies to assess before changing a time type.
3. Why are a time account type and a balance not synonymous?
4. How do you validate an unexpected balance?
5. What should a concept glossary contain?
6. Why can renaming require impact analysis?
7. How should an unmapped legacy code be handled?
8. What makes a manual adjustment auditable?
9. How do you define a trustworthy time-related metric?
10. What evidence would you present to an architecture reviewer?

## Validation checklist
- Business definition, examples, exclusions and owner are documented.
- Recording, grouping, account and balance semantics are clearly distinguished.
- Population and assignment rules are approved.
- Effective-date and historical-data behavior is understood.
- Dependencies across recording, evaluation, absence, integration and reporting are assessed where relevant.
- Corrections, reversals, adjustments and exceptions are tested.
- Naming, reuse, ownership and retirement follow governance.
- Mappings and balances are reconciled for migration/integration scenarios.
- Access and audit requirements are tested.
- Product-specific behavior is verified against the applicable release and tenant configuration.

## Scoring rubric (0–2 per dimension)
1. Business semantics and policy context are clear.
2. Personal accountability is explicit.
3. Concepts and dependencies are distinguished accurately.
4. Exceptions, controls and validation are addressed.
5. Results are evidence-backed and the SME probe demonstrates judgment.

**Target:** 8/10 or better, with no critical technical accuracy or candidate-integrity issue.

## Anti-patterns to avoid
- Treating time types, groups, accounts, balances, recorded time and evaluated time as interchangeable.
- Creating new concepts before checking whether an approved concept already covers the requirement.
- Merging concepts based on similar names alone.
- Adjusting balances before tracing the underlying policy, data and processing.
- Treating local variation as a naming problem when semantics differ.
- Changing historical behavior without explicit policy and audit review.
- Claiming hypothetical scenarios, metrics or results as personal achievements.
- Assuming product behavior is identical across releases and tenant configurations.

## Reusable practice worksheet
- **Business problem and policy context:**
- **My responsibility and decision rights:**
- **Concept and approved definition:**
- **Population and assignment rules:**
- **Dependencies and alternatives:**
- **Lifecycle and effective-date behavior:**
- **Exceptions and controls:**
- **Validation/reconciliation evidence:**
- **Verified result:**
- **SME challenge and response:**
- **Lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for the local business-first discovery context. This module provides interview-practice structures; it does not claim every described concept or relationship behaves identically across SAP SuccessFactors releases. Validate product-specific semantics against the relevant SAP documentation and actual tenant configuration.
