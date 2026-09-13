# AI Workflow Specification Template

## Practical Technical Specification for Designing Production AI Automation Workflows

Use this template after an AI automation opportunity has been identified and approved for design.

The purpose is to convert a business automation idea into a clear implementation specification that developers, automation specialists, CRM teams, AI engineers and business owners can review before deployment.

This template covers:

- Business objective
- Trigger and workflow logic
- Systems and integrations
- Data mapping
- AI responsibilities
- Prompt and output requirements
- Business rules
- Human handoff
- Error handling
- Security and privacy
- Testing
- Measurement
- Deployment and ownership

> **Principle:** A production workflow should be understandable without relying on undocumented logic inside an automation platform.

---

# 1. Workflow Information

```text
Workflow Name:

Workflow ID:

Version:

Status:
[ ] Draft
[ ] Review
[ ] Approved
[ ] Development
[ ] Testing
[ ] Production
[ ] Paused
[ ] Retired

Business Owner:

Technical Owner:

CRM / System Owner:

Prepared By:

Created Date:

Last Updated:
```

---

# 2. Business Objective

## Problem

```text
What business problem does this workflow solve?

____________________________________________________________

____________________________________________________________
```

## Desired Outcome

```text
____________________________________________________________
```

## Primary Success Metric

```text
Metric:

Baseline:

Expected Direction / Target:

Measurement Source:
```

---

# 3. Scope

## Included

```text
1.
2.
3.
4.
```

## Excluded

```text
1.
2.
3.
4.
```

Clearly defining exclusions prevents the workflow from expanding into unsupported use cases.

---

# 4. Users / Entities Affected

- [ ] Prospect
- [ ] Lead
- [ ] Customer
- [ ] Employee
- [ ] Sales team
- [ ] Support team
- [ ] Marketing team
- [ ] Operations team
- [ ] Other: ______________________

### Relevant Entity Types

```text
Contact:

Company:

Opportunity:

Appointment:

Conversation:

Order / Payment:

Other:
```

---

# 5. Workflow Trigger

What starts the workflow?

- [ ] Form submission
- [ ] CRM contact created
- [ ] CRM field updated
- [ ] Opportunity stage changed
- [ ] Incoming WhatsApp message
- [ ] Incoming email
- [ ] Website chat
- [ ] Appointment event
- [ ] Payment event
- [ ] Webhook
- [ ] API event
- [ ] Scheduled event
- [ ] Manual employee action
- [ ] Other: ______________________

### Exact Trigger Definition

```text
____________________________________________________________
```

### Trigger Source

```text
System:

Event:

Endpoint / Webhook / Automation:

Relevant Event ID:
```

---

# 6. Entry Conditions

The workflow should execute only when:

```text
Condition 1:

Condition 2:

Condition 3:

Condition 4:
```

Example:

```text
Contact exists
AND
Service Interest is populated
AND
Automation Status != Paused
AND
Event ID has not already been processed
```

---

# 7. Exclusion Conditions

Do not enter when:

- [ ] Contact opted out
- [ ] Record is duplicate
- [ ] Human currently owns conversation
- [ ] Opportunity is closed
- [ ] Customer already completed desired action
- [ ] Required data is missing
- [ ] Event was previously processed
- [ ] Workflow is paused
- [ ] Other: ______________________

### Exact Exclusions

```text
____________________________________________________________
```

---

# 8. Current Process

Document the process being replaced or improved.

```text
Trigger
↓
Current Step 1
↓
Current Step 2
↓
Current Step 3
↓
Current Outcome
```

### Current Problems

```text
____________________________________________________________

____________________________________________________________
```

---

# 9. Proposed Workflow

```text
Trigger
↓
Validation
↓
Data Retrieval
↓
Rules / AI Processing
↓
Decision
↓
Action
↓
Human Handoff if Required
↓
CRM / System Update
↓
Measurement
↓
End
```

### Detailed Flow

```text
____________________________________________________________

____________________________________________________________

____________________________________________________________
```

---

# 10. Workflow Step Specification

Use one row for each major step.

| # | Step | System | Input | Logic | Output | Failure Action |
|---:|---|---|---|---|---|---|
| 1 | | | | | | |
| 2 | | | | | | |
| 3 | | | | | | |
| 4 | | | | | | |
| 5 | | | | | | |
| 6 | | | | | | |

---

