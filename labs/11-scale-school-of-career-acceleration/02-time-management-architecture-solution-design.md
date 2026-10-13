# Interview Stream 02 — Time Management Architecture & Solution Design

## Outcome
Demonstrate that you can translate agreed workforce-time policies into a supportable end-to-end SAP SuccessFactors solution, explain why the design fits the business, and prove that the design handles normal cases, exceptions, integration dependencies and change.

## Scope boundary
This stream covers end-to-end solution design, fit-to-standard, capability mapping, configuration boundaries, non-functional needs, design alternatives, maintainability and architecture rationale. Detailed discovery techniques belong in Stream 01; specific work schedules, profiles, time types, time valuation, and CICO mechanics belong in Streams 03–12.

## STAR answer standard
- **Situation:** Describe the workforce, operating model, business problem, constraints and impact using facts you can defend.
- **Task:** Clarify your personal accountability, decision rights and delivery boundaries.
- **Action:** Explain how you compared options, mapped business requirements to capabilities, evaluated standard functionality, identified dependencies and exceptions, recorded decisions, and validated the proposed design.
- **Result:** Use verified evidence such as approved design decisions, signed-off process maps, test results, resolved design gaps, or successful UAT. Never invent project outcomes or metrics.
- **SME probe:** Be ready to justify the trade-off, explain an edge case, identify a rejected alternative and show the evidence behind your conclusion.
- **Version check:** Verify product behavior against the edition/release and the actual configuration in scope.

## 20 fully structured STAR practice scenarios

These are model answer structures for practice—not claims about your personal work history. Replace bracketed context with your real experience. If you have not delivered the scenario, label it as a lab, design exercise or proposed approach. Any sample result must be supported by evidence before you present it as a real achievement.

### 1. Designing a fit-to-standard solution when the business asks for customization
**Situation:** A customer requests a bespoke time process because the legacy system handles a particular exception differently. The request is described as a requirement, but its business purpose and frequency are not yet clear.

**Task:** Establish whether standard capability can satisfy the actual business outcome, and make the trade-off transparent before committing to a custom design.

**Action:**
1. Separate the desired outcome from the requested solution.
2. Map the current process, employee population, policy rule, exception frequency and control requirements.
3. Demonstrate the relevant standard capability using a representative scenario and the applicable product release.
4. Compare standard configuration, a controlled process change, and any genuinely necessary extension against fit, risk, supportability, upgrade impact and testing effort.
5. Record the gap, evidence, decision owner and approval; keep assumptions visible until confirmed.

**Result:** The defensible result is a documented fit-to-standard decision with a customer-approved rationale and traceable test cases. State any time or cost benefit only if measured.

**SME probe:** What if the customer insists on customization?  
**Answer outline:** Explain the options and consequences, verify that the gap is real, quantify impact where evidence exists, document the risk, and route the decision through architecture and business governance. Do not imply that a consultant can unilaterally waive a valid legal or contractual need.

### 2. Designing a global template with legitimate local variation
**Situation:** A multinational organization wants one global time-management template, but employee groups and countries have different schedules, policies and approval practices.

**Task:** Preserve global consistency without erasing approved local variation.

**Action:**
1. Establish global design principles and non-negotiable controls.
2. Build a variation matrix by country, employee group, work pattern and policy owner.
3. Classify each difference as a legal/policy requirement, a business preference, a legacy habit or an unresolved question.
4. Map differences to standard configuration options where supported and verify their interactions.
5. Define ownership, documentation, regression scope and approval criteria for each exception.

**Result:** Present a governed template and variation register, backed by stakeholder approval and representative test coverage. Avoid claiming every country can be handled by a single configuration without validation.

**SME probe:** How do you stop local exceptions from multiplying?  
**Answer outline:** Require an evidenced business or regulatory reason, an accountable owner, impact assessment, reusable design where possible, and periodic review of exceptions.

### 3. Balancing a fast workaround against downstream risk
**Situation:** Operations asks for a quick manual workaround to get time results ready, while the design team is concerned that it may weaken traceability or create inconsistent downstream data.

