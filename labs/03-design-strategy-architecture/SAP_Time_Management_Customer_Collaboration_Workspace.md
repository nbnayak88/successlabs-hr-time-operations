# SAP SuccessFactors Time Management Customer Collaboration Workspace

## Purpose

Build a modern interactive web application in Google AI Studio that combines three SAP SuccessFactors Best Practice workbooks into one editable customer-requirement, case-study, learning, and collaboration workspace.

The three source workbooks are:

1. `SAP_BP_Workbook_TimeTracking`
2. `SAP_BP_Workbook_Timetracking_Time_Statements`
3. `SAP_BP_Workbook_ClockInClockOut`

Keep the three workbooks as separate selectable modules, while also providing an end-to-end view across all three.

The application should feel like a modern collaboration space combining the strengths of Miro, Notion, a product-discovery workspace, an SAP solution-design cockpit, and an interactive learning platform. It must not feel like an Excel viewer.

The central objective is:

> Help an SAP SuccessFactors consultant discover a customer's business requirement in simple language, walk through realistic case studies, ask the right questions, capture answers, map those answers to SAP concepts/configuration, validate the requirement, and produce downloadable project artifacts.

Everything created by the user must be editable.

---

## 1. Three Knowledge Modules

### Module 1 — SAP Time Tracking

Source: `SAP_BP_Workbook_TimeTracking`

Use its configuration topics, including:

- Job Information
- Employee Time Sheet
- Employee Time Valuation Result
- Time Management Configuration
- Time Account Type
- Time Type
- Allowance Type
- Time Type Group
- Time Valuation
- Time Recording Profile
- Grace Rounding Work Schedule
- Custom Rounding Lookup
- Custom Rounding Rules
- Time Records Filter
- Time Valuation Period
- Error Generation - Time Valuation
- Time Recording Admissibility
- Workflow
- Rules Formulae

### Module 2 — Time Tracking / Time Statements

Source: `SAP_BP_Workbook_Timetracking_Time_Statements`

Keep this as a distinct module.

Focus on:

- employee time-sheet experience
- time statements
- recorded time
- evaluated time
- approvals
- corrections
- business rules
- workflow
- time valuation
- employee/manager review

### Module 3 — Clock In / Clock Out

Source: `SAP_BP_Workbook_ClockInClockOut`

Important areas include:

- Time Event Types
- Clock In Clock Out Groups
- CICO Settings
- Time Event Derivation Rules
- Reasons For Manual Event
- Time Records Filter
- Time Valuation Period
- Error Generation - Time Valuation
- Time Recording Admissibility
- Workflow
- Rules Formulae

---

# 2. Core Consulting Philosophy

Never begin with SAP configuration terminology.

Always follow:

**Business Situation**
→ What is happening?

**Customer Requirement**
→ What does the customer want?

**Discovery Questions**
→ What must we ask?

**Customer Answers**
→ What does the customer tell us?

**Business Rule**
→ What rule has the customer actually decided?

**SAP Concept**
→ What SuccessFactors concept addresses it?

**Configuration**
→ Which configuration objects are relevant?

**Employee Journey**
→ What does the employee actually do?

**System Outcome**
→ What does the system produce?

**Exceptions**
→ What happens when the normal process fails?

**Validation**
→ How do we confirm the requirement with the customer?

Never turn an assumption into a customer requirement.

---

# 3. Application Navigation

Create a left navigation:

1. Home
2. Workbooks
3. Case Studies
4. Customer Journey
5. User Stories
6. Requirement Workshop
7. Configuration Map
8. Polls
9. Collaboration Room
10. Scratch Pad
11. Solution Design
12. Requirements Register
13. Decision Log
14. Open Questions
15. Test Scenarios
16. Downloads
17. Settings

---

# 4. Home Dashboard

Show three large selectable cards:

### Time Tracking
Understand how employee time is recorded, categorized, evaluated and processed.

### Time Statements
Understand how employees and managers review recorded and evaluated time.

### Clock In / Clock Out
Understand how time events become meaningful time records.

Each card should display:

- number of configuration topics
- number of case studies
- number of discovery questions
- number of user stories
- progress

Allow selecting:

- one workbook
- two workbooks
- all three

Provide:

**Explore End-to-End Journey**

---

# 5. End-to-End Journey

Create a visual flow:

Employee
→ Arrives at Work
→ Clock In
→ Time Event Captured
→ Event Interpreted
→ Time Type Determined
→ Time Recorded
→ Break / Additional Time
→ Clock Out
→ Time Valuation
→ Normal Time / Overtime / Other Result
→ Manager Review / Approval
→ Time Statement
→ Payroll / Reporting / Downstream Process

Every node must be clickable.

Each node opens:

- simple explanation
- technical explanation
- business purpose
- related workbook
- configuration objects
- case studies
- discovery questions
- user stories
- notes

---

# 6. Case Study Engine

This is the most important part of the application.

Create an editable Case Study Library.

Each case study contains:

- Title
- Business Situation
- Why the Customer Cares
- Customer Conversation
- Discovery Questions
- Customer Answers
- Requirement Decision
- Business Rule
- SAP Concept
- Configuration Mapping
- Employee Experience
- System Behavior
- Example Calculation
- Exceptions
- Validation Questions
- User Stories
- Acceptance Criteria
- Test Scenarios
- Status
- Notes

Statuses:

- Not Started
- Discovery
- Requirement Captured
- Configuration Designed
- Customer Validated
- Ready for Build
- Closed

Support:

- Add
- Edit
- Delete
- Duplicate
- Reorder

---

# 7. Customer Conversation Mode

For every case study, first explain the business scenario in simple language.

Example:

> Your employees normally work from 9:00 AM to 6:00 PM. One employee arrives at 8:55 AM and leaves at 7:00 PM. Before we configure the system, we need to understand how your organization wants to treat the early arrival, break, and additional working time.

Then provide discovery questions.

The consultant should be able to ask one question at a time.

Do not expose technical configuration too early.

---

# 8. Preloaded Case Studies

Create at least these realistic cases.

## Clock In / Clock Out

1. Employee clocks in at scheduled start
2. Employee clocks in early
3. Employee clocks in late
4. Employee forgets to clock in
5. Employee forgets to clock out
6. Employee takes a break
7. Employee works beyond scheduled hours
8. Employee works on a weekend
9. Employee works on a public holiday
10. Employee manually corrects a time event
11. Employee provides a reason for a manual correction
12. Different employee groups have different CICO behavior
13. Location capture is required
14. Location capture is not required
15. Multiple clock events need interpretation
16. A time event needs to derive a specific time type

## Time Tracking

17. Normal attendance
18. Overtime
19. Time Off in Lieu
20. Working Time Account
21. Different time types
22. Different time type groups
23. Time valuation threshold
24. Daily versus weekly valuation
25. Rounding
26. Grace period
27. Custom rounding
28. Time recording restriction
29. Historical correction
30. Manager approval
31. Error during time valuation
32. Different work schedules
33. Different employee populations
34. Allowance / premium condition

## Time Statements

35. Employee reviews time statement
36. Employee sees incorrect time
37. Employee requests correction
38. Manager reviews time
39. Approved versus unapproved time
40. Valuated versus recorded time
41. Overtime displayed to employee
42. Missing time
43. Time statement dispute
44. Payroll-relevant time result

All cases must be editable and duplicable.

---

# 9. Discovery Question Framework

For each scenario ask questions under these headings:

### Business Context
What business process are we supporting?

### Employee Population
Who is affected?

### Current Process
How is this done today?

### Business Rule
What determines the outcome?

### Exceptions
What happens when the normal process does not apply?

### Approval
Who approves?

### Compliance
Are there country/legal requirements?

### Payroll
Does the result affect payroll?

### Reporting
What needs to be visible?

### Future State
Do you expect the process to change?

Every question must have an editable customer-answer field.

---

# 10. Customer User Journey Builder

Create an editable drag-and-drop journey.

Each step has:

- Actor
- Action
- System Response
- Business Rule
- Pain Point
- Requirement
- SAP Mapping
- Notes

Allow:

- add
- edit
- delete
- duplicate
- reorder
- drag and drop

Example:

Employee
→ Open Time Recording
→ Clock In
→ Work
→ Break
→ Resume
→ Clock Out
→ System Calculates Time
→ Manager Reviews
→ Time Statement Updated
→ Payroll Result

---

# 11. User Stories

Create editable user stories.

Format:

### As a
Employee

### I want to
Clock in when I begin work

### So that
My working time is accurately recorded

Fields:

- Actor
- Action
- Business Value
- Acceptance Criteria
- Priority
- Related Case Study
- Related Configuration
- Status
- Notes

Roles:

- Employee
- Manager
- HR Administrator
- Time Administrator
- Payroll Administrator
- HR Business Partner
- System Administrator

---

# 12. Acceptance Criteria

Support Given / When / Then.

Example:

Given the employee has a valid work schedule

When the employee clocks in

Then the system records the clock-in event

And the event is associated with the employee

And the resulting time can participate in time processing.

Allow multiple acceptance criteria.

---

# 13. Poll System

Create an editable polling system.

Poll types:

- Single choice
- Multiple choice
- Yes / No
- Rating
- Ranking
- Free text

Example:

**How does your organization currently calculate overtime?**

Options:

- Daily
- Weekly
- Monthly
- Based on scheduled hours
- Other

Allow:

- create
- edit
- delete
- duplicate
- collect responses
- reset
- show results
- export

Use charts for results.

Do not hard-code results.

---

# 14. Collaboration Room

Create a workshop collaboration room.

### Left
Agenda

### Center
Interactive workshop canvas

### Right
Participants / Activity / Notes

Support:

- case-study discussion
- polls
- user stories
- journey mapping
- requirement capture
- sticky notes
- comments
- decisions
- open issues

Participant roles:

- Consultant
- Customer
- HR
- Payroll
- Manager
- Observer

Local/simulated participants are acceptable for MVP.

---

# 15. Scratch Pad / Sticky Notes

Create a free-form collaborative canvas.

Sticky note fields:

- Title
- Text
- Category
- Author
- Timestamp
- Tags

Categories:

- Requirement
- Question
- Decision
- Risk
- Assumption
- Issue
- Idea
- Follow-up

Allow:

- drag
- resize
- edit
- delete
- duplicate
- group
- tag
- filter

---

# 16. Configuration Map

Create an interactive visual relationship map.

### Clock In / Clock Out

Time Event Type
→ CICO Group
→ CICO Settings
→ Time Event Derivation Rule
→ Time Type
→ Time Recording
→ Time Valuation
→ Employee Time Valuation Result
→ Time Statement

### Time Tracking

Work Schedule
→ Time Recording Profile
→ Time Type
→ Time Type Group
→ Time Records Filter
→ Time Valuation
→ Valuation Result

### Time Statement

Recorded Time
→ Evaluated Time
→ Approval / Correction
→ Employee Review
→ Business / Payroll Result

Relationships must be editable.

---

# 17. Business Language / Consultant Language

Every technical concept must have a toggle:

**Business View | Consultant View**

Example:

### Business View

"This is the rule that tells the system what a clock event means."

### Consultant View

"This is the time event derivation configuration that determines how an event is interpreted and associated with the relevant time process."

Also provide:

**Explain Like a Customer**

and

**What Should I Ask?**

buttons.

---

# 18. Requirement Traceability

Create a complete traceability chain:

Requirement
→ Case Study
→ Customer Question
→ Customer Answer
→ Business Rule
→ User Story
→ Configuration Object
→ Acceptance Criteria
→ Test Scenario
→ Customer Sign-off

Allow navigation in both directions.

---

# 19. Requirements Register

Editable table with:

- Requirement ID
- Requirement
- Business Process
- Workbook
- Case Study
- User Story
- Priority
- Customer Decision
- SAP Concept
- Configuration Object
- Open Question
- Owner
- Status
- Target Date
- Notes

Support:

- search
- sort
- filter
- inline editing
- add
- delete
- duplicate
- export

---

# 20. Decision Log

Fields:

- Decision ID
- Date
- Topic
- Decision
- Rationale
- Customer
- Consultant
- Related Requirement
- Impact
- Status

Editable.

---

# 21. Open Questions Register

Fields:

- Question ID
- Question
- Why it matters
- Customer response
- Owner
- Due date
- Status
- Related case study

Statuses:

- Open
- Waiting for Customer
- Answered
- Closed

---

# 22. Test Scenario Builder

Turn every requirement into a business test.

Example:

### Test Scenario

Employee works 9 hours on a normal scheduled day.

Input:

Scheduled time = 8 hours

Actual time = 9 hours

Expected result:

8 hours normal

1 hour overtime

All values must be editable.

Fields:

- Test ID
- Scenario
- Preconditions
- Input
- Expected Result
- Actual Result
- Pass / Fail
- Tester
- Date
- Notes

---

# 23. Export Center

Everything created by the user must be downloadable.

Support:

### PDF
Customer Requirements Document