# 11. Systems and Integrations

| System | Role | Read | Write | Integration Method | Owner |
|---|---|---|---|---|---|
| CRM | | | | | |
| AI Provider | | | | | |
| Messaging | | | | | |
| Calendar | | | | | |
| Website / Form | | | | | |
| Analytics | | | | | |
| Other | | | | | |

Integration methods may include:

- Native integration
- API
- Webhook
- Integration platform
- Database
- File exchange

---

# 12. Source of Truth

| Data | Authoritative System | Update Direction |
|---|---|---|
| Contact | | |
| Lead Source | | |
| Service Interest | | |
| Qualification | | |
| Owner | | |
| Opportunity Stage | | |
| Appointment | | |
| Payment | | |
| Communication Status | | |

Avoid allowing multiple systems to overwrite critical fields without explicit synchronization rules.

---

# 13. Input Data

List required inputs.

| Field | Source | Type | Required? | Validation | Sensitive? |
|---|---|---|:---:|---|:---:|
| | | | [ ] | | [ ] |
| | | | [ ] | | [ ] |
| | | | [ ] | | [ ] |
| | | | [ ] | | [ ] |

---

# 14. Data Normalization

Required transformations:

```text
Phone normalization:

Email normalization:

Date/time normalization:

Location normalization:

Currency normalization:

Text cleanup:

Other:
```

---

# 15. Duplicate Handling

### Duplicate Identifier(s)

```text
[ ] Email
[ ] Phone
[ ] CRM Contact ID
[ ] External ID
[ ] Event ID
[ ] Appointment ID
[ ] Other:
```

### Duplicate Logic

```text
Existing Record?
├── Yes → ______________________________________
└── No  → ______________________________________
```

---

# 16. Idempotency

How will repeated events be prevented from causing repeated consequences?

```text
Idempotency Key:

Where Stored:

Retention:

Duplicate Event Action:
```

Example:

```text
Webhook Event ID already processed?
├── Yes → Stop
└── No → Continue and store ID
```

---

# 17. Business Rules

Document deterministic rules separately from AI.

### Rule 1

```text
IF:

THEN:

ELSE:
```

### Rule 2

```text
IF:

THEN:

ELSE:
```

### Rule 3

```text
IF:

THEN:

ELSE:
```

### Rule 4

```text
IF:

THEN:

ELSE:
```

Important policies such as eligibility, pricing authority, ownership and communication restrictions should not depend on unconstrained model interpretation.

---

# 18. AI Requirement

Does this workflow actually require AI?

```text
[ ] Yes
[ ] No
```

### AI Task

- [ ] Intent classification
- [ ] Requirement extraction
- [ ] Structured data extraction
- [ ] Summarization
- [ ] Suggested response
- [ ] FAQ interpretation
- [ ] Document analysis
- [ ] Language understanding
- [ ] Other: ______________________

### Why AI Is Required

```text
____________________________________________________________
```

---

# 19. AI Responsibility Boundary

## AI May

```text
1.
2.
3.
4.
```

## AI May Not

```text
1.
2.
3.
4.
```

Example restrictions:

- Invent customer information
- Negotiate pricing
- Approve discounts
- Make contractual commitments
- Override CRM ownership
- Ignore opt-out state
- Confirm unavailable appointments
- Expose internal information

---

# 20. AI Model / Provider

```text
Provider:

Model:

Model Version / Alias:

API / Platform:

Reason Selected:

Fallback Model if Applicable:
```

Avoid assuming model behavior remains unchanged indefinitely.

---

# 21. AI Context

What context is supplied?

- [ ] Current customer message
- [ ] Recent conversation
- [ ] CRM fields
- [ ] Approved knowledge
- [ ] Product/service data
- [ ] Previous summary
- [ ] Other: ______________________

### Context Limits

```text
____________________________________________________________
```

Only provide information required for the task.

---

# 22. AI Prompt Specification

### System / Instruction Purpose

```text
____________________________________________________________
```

### Required Instructions

```text
1.
2.
3.
4.
5.
```

### Prohibited Behavior

```text
1.
2.
3.
4.
```

### Missing Information Behavior

```text
If information is not available:

____________________________________________________________
```

The model should not invent missing business or customer facts.

---

# 23. Prompt Template