**Task:** Help stakeholders make a time-bound decision without hiding control or payroll-relevant risks.

**Action:**
1. Establish the immediate business impact and deadline.
2. Identify which records and populations are affected and whether the workaround changes source data, evaluated results or only presentation.
3. Compare safe recovery options, including controlled manual correction, reprocessing, or a temporary process with reconciliation.
4. Define approvals, access restrictions, logging, validation and an expiry/exit condition.
5. Communicate residual risk to the accountable business and technical owners.

**Result:** Evidence should show an approved containment path, reconciled affected records and a tracked permanent fix—not merely that the deadline was met.

**SME probe:** When would you reject the workaround?  
**Answer outline:** If it bypasses mandatory controls, creates an untraceable result, violates a verified policy or makes downstream outputs unreliable, escalate and propose a safer alternative.

### 4. Choosing between two viable configuration designs
**Situation:** Two standard design options appear to meet the requirement, but they differ in maintainability, flexibility and testing complexity.

**Task:** Recommend an option based on explicit criteria rather than personal preference.

**Action:**
1. Confirm the business rule and acceptance criteria.
2. Define criteria such as functional fit, supportability, data consistency, configuration complexity, performance, auditability and change impact.
3. Build a small decision matrix and test representative normal, negative and boundary scenarios.
4. Check dependencies and release-specific behavior in the relevant documentation or test environment.
5. Review the recommendation with the process owner, technical lead and support team; record why the alternative was rejected.

**Result:** A reviewable architecture decision record and evidence from scenario validation support the recommendation.

**SME probe:** What if stakeholders disagree with your scoring?  
**Answer outline:** Make assumptions and weights visible, invite challenge, distinguish facts from judgments, and obtain a decision from the accountable owner.

### 5. Finding a critical boundary case late in design
**Situation:** During a design walkthrough, a cross-midnight shift or a period boundary reveals that the proposed process may behave differently from the normal daytime scenario.

**Task:** Assess whether the gap is material and prevent an incomplete design from moving forward unnoticed.

**Action:**
1. Reproduce the boundary case with explicit inputs and expected business behavior.
2. Trace the relevant schedule, time-recording, valuation and downstream dependencies without assuming which component is responsible.
3. Assess affected employee groups, periods, reports and interfaces.
4. Update the design, decision log, requirements traceability and negative/boundary test set.
5. Obtain approval of the corrected interpretation before closing the design gap.

**Result:** Evidence includes an agreed expected result, updated design and passing regression test. Report defect or schedule impact only from actual records.

**SME probe:** How do you know this is a design gap rather than a configuration defect?  
**Answer outline:** Compare the approved requirement, design specification, configured behavior and test data; classify the gap based on evidence rather than intuition.

### 6. Investigating an unexpected result in a design prototype
**Situation:** A prototype produces a time result that differs from the business expectation, and stakeholders immediately suggest changing a rule.

**Task:** Find the cause before changing configuration and protect the integrity of the design.

**Action:**
1. Preserve the test inputs, employee attributes, schedule, time records, effective dates and system output.
2. Confirm the expected result against the approved policy and acceptance criterion.
3. Reproduce the issue with a minimal scenario and compare it with a known-good case.
4. Trace the processing chain and dependencies; inspect the relevant configuration and product behavior.
5. Change one justified factor at a time, rerun positive and negative cases, and document the root cause and regression scope.

**Result:** A repeatable defect record, validated correction and regression evidence are stronger than an unsupported claim that the issue was fixed.

**SME probe:** What if the expected result was never approved?  
**Answer outline:** Stop treating it as a defect until the policy owner confirms the intended behavior; record the ambiguity and avoid encoding a guess as a rule.

### 7. Resolving disagreement between policy and operations
**Situation:** The policy owner and operations lead disagree about how a time exception should be handled, and each believes the other owns the decision.

**Task:** Keep architecture work moving without silently choosing a policy.