### Excel
Requirements Register

### CSV
Requirements / User Stories / Poll Results

### JSON
Complete workshop/project data

### Markdown
Case Studies / Requirements / User Stories

### Printable Workshop Summary

Exports should include:

- project information
- selected workbooks
- customer journey
- case studies
- questions
- answers
- decisions
- requirements
- user stories
- acceptance criteria
- configuration mapping
- test scenarios
- open issues
- poll results
- notes

---

# 24. Data Model

For MVP, do not require a backend.

Use:

- React state
- IndexedDB and/or localStorage

Data must survive refresh.

Entities:

- Workbook
- ConfigurationTopic
- CaseStudy
- DiscoveryQuestion
- CustomerAnswer
- BusinessRule
- UserJourney
- JourneyStep
- UserStory
- AcceptanceCriterion
- Requirement
- Decision
- OpenQuestion
- TestScenario
- Poll
- PollOption
- PollResponse
- StickyNote
- Workshop
- Participant
- Comment

Keep architecture backend-ready.

Do not require Supabase for MVP.

Do not require authentication for MVP.

---

# 25. Import

Support importing:

- JSON
- CSV
- Markdown

Design the architecture so future workbook-derived datasets can also be imported.

---

# 26. Global Search

Search across:

- workbooks
- configuration topics
- case studies
- questions
- answers
- user stories
- requirements
- notes
- decisions
- test cases

Show source and navigation target.

---

# 27. Filtering

Filter by:

- Workbook
- Business Process
- Case Study
- Employee
- Manager
- Payroll
- Configuration Object
- Status
- Priority
- Country
- Workshop

---

# 28. UI / UX

Create a premium modern enterprise interface.

Design language:

- clean
- modern
- spacious
- professional
- collaborative
- slightly futuristic
- enterprise-grade
- restrained colors
- not an Excel clone
- not a simple CRUD dashboard
- not a direct SAP Fiori imitation

Use:

- cards
- tabs
- chips
- drawers
- modals
- breadcrumbs
- timelines
- flow diagrams
- interactive canvas
- tables
- contextual panels
- command palette

Desktop-first but responsive for tablet/mobile.

---

# 29. Dashboard Metrics

Show:

- Total Case Studies
- Requirements Captured
- Open Questions
- Decisions Made
- User Stories
- Test Scenarios
- Poll Participation
- Workshop Progress

Use charts where useful.

---

# 30. AI Assistant

Add an AI assistant panel.

It should help with:

### Explanation

"Explain Time Valuation to an HR manager."

### Discovery

"What should I ask the customer before configuring overtime?"

### User Stories

"Turn these answers into a user story."

### Testing

"Create test scenarios from this requirement."

### Customer Communication

"Explain this configuration to a customer."

The assistant must distinguish:

- source knowledge
- customer-provided information
- assumptions

Never present assumptions as customer decisions.

---

# 31. AI Case Study Generator

Provide:

**+ New Case Study**

Inputs:

- Title
- Business Problem
- Actors
- Business Process
- Customer Context
- Questions
- Expected Decisions
- SAP Concepts
- Configuration Mapping

AI can generate a draft.

Everything remains editable.

---

# 32. Customer Workshop Mode

When activated, initially hide technical details.

Show only:

1. Business Scenario
2. Customer Question
3. Customer Answer
4. Decision
5. Next Question

Provide:

**Reveal SAP Configuration**

This allows the consultant to conduct a natural business conversation without overwhelming the customer.

---

# 33. Consultant Mode

Show:

- business requirement
- SAP concept
- configuration object
- dependencies
- technical notes
- rules
- workflow
- valuation
- test scenario

---

# 34. Three-Workbook Cross Mapping

Create an editable matrix:

| Business Requirement | Time Tracking | Time Statements | Clock In/Out |
|---|---|---|---|
| Capture working time | | | |
| Clock event | | | |
| Time valuation | | | |
| Time result | | | |
| Employee review | | | |
| Manual event correction | | | |
| Workflow | | | |

Do not invent relationships. Populate only from known workbook/configuration relationships and allow the consultant to edit them.

---

# 35. Requirement Quality Check

Before a requirement is marked complete, check whether:

- business problem is defined
- employee population is defined
- business rule is explicit
- exceptions are documented
- approval is defined
- payroll impact is understood
- relevant time type is identified
- valuation behavior is understood
- customer decision is captured
- acceptance criterion exists
- test scenario exists
- customer validation is recorded