```text
ROLE / TASK:
[Describe the narrow AI task.]

APPROVED CONTEXT:
{{context}}

CUSTOMER / INPUT DATA:
{{input}}

INSTRUCTIONS:
1.
2.
3.

OUTPUT REQUIREMENT:
[Define exact expected structure.]

IF UNCERTAIN:
[Define fallback or escalation behavior.]
```

Do not place credentials, API keys or secrets in prompts.

---

# 24. AI Output Schema

Where possible, use structured output.

Example:

```json
{
  "intent": "sales_enquiry",
  "service_interest": "crm_automation",
  "requirement_summary": "Needs lead routing and follow-up automation",
  "needs_human_review": false
}
```

### Production Schema

```json
{
}
```

---

# 25. Output Validation

Validate:

- [ ] JSON/schema
- [ ] Required keys
- [ ] Allowed categories
- [ ] Data types
- [ ] Maximum length
- [ ] Missing values
- [ ] Unsupported values
- [ ] Sensitive content
- [ ] Other: ______________________

### Invalid Output Action

```text
____________________________________________________________
```

Never write unvalidated AI output directly into consequential production fields.

---

# 26. AI Confidence / Uncertainty

If the implementation uses uncertainty logic, define how it is interpreted.

```text
Reliable / Supported:
→ Continue

Unclear:
→ Ask approved clarification or review

Unsupported:
→ Human handoff
```

Do not treat a model-generated numerical confidence score as guaranteed probability unless the system has been specifically calibrated and validated for that use.

---

# 27. Human Handoff

### Handoff Required?

```text
[ ] Yes
[ ] No
```

### Triggers

- [ ] Customer asks for human
- [ ] AI uncertain
- [ ] Unsupported request
- [ ] Complaint
- [ ] Pricing negotiation
- [ ] High-value opportunity
- [ ] Sensitive topic
- [ ] Workflow failure
- [ ] Approval required
- [ ] Other: ______________________

---

# 28. Handoff Routing

```text
Primary Owner / Queue:

Fallback Owner / Queue:

Priority:

Expected Internal Response Target:
```

### On Handoff

```text
AI Active = FALSE

Handoff Status = Open

Human Owner = ____________________

Related Automation Paused:
__________________________________
```

---

# 29. Handoff Summary

Required summary fields:

```text
Contact:

Intent:

Requirement:

Relevant CRM Status:

Important Conversation Context:

Handoff Reason:

Recommended Next Action:
```

Summaries should remain factual and distinguish inference from verified information.

---

# 30. Customer Communication

Does the workflow send customer-facing messages?

```text
[ ] Yes
[ ] No
```

### Channel

- [ ] WhatsApp
- [ ] Email
- [ ] SMS
- [ ] Website Chat
- [ ] Social Messaging
- [ ] Other: ______________________

### Message Purpose

```text
____________________________________________________________
```

---

# 31. Message Specification

```text
Message / Template Name:

Trigger:

Eligibility:

Variables:

Stop Conditions:

Fallback:
```

### Approved Copy

```text
____________________________________________________________

____________________________________________________________
```

---

# 32. Communication Controls

Verify:

- [ ] Communication eligibility checked
- [ ] Current platform requirements reviewed
- [ ] Opt-out respected
- [ ] Human takeover checked
- [ ] Business hours considered where relevant
- [ ] Duplicate message prevented
- [ ] Customer already completed goal checked
- [ ] Current appointment/opportunity state checked

---

# 33. CRM Actions

| Event | CRM Action | Field | New Value |
|---|---|---|---|
| | | | |
| | | | |
| | | | |
| | | | |

### Fields AI May Update

```text
____________________________________________________________
```

### Fields AI May NOT Update Directly

```text
____________________________________________________________
```

---

# 34. Opportunity / Pipeline Actions

```text
Create Opportunity?
[ ] Yes
[ ] No

Creation Condition:

Pipeline:

Initial Stage:

Owner:

Stage Automation Rules:

Won Condition:

Lost Condition:
```

---

# 35. Appointment Actions

```text
Calendar:

Appointment Type:

Booking Condition:

Confirmation:

Reminder Workflow:

Reschedule Logic:

Cancellation Logic:

No-Show Logic:
```

AI should not invent availability when availability must come from a calendar or scheduling system.

---

# 36. Stop Conditions

The workflow stops when:

- [ ] Goal completed
- [ ] Customer opts out
- [ ] Human takes ownership
- [ ] Opportunity closes
- [ ] Appointment booked
- [ ] Customer becomes ineligible
- [ ] Maximum attempts reached
- [ ] Workflow manually paused
- [ ] Other: ______________________

### Exact Stop Logic

```text
____________________________________________________________
```

---

# 37. Retry Logic

| Failure | Retry? | Attempts | Delay | Final Action |
|---|:---:|---:|---|---|
| Temporary API error | | | | |
| AI timeout | | | | |
| CRM unavailable | | | | |
| Message failure | | | | |
| Invalid data | | | | |

Do not use unlimited retries.

---

# 38. Error Handling

### Error Categories

- [ ] Input
- [ ] API
- [ ] Authentication
- [ ] AI
- [ ] CRM
- [ ] Messaging
- [ ] Calendar
- [ ] Business rule
- [ ] Duplicate
- [ ] Unknown

### General Failure Path

```text
Failure
↓
Log Error
↓
Retry if Safe
↓
Recovered?
├── Yes → Continue
└── No
     ↓
Create Recovery Task / Alert
↓
Human Review if Required
```

---

# 39. Loop Prevention

Could system updates trigger the workflow again?

```text
[ ] Yes
[ ] No
[ ] Unknown
```

### Prevention Method

- [ ] Source marker
- [ ] Workflow flag
- [ ] Event ID
- [ ] Timestamp
- [ ] Change detection
- [ ] Idempotency key
- [ ] Other: ______________________

---

# 40. Logging

Record where appropriate:

```text
Execution ID
Workflow Version
Contact / Entity ID
Trigger Event ID
Timestamp
Input Status
AI Model
AI Output Status
Decision
Action
Human Handoff
Error
Final Outcome
```

Avoid logging unnecessary sensitive data.

---

# 41. Monitoring

### Operational Metrics

```text
Workflow executions:

Success rate:

Failure rate:

Processing time:

Retry rate:

Backlog:
```

### AI Metrics

```text
Valid output rate:

Classification / extraction accuracy:

Human correction rate:

Unsupported output rate:
```

### Business Metrics

```text
____________________________________________________________
```

---

# 42. Alerts

Create alerts for:

- [ ] Authentication failure
- [ ] Failure spike
- [ ] AI invalid-output spike
- [ ] Queue backlog
- [ ] Messaging failure
- [ ] Cost spike
- [ ] Duplicate-event spike
- [ ] Missed handoff
- [ ] Other: ______________________

### Alert Destination

```text
____________________________________________________________
```

---

# 43. Security

Review:

- [ ] Credentials stored securely
- [ ] Least-privilege API access
- [ ] Webhooks authenticated/validated
- [ ] Secrets excluded from prompts
- [ ] Secrets excluded from repository
- [ ] Employee permissions reviewed
- [ ] Logs protected
- [ ] Production/test environments separated where appropriate

---

# 44. Privacy and Data Handling

### Personal Data Used

```text
____________________________________________________________
```

### Sensitive Data Used

```text
____________________________________________________________
```

### AI Provider Receives

```text
____________________________________________________________
```

### Data Retention

```text
____________________________________________________________
```

### Required Review

- [ ] Privacy
- [ ] Security
- [ ] Legal/compliance
- [ ] Vendor terms
- [ ] No additional review identified

Requirements depend on the use case and jurisdiction.

---

# 45. Cost Controls

Track:

```text
Automation platform cost:

AI/API cost:

Messaging cost:

Infrastructure:

Human review:

Expected monthly volume:

Estimated cost per case:
```

### Cost Alert / Limit

```text
____________________________________________________________
```

---

# 46. Test Environment

```text
Environment:

Test CRM Account / Pipeline:

Test Phone / Email:

Test Calendar:

Test API Credentials:

Test Data Policy:
```

Do not use live customer data unnecessarily during testing.

---

# 47. Functional Test Cases

| # | Scenario | Expected Result | Status |
|---:|---|---|:---:|
| 1 | Normal valid input | | [ ] |
| 2 | Missing required data | | [ ] |
| 3 | Duplicate event | | [ ] |
| 4 | Existing customer | | [ ] |
| 5 | Human requested | | [ ] |
| 6 | AI uncertain | | [ ] |
| 7 | Unsupported request | | [ ] |
| 8 | API failure | | [ ] |
| 9 | CRM failure | | [ ] |
| 10 | Customer opts out | | [ ] |