**Action:**
1. Write the conflicting interpretations side by side.
2. Identify evidence needed: policy document, collective agreement, operational control or formal decision.
3. Explain the system and downstream consequences of each option in business language.
4. Identify the accountable decision owner and timebox the decision where appropriate.
5. Record the decision, rationale, impact, open risks and tests that must change.

**Result:** A traceable decision or explicitly managed open issue enables design governance. Do not report “alignment” unless the owner actually approved the outcome.

**SME probe:** What if the deadline arrives before the decision?  
**Answer outline:** Escalate the dependency, present safe options and schedule/risk impact, and seek formal conditional approval or a scope decision. Do not invent a policy.

### 8. Deciding whether a manual exception should be automated
**Situation:** A team uses a spreadsheet and manual adjustment to handle an exception that is not covered by its normal time process.

**Task:** Decide whether automation is justified and define the control requirements.

**Action:**
1. Measure frequency, effort, error risk, business impact and exception diversity from available evidence.
2. Understand why the exception exists and whether the underlying policy or upstream data should be corrected first.
3. Compare standard configuration, controlled manual processing and an extension or integration only where justified.
4. Evaluate auditability, ownership, failure handling, testing, support effort and change risk.
5. Define monitoring, manual fallback and success criteria for a pilot if automation is selected.

**Result:** A documented decision grounded in actual exception data and controls; if piloted, use observed results rather than estimated savings presented as facts.

**SME probe:** Why not automate every repetitive task?  
**Answer outline:** Automation can scale an incorrect policy, obscure exceptions or create brittle dependencies. First stabilize the rule and define controls.

### 9. Designing different behavior for different employee groups
**Situation:** Salaried office employees, hourly workers and shift-based employees need different time-recording behavior, but the customer also wants a maintainable common design.

**Task:** Define the smallest supportable set of variants that meets approved requirements.

**Action:**
1. Create an employee-population matrix based on policy-relevant attributes rather than job-title assumptions.
2. Identify common requirements and meaningful differences in schedule, recording method, eligibility, approval and valuation.
3. Map each variant to supported configuration and assignment mechanisms after release verification.
4. Define default behavior, exception handling and controls against incorrect assignment.
5. Test representative employees from each population and regression-test shared behavior.

**Result:** An approved population-to-design matrix, configuration mapping and test evidence demonstrate controlled variation.

**SME probe:** How would you handle a newly acquired employee population?  
**Answer outline:** Assess the population against the matrix, identify true gaps, assign an owner, validate policy and avoid creating a new variant until evidence justifies it.

### 10. Verifying a capability before promising it to the customer
**Situation:** A stakeholder says the product supports a requested time behavior, but the team has not verified the relevant edition, release or configuration dependency.

**Task:** Provide a reliable capability assessment before the design baseline is approved.

**Action:**
1. Phrase the requested behavior as a testable business outcome.
2. Search the applicable SAP product documentation and relevant best-practice workbook, checking edition and release.
3. Validate prerequisites, limitations, supported scope and dependencies in an appropriate test tenant or authoritative source.
4. Distinguish standard capability, configuration, integration, workaround and unverified assumption.
5. Communicate the evidence and any uncertainty; update the solution decision and estimates only after validation.

**Result:** A qualified capability statement and documented evidence protect the customer from an unsupported commitment.

**SME probe:** What if documentation and tenant behavior appear inconsistent?  
**Answer outline:** Confirm release and tenant configuration, reproduce the case, consult the relevant product support channel or implementation guidance, and record the unresolved issue. Do not generalize from one test.

### 11. Supporting country and collective-agreement variation
**Situation:** The design must support multiple countries and employee groups, and break, overtime or working-time rules may be influenced by local law or collective agreements.

**Task:** Design a solution that uses authoritative policy inputs and does not treat an illustrative rule as universal.

