# Interview Stream 01 — Time Management Discovery & Requirements

## Outcome
Demonstrate that you can turn an ambiguous workforce-time policy into a validated, testable requirement before discussing SAP configuration.

## Scope
This stream covers discovery, employee populations, current-state pain, decision ownership, policy variation, assumptions, and acceptance criteria. Detailed architecture trade-offs belong in Stream 02; detailed configuration and time valuation belong in Streams 03–12.

## Reusable answer spine
**Situation:** Describe the workforce, operating model, country/site variation and process failure using only facts you can defend.  
**Task:** State your role in clarifying the requirement and the decision that had to be made.  
**Action:** Map the current journey; segment employee populations; ask about normal and exceptional cases; distinguish policy from assumptions; record decisions, owners and open questions; translate agreed policy into acceptance criteria; validate the interpretation with the process owner.  
**Result:** Use verified evidence such as signed-off requirements, reduced unresolved questions, approved scenarios or successful UAT—not invented percentages.  
**SME follow-up:** Explain what evidence supports the policy, how conflicting answers were resolved, and what you would do if the customer could not decide.

## 20 STAR scenario prompts

Each prompt is a rehearsal scenario, not a claim about your personal experience. Build the response with the answer spine above and insert only evidence from your actual work.

1. A global customer gives one statement for overtime, but sites apply different local practices. How did you discover the real rule and identify policy owners?
2. Employees claim that recorded hours are wrong, while managers say the time statement is correct. How did you separate perception, process, and data questions?
3. The customer requests “automatic overtime” without defining thresholds, eligible populations, or approval. How did you turn the phrase into testable requirements?
4. A shift-based workforce and office employees have different recording needs. How did you segment personas and avoid designing for an average employee?
5. A policy owner says early arrival should count, while operations says it should not. How did you document the decision and keep assumptions out of the design?
6. Payroll needs a reliable period result, but managers prioritize real-time visibility. How did you discover the competing timing and control requirements?
7. The existing process uses spreadsheets and manual adjustments. How did you identify what should be preserved, retired, or redesigned?
8. A union or local agreement may change break and overtime treatment. How did you identify authoritative sources and prevent unsupported assumptions?
9. The customer wants a single global template. How did you test whether country, employee-group, and site variations require controlled exceptions?
10. A requirement says “round time fairly.” How did you elicit the exact rounding unit, direction, boundaries, exceptions, and approval?
11. Managers want to edit records directly, while the control owner needs traceability. How did you discover the permitted correction path and evidence needs?
12. The employee population includes mobile workers with unreliable connectivity. How did you capture offline, delayed-event, and exception requirements without promising unsupported capability?
13. Stakeholders disagree on whether an absent punch should be inferred or corrected by the employee. How did you establish policy and accountability?
14. The customer gives sample cases but no expected results. How did you facilitate a decision table and obtain sign-off?
15. A new time process must work for employees with different schedules and recording profiles. How did you define the segmentation and eligibility questions?
16. A business sponsor asks for dashboards before agreeing metric definitions. How did you clarify what “missing time,” “overtime,” and “exception” mean?
17. An acquired entity has a different time policy and legacy data. How did you discover transition requirements and define what must be migrated?
18. The customer changes a requirement after UAT begins. How did you assess impact, update traceability, and secure a decision on schedule or scope?
19. The configuration team says a requirement is standard, but the process owner describes an exception. How did you validate fit-to-standard without prematurely committing to customization?
20. A critical question remains unanswered near design sign-off. How did you expose the risk, define options, and obtain a documented decision or conditional approval?

## SME probe bank
- How did you distinguish an actual policy from a workaround used by one team?
- Which employee populations and edge cases did you explicitly model?
- What artifact proves the process owner approved the rule?
- How did you manage an unanswered question that blocked configuration or testing?
- How did you turn the requirement into Given/When/Then acceptance criteria?
- What would make you challenge a customer request rather than immediately configure it?
- How did you prevent payroll dependencies from being discovered only during testing?
- How would the discovery change for mobile, shift, part-time, and cross-midnight populations?

## Rapid-fire questions
1. What is the difference between a business requirement and a solution assumption?
2. Why is employee segmentation important in time management?
3. What makes a time policy testable?
4. What should an assumptions register contain?
5. Who should approve a policy decision?
6. Why capture normal and exceptional cases?
7. How do you handle conflicting stakeholder answers?
8. What is requirement traceability?
9. When should a question remain open rather than be guessed?
10. What evidence should exist before design sign-off?

## Quality rubric (0–2 each)
- Business context, workforce population and impact are explicit.
- Candidate's personal responsibility is clear.
- Discovery questions expose rules and exceptions.
- Decision, assumption and risk are separated.
- Outcome is evidenced and the SME probe is answered with sound judgment.

**Target:** 8/10 or better, with no invented experience or unsupported product claim.

## Common anti-patterns
- Starting with configuration objects before understanding the policy.
- Treating one site's practice as a global requirement.
- Inventing time, overtime, break, or compliance rules.
- Claiming measurable benefits without evidence.
- Saying “we configured it” without explaining your own decisions or validation.

## Evidence checklist
Bring sanitized examples, where available: discovery questionnaire, process map, requirements register, decision log, assumptions/open-question log, acceptance criteria, traceability matrix, and UAT sign-off.

## Source and version verification
Use the repository's [Time Management Customer Collaboration Workspace](../03-design-strategy-architecture/SAP_Time_Management_Customer_Collaboration_Workspace.md) as the business-first discovery reference. Verify all product-specific behavior against the applicable SAP SuccessFactors edition, release, configuration workbook and customer design. A workbook topic is a discovery aid, not proof that every customer scenario is supported without configuration or constraints.