---

# 48. AI Test Cases

Test:

- [ ] Clear intent
- [ ] Ambiguous intent
- [ ] Missing information
- [ ] Long input
- [ ] Short input
- [ ] Typographical errors
- [ ] Multiple requirements
- [ ] Unsupported request
- [ ] Customer asks for human
- [ ] Adversarial / irrelevant input where appropriate
- [ ] Multiple supported languages where applicable

### AI Acceptance Criteria

```text
____________________________________________________________
```

---

# 49. Failure Test Cases

Test intentionally:

```text
AI API unavailable
CRM unavailable
Messaging provider unavailable
Invalid credentials
Invalid JSON
Missing field
Duplicate webhook
Out-of-order event
Calendar unavailable
Owner unavailable
```

Every critical failure should have an expected behavior.

---

# 50. Human Handoff Tests

- [ ] Explicit human request
- [ ] AI uncertainty
- [ ] Complaint
- [ ] High-value lead
- [ ] Owner unavailable
- [ ] Fallback queue
- [ ] AI pauses
- [ ] Human receives context
- [ ] Resume logic
- [ ] Handoff closes correctly

---

# 51. User Acceptance Testing

```text
Business Tester:

Test Period:

Number of Test Cases:

Issues Found:

Critical Issues:

Approval:
[ ] Approved
[ ] Approved with Conditions
[ ] Rejected
```

---

# 52. Deployment Checklist

- [ ] Business rules approved
- [ ] Prompt approved
- [ ] AI output validated
- [ ] Integrations tested
- [ ] Idempotency tested
- [ ] Error handling tested
- [ ] Human handoff tested
- [ ] Communication controls tested
- [ ] Monitoring active
- [ ] Alerts active
- [ ] Dashboard/reporting active
- [ ] Rollback plan documented
- [ ] Owners trained
- [ ] Production credentials configured securely

---

# 53. Rollout Strategy

Select:

```text
[ ] Internal Test
[ ] Limited Pilot
[ ] Percentage Rollout
[ ] Single Team / Location
[ ] Single Use Case
[ ] Full Deployment
```

### Initial Scope

```text
____________________________________________________________
```

### Expansion Condition

```text
____________________________________________________________
```

---

# 54. Rollback Plan

If the workflow creates unacceptable behavior:

```text
1. Disable:
________________________________________

2. Restore Manual Process:
________________________________________

3. Recover Failed Records:
________________________________________

4. Notify:
________________________________________

5. Investigate:
________________________________________
```

---

# 55. Measurement Plan

### Baseline Period

```text
____________________________________________________________
```

### Metrics

| Metric | Baseline | Target / Direction | Source | Review Frequency |
|---|---:|---:|---|---|
| Reliability | | | | |
| Processing Time | | | | |
| Human Intervention | | | | |
| AI Quality | | | | |
| Business Outcome | | | | |
| Cost | | | | |

---

# 56. Post-Launch Review

### Review Date

```text
____________________________________________________________
```

### Questions

```text
Is the workflow reliable?

Is AI output accurate enough for its assigned task?

Are human handoffs working?

Are failures visible?

Has manual effort changed?

Has the business outcome improved?

Are operating costs acceptable?

Should the workflow be expanded, modified or retired?
```

---

# 57. Version History

| Version | Date | Change | Owner | Approved By |
|---|---|---|---|---|
| 1.0 | | Initial specification | | |
| | | | | |
| | | | | |

Track major changes to prompts, models, rules and integrations.

---

# 58. Change Control

Changes requiring review may include:

- AI model change
- Prompt change
- Business-rule change
- New CRM field
- New communication channel
- New customer segment
- New system integration
- Expanded AI authority
- Changed human handoff
- Changed data access

### Change Approval Process

```text
____________________________________________________________
```

---

# 59. Final Approval

```text
Business Owner:
Name:
Approved: [ ] Yes [ ] No
Date:

Technical Owner:
Name:
Approved: [ ] Yes [ ] No
Date:

Security / Privacy Review if Required:
Name:
Approved: [ ] Yes [ ] No
Date:

Final Production Approval:
Name:
Date:
```

---

# 60. Quick Workflow Specification

For smaller, lower-risk workflows:

```text
WORKFLOW
________________________________________

OBJECTIVE
________________________________________

TRIGGER
________________________________________

ENTRY CONDITIONS
________________________________________

INPUT
________________________________________

RULES
________________________________________

AI TASK
________________________________________

AI OUTPUT
________________________________________

ACTION
________________________________________

HUMAN HANDOFF
________________________________________

STOP CONDITIONS
________________________________________

FAILURE PATH
________________________________________

SYSTEMS
________________________________________

MEASUREMENT
________________________________________

OWNER
________________________________________
```

---

# 61. Example Specification — AI Lead Routing

> Illustrative example only.

## Objective

Reduce manual lead-routing time while preserving existing CRM ownership rules.

## Trigger

```text
New inbound website lead
```

## Entry Conditions

```text
Valid contact
AND
Service interest available or free-text enquiry present
AND
No existing active opportunity
```

## AI Task

Extract:

```json
{
  "service_interest": "",
  "requirement_summary": "",
  "needs_human_review": false
}
```

## Business Rules

```text
Existing Owner?
├── Yes → Preserve Owner
└── No
     ↓
Service = SEO?
├── Yes → SEO Queue
└── Service = Automation?
     ├── Yes → Automation Queue
     └── Human Review
```

## AI Restrictions

AI does not:

- Select employee based on invented criteria
- Change existing ownership
- Determine pricing
- Create unsupported customer information

## Handoff

Trigger if:

```text
Service unclear
Custom requirement
AI output invalid
Customer requests human
```

## Measurement

```text
Routing time
Correct routing rate
Reassignment rate
Human review rate
Workflow success rate
```

---

# 62. Common Specification Mistakes

## Building Directly in the Automation Tool

Important workflow logic should be documented first.

## Mixing AI and Business Rules

Keep deterministic policy separate from model interpretation.

## No Source of Truth

Unclear ownership creates conflicting data.

## No Invalid-Output Path

AI output must be treated as untrusted until validated.

## No Idempotency

Duplicate events can create duplicate messages, contacts, tasks or opportunities.

## Only Testing the Happy Path

Production reliability depends heavily on failure behavior.

## No Human Handoff

AI needs a controlled boundary.

## No Rollback Plan

Every important automation should be stoppable.

## No Measurement

A workflow cannot be improved if its outcome is invisible.

---

# 63. Core Principles

1. **Document the business objective before technical logic.**
2. **Define triggers, entry conditions and exclusions precisely.**
3. **Separate deterministic rules from AI interpretation.**
4. **Validate AI output before consequential actions.**
5. **Define authoritative systems for critical data.**
6. **Build idempotency, retries and recovery into the design.**
7. **Make human handoff explicit.**
8. **Test failure paths before production.**
9. **Track workflow, prompt, model and rule versions.**
10. **Measure the workflow against the original business outcome.**

---

# Related Resources

- [AI Automation Opportunity Worksheet](ai-automation-opportunity-worksheet.md)
- [AI Automation Strategy Framework](ai-automation-strategy-framework.md)
- [AI Workflow Design Framework](ai-workflow-design-framework.md)
- [CRM + AI Automation Framework](crm-ai-automation-framework.md)
- [WhatsApp + AI Automation Framework](whatsapp-ai-automation-framework.md)
- [AI Agent Human Handoff Framework](ai-agent-human-handoff-framework.md)
- [AI Automation Measurement Framework](ai-automation-measurement-framework.md)
- [AI Lead Qualification Framework](ai-lead-qualification-framework.md)
- [AI Automation Readiness Checklist](ai-automation-readiness-checklist.md)
- [AI Automation Playbooks](README.md)

---

## About the Repository

This template is part of **[AI Automation Playbooks](README.md)**, maintained by **[Prashant Rajput](https://github.com/prashant6788)**, Founder of [Touchstone Infotech](https://www.touchstoneinfotech.com/).

The repository focuses on practical systems for:

**AI · Automation · CRM · Lead Management · Workflow Design · System Integration · Revenue Operations**

---

## Important Note

This template is an implementation-planning resource, not a substitute for architecture, security, privacy, legal or compliance review where those are required.

AI models, APIs, CRM platforms, messaging systems and automation tools change continuously. Production specifications should be validated against current vendor documentation, business requirements, data sensitivity, applicable regulations and real-world testing.

---

## License

This resource is intended to follow the license applicable to the **AI Automation Playbooks** repository.

See [LICENSE](LICENSE) for license details once the repository license is published.