**Action:**
1. Identify legal, labor-relations and business policy owners.
2. Gather authoritative, current sources and confirm the effective date and covered population.
3. Translate approved rules into a country/population variation matrix and identify where expert review is required.
4. Verify whether the product supports each required behavior and identify configuration or process gaps.
5. Design tests for boundaries, exceptions, effective dates and changes to the governing policy.

**Result:** A signed-off policy-to-design traceability set and reviewed test evidence. Do not present the design as legal advice.

**SME probe:** Who owns the final interpretation?  
**Answer outline:** The authorized legal, labor-relations or policy owner—not the technical consultant. The consultant translates approved decisions into system behavior and makes limitations visible.

### 12. Resolving disagreement between a time result and a downstream consumer
**Situation:** A downstream system interprets a time result differently from the source process, causing a mismatch in a report or payroll-relevant hand-off.

**Task:** Establish a shared end-to-end contract and clarify ownership across system boundaries.

**Action:**
1. Trace a sample record from source event through evaluated result to the receiving system.
2. Compare identifiers, dates, units, status semantics, mapping rules, timing and error handling.
3. Confirm which system is authoritative for each data element and who owns the mapping.
4. Agree retry, duplicate handling, reconciliation and exception ownership.
5. Test normal, correction, late-arriving and rejected records end to end.

**Result:** Approved mapping documentation, reconciliation evidence and clear support ownership show the architecture is controlled.

**SME probe:** How do you avoid “fixing” the wrong system?  
**Answer outline:** Follow the record across boundaries and compare each transformation with the contract and source-of-truth rule before assigning root cause.

### 13. Designing analytics when a metric has no agreed definition
**Situation:** Leaders ask for an overtime or missing-time dashboard, but teams use different definitions and filters.

**Task:** Prevent misleading reporting by establishing business semantics before choosing the visualization.

**Action:**
1. Ask what decision the metric should support and who owns it.
2. Define numerator, denominator, time window, exclusions, population, time zone and treatment of corrections.
3. Identify authoritative source fields and the difference between recorded and evaluated time.
4. Validate calculations against representative records and agreed examples.
5. Document lineage, refresh timing, access controls and change governance.

**Result:** A metric dictionary and reconciled sample report provide evidence that stakeholders share the same meaning.

**SME probe:** What if executives demand a number before definitions are agreed?  
**Answer outline:** Provide a clearly labeled provisional view only if safe and useful, disclose assumptions, and do not present it as an official comparable KPI.

### 14. Handling a late design change near a sprint or cutover
**Situation:** A policy change arrives after design approval and near a planned release or cutover.

**Task:** Evaluate the change objectively and help the decision owner understand consequences.

**Action:**
1. Record the changed requirement and reason.
2. Trace impacts across configuration, employee populations, interfaces, migration, security, tests, training and support.
3. Compare implementing now, deferring, or using a controlled interim process.
4. Assess the risks and test/regression effort using actual delivery evidence.
5. Obtain formal approval, update the baseline and communicate the decision to all affected teams.

**Result:** A controlled change record and updated release plan demonstrate governance. Avoid claiming the schedule was protected unless it was.

**SME probe:** What if the change is legally mandatory?  
**Answer outline:** Escalate urgency and compliance exposure, involve the authorized policy/legal owner, assess safe implementation options and formal go/no-go criteria; do not treat legal obligations as optional scope preferences.

### 15. Designing out a recurring support issue
**Situation:** The support team repeatedly resolves similar time-processing errors through manual intervention.

**Task:** Determine whether the architecture, configuration, data quality, user process or monitoring design is allowing recurrence.

**Action:**
1. Categorize incidents by cause, population, trigger and recurrence using support evidence.
2. Separate immediate recovery from root-cause elimination.
3. Trace the relevant upstream data, configuration, exception path and downstream effects.
4. Compare prevention options such as validation, better error guidance, controlled configuration, monitoring or process change.
5. Add regression tests, ownership, runbook updates and a measure to detect recurrence.

**Result:** Root-cause evidence, a preventive action and a monitoring plan demonstrate improvement; use actual incident trends to quantify it.