Show:

**Complete**

or

**Needs Information**

Do not automatically decide the business requirement.

---

# 36. Project Management

Allow multiple projects/workshops.

Example:

**ABC Manufacturing — Time Management Discovery**

Save:

- project details
- selected modules
- case studies
- answers
- requirements
- decisions
- polls
- sticky notes
- user stories
- tests

Actions:

- New Project
- Save
- Duplicate
- Rename
- Archive
- Export
- Import

---

# 37. Demo Project

Preload:

**ABC Manufacturing — Time Management Discovery**

Include:

- 3 case studies
- 10 discovery questions
- 5 user stories
- 5 requirements
- 3 decisions
- 3 open questions
- 5 test scenarios
- 1 poll
- 10 sticky notes
- end-to-end journey

All demo data must be editable/deletable.

---

# 38. Important End-to-End Case Study

Preload:

## Employee Works Beyond Scheduled Hours

Scenario:

Employee is scheduled 9:00 AM–6:00 PM.

Employee clocks in at 8:55 AM.

Employee takes a 1-hour lunch break.

Employee clocks out at 7:00 PM.

The application must NOT assume whether the employee receives overtime.

Ask:

1. What is the planned working duration?
2. Is the 8:55 AM arrival considered working time?
3. Is there a grace period?
4. Is lunch recorded as a break?
5. Is lunch automatically deducted?
6. Must the employee clock out for lunch?
7. Is 7:00 PM considered overtime?
8. Does overtime begin after planned hours?
9. Is overtime calculated daily or weekly?
10. Does overtime require manager approval?
11. Is overtime paid?
12. Can overtime become Time Off in Lieu?
13. Do different employee groups have different rules?
14. Are weekends and holidays treated differently?

Answers should drive the subsequent business rule, SAP mapping, user story, acceptance criteria, and test scenario.

---

# 39. UX Principle

The application must continuously help the consultant answer:

### What is the customer trying to achieve?

### What should I ask?

### What did the customer decide?

### How does that translate into SAP?

This is the central design philosophy.

---

# 40. Component Architecture

Use reusable components:

- AppShell
- Sidebar
- Header
- WorkbookSelector
- CaseStudyCard
- CaseStudyEditor
- DiscoveryQuestion
- AnswerEditor
- UserJourney
- JourneyStep
- UserStoryCard
- AcceptanceCriteriaEditor
- RequirementTable
- DecisionLog
- OpenQuestionTable
- PollBuilder
- PollResults
- CollaborationRoom
- StickyCanvas
- ConfigurationMap
- ConfigurationDetail
- TestScenarioBuilder
- ExportCenter
- AIAssistant
- CustomerMode
- ConsultantMode
- SearchCommand
- ProjectSwitcher

---

# 41. Technical Requirements

Use:

- React
- TypeScript
- modern component architecture
- reusable components
- strongly typed data models
- responsive CSS
- IndexedDB/localStorage
- modular services

Keep the application backend-ready.

Do not introduce unnecessary infrastructure.

---

# 42. Build Strategy

Build the MVP in stages.

### Phase 1
Application shell, workbook selector, dashboard and data model.

### Phase 2
Case study engine and discovery workflow.

### Phase 3
Customer journey and user stories.

### Phase 4
Collaboration room, polls and sticky notes.

### Phase 5
Configuration mapping and traceability.

### Phase 6
Test scenario builder.

### Phase 7
AI assistant and AI case-study generation.

### Phase 8
Export/import.

At every stage keep existing functionality working.

---

# 43. Final Success Criteria

A consultant must be able to:

1. Select any workbook.
2. Select multiple workbooks.
3. Select an end-to-end journey.
4. Select a case study.
5. Understand it in plain language.
6. Ask structured customer questions.
7. Capture customer answers.
8. Build a customer journey.
9. Create user stories.
10. Run a poll.
11. Collaborate with sticky notes.
12. Capture decisions.
13. Track open questions.
14. Map requirements to SAP concepts.
15. Map concepts to configuration.
16. Create acceptance criteria.
17. Create test scenarios.
18. Validate requirements.
19. Edit everything.
20. Save the workshop.
21. Export the complete result.

The application should feel like a **living customer workshop and solution-design environment**, not a static training repository.

Build the MVP now. Prioritize the customer workshop experience, case studies, discovery questions, editability, traceability and downloads over decorative features.