**SME probe:** How do you know the issue is truly resolved?  
**Answer outline:** Define a monitored observation window, validate the original and adjacent scenarios, review recurrence evidence, and keep rollback/escalation criteria.

### 16. Designing least-privilege access and auditability
**Situation:** Managers need visibility into their team's time, administrators need broader operational access, and audit stakeholders require traceable corrections.

**Task:** Design access and control requirements without overexposing employee data or blocking legitimate work.

**Action:**
1. Map roles to business tasks and data scope.
2. Apply least privilege and separation of duties where applicable.
3. Validate view, edit, approve and correction permissions with representative users.
4. Check audit requirements, sensitive data exposure, delegation and emergency access.
5. Include positive and negative access tests, periodic review and an exception process.

**Result:** An approved role matrix and access-test evidence support the design.

**SME probe:** What if a manager needs temporary access outside their normal scope?  
**Answer outline:** Use the approved delegation or exception mechanism, restrict scope and duration, record authorization, and verify removal. Do not grant broad permanent access for convenience.

### 17. Explaining a technical design to a skeptical customer
**Situation:** A customer rejects a proposed time design because the configuration terms are unfamiliar and they believe the solution will not match employee reality.

**Task:** Explain the design in business language and test whether the concern is a real requirement gap.

**Action:**
1. Restate the employee journey and intended business outcome without technical jargon.
2. Walk through a representative normal case and one exception using agreed inputs.
3. Show how the business rule maps to system behavior, including what is not supported or remains manual.
4. Invite the customer to challenge the expected result and record changes or open questions.
5. Update acceptance criteria and design decisions only after the process owner confirms the interpretation.

**Result:** Evidence is a validated walkthrough, recorded decision and agreed test cases—not simply a meeting that ended without objections.

**SME probe:** What if the customer says “the system should just know”?  
**Answer outline:** Explain which policy input or event is missing, give concrete alternatives, and ask the owner to choose the intended rule rather than concealing ambiguity behind automation.

### 18. Responding to inconsistent data during a mock migration
**Situation:** A mock migration reveals inconsistent employee time data or balances, and the team cannot reconcile all source totals.

**Task:** Design a safe migration decision with clear data ownership and cutover criteria.

**Action:**
1. Classify records by source, data type, period, employee population and error category.
2. Agree source-of-truth rules and distinguish data defects from expected legacy differences.
3. Define cleansing, transformation, rejected-record handling and reconciliation controls.
4. Test representative records, opening balances and downstream dependencies with business owners.
5. Establish thresholds, sign-off, unresolved-risk treatment and go/no-go criteria before production load.

**Result:** Reconciliation reports, accepted exceptions and a documented cutover decision provide evidence of readiness.

**SME probe:** Would you load first and reconcile later?  
**Answer outline:** Only if a formally approved risk-based strategy allows it and controls preserve integrity. Material unexplained differences in critical records should trigger escalation and a go/no-go decision.

### 19. Designing transparency between recorded and evaluated time
**Situation:** Employees see a recorded duration that differs from the evaluated result and assume the system has lost time.

**Task:** Make the result explainable without changing or obscuring the underlying policy.

**Action:**
1. Trace the sample from raw recorded time to evaluated result.
2. Identify applicable breaks, rounding, valuation thresholds, schedule rules, corrections and errors.
3. Verify that the intended behavior matches the approved requirement.
4. Improve employee-facing explanation, statement visibility or support guidance within supported product capability.
5. Test normal and disputed cases and establish a correction/escalation path.

**Result:** A validated explanation, test evidence and an agreed dispute process demonstrate improved transparency. Quantify user impact only when measured.

**SME probe:** What if the evaluated result is technically correct but the policy is unpopular?  
**Answer outline:** Separate technical correctness from policy acceptability, show the evidence, refer the policy decision to its owner and change system behavior only after approval.

### 20. Defending the final design in an architecture review
**Situation:** A skeptical subject-matter expert challenges the proposed design, questioning assumptions, exception handling, supportability and downstream effects.

**Task:** Defend the recommendation transparently and identify where the evidence is incomplete.

**Action:**
1. Summarize the business outcome, requirements, constraints and non-functional needs.
2. Show the capability map, end-to-end process, configuration boundaries and key dependencies.
3. Present alternatives and explain the criteria behind the selected option.
4. Walk through representative positive, negative, boundary, correction and integration scenarios.
5. State product/version evidence, residual risks, open decisions, operational ownership and rollback or mitigation plans.
6. Record review feedback and update the decision log and traceability baseline.

**Result:** An approved design decision, explicit conditions and a testable delivery plan are the credible outcome. Approval may be conditional; do not portray unresolved risk as closed.

**SME probe:** What would cause you to reverse your recommendation?  
**Answer outline:** New authoritative policy, verified product limitation, failed acceptance test, unacceptable risk, materially changed constraints or stronger evidence for an alternative should trigger reassessment.

## Architecture decision checklist
Before design sign-off, confirm:
- The business outcome and acceptance criteria are approved.
- Employee populations and legitimate variants are understood.
- Standard capability and release-specific limitations are verified.
- Time Off, Time Tracking, CICO, time statements and payroll dependencies are not conflated.
- Normal, negative, boundary, correction and failure cases are covered.
- Data ownership, access, auditability, integration and operational support are addressed.
- Alternatives, assumptions, risks, owners and decisions are documented.
- Each requirement traces to design, configuration, acceptance criteria and tests.

## SME follow-up bank
- What product/version and source support the behavior you described?
- Which upstream dependency has the greatest impact on the design?
- What happens when data is missing, corrected late or crosses a period boundary?
- What alternative did you reject, and what evidence informed that decision?
- How did you prove the design matched the approved business rule?
- What is the audit trail and who is authorized to correct the record?
- How did you manage country, employee-group or schedule variation?
- What was your individual contribution versus the team's contribution?
- Which residual risk did you communicate, and to whom?
- What evidence would make you revisit the architecture decision?

## Rapid-fire revision
1. What is fit-to-standard, and what is it not?
2. What belongs in an architecture decision record?
3. How do you distinguish a product limitation from a configuration gap?
4. Why should design include negative and boundary scenarios?
5. How do you control local variation in a global template?
6. Why must recorded and evaluated time be distinguished?
7. What is the difference between an assumption and a decision?
8. How do you validate a downstream mapping?
9. What does least privilege mean for time data?
10. What evidence is sufficient to recommend design sign-off?

## Scoring rubric (0–2 per dimension)
1. Business context and impact are explicit.
2. Personal accountability is clear.
3. Technical concepts are accurate and appropriately qualified.
4. Alternatives, dependencies, exceptions and validation are explained.
5. Results are evidence-backed and SME probes show sound judgment.

**Target:** 8/10 or better, with no critical accuracy, compliance or candidate-integrity issue.

## Anti-patterns to avoid
- Starting with configuration names before clarifying the business outcome.
- Treating a stakeholder preference as a legal or policy requirement without verification.
- Assuming standard capability without checking edition, release and configuration.
- Designing only for the normal case.
- Claiming an architecture decision was successful without test or approval evidence.
- Inventing metrics, client examples or personal ownership.
- Conflating time recording, valuation, time off, statements and payroll processing.

## Reusable practice worksheet
- **One-sentence business problem:**
- **My role and decision authority:**
- **Approved requirement and constraints:**
- **Options considered:**
- **Chosen design and rationale:**
- **Dependencies and exceptions:**
- **How I validated the design:**
- **Verified result and evidence:**
- **SME challenge and answer:**
- **Residual risk and lesson learned:**

## Source notes
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) for business-first discovery, the three-workbook framing (Time Tracking, Time Statements, Clock In/Clock Out), and the principle that assumptions must not be presented as customer decisions. This repository context is not a substitute for release-specific SAP documentation or actual project evidence.
