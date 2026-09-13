# AI Automation Implementation Example

## Sanitized Example: B2B Services Lead Qualification, Routing and Appointment Workflow

> **Important:** This is a fictional, sanitized implementation example created for educational purposes. It does not represent a specific Touchstone Infotech client, and the example data, company names, volumes and workflow outcomes below should not be interpreted as real client results.

This example demonstrates how the frameworks in this repository can be combined into one practical AI automation system.

The scenario is intentionally realistic but simplified enough to show the architecture clearly.

---

# 1. Scenario

A fictional B2B services company receives enquiries through:

- Website forms
- Paid advertising landing pages
- WhatsApp
- Referral campaigns

The company offers three service categories:

```text
SEO
CRM Automation
Paid Media
```

Before automation, a sales coordinator manually:

1. Reviews each enquiry
2. Identifies the requested service
3. Checks whether enough qualification information exists
4. Creates or updates the CRM contact
5. Assigns the correct salesperson
6. Sends an acknowledgement
7. Offers a consultation
8. Follows up when the lead does not respond

The company wants to automate the repetitive parts without allowing AI to control pricing, commercial decisions or customer ownership.

---

# 2. Business Problem

The existing process has several operational problems.

```text
Lead arrives
↓
Waits for employee review
↓
Employee reads free-text enquiry
↓
Employee identifies service
↓
Employee updates CRM
↓
Employee assigns owner
↓
Employee sends response
```

Potential issues include:

- Response delays
- Inconsistent categorization
- Manual CRM updates
- Missed assignment
- Repetitive qualification
- Limited visibility into workflow failures
- No structured AI-to-human escalation

---

# 3. Desired Outcome

The proposed system should:

- Capture leads centrally
- Preserve lead-source attribution
- Validate required information
- Use AI to interpret free-text requirements
- Apply deterministic qualification rules
- Route leads according to explicit business rules
- Send an approved acknowledgement
- Offer an appropriate consultation path
- Escalate unclear or sensitive cases
- Record workflow outcomes
- Measure reliability and business impact

The goal is **not** to create an autonomous salesperson.

---

# 4. Automation Boundary

The implementation separates work into three layers.

## Deterministic Automation

Used for:

- Duplicate detection
- CRM record creation/update
- Attribution
- Eligibility rules
- Lead routing
- Appointment status
- Follow-up timing
- Stop conditions
- Human ownership

## AI

Used for:

- Intent classification
- Service-interest extraction
- Requirement summarization
- Identifying whether clarification may be required
- Creating a factual handoff summary

## Human

Required for:

- Pricing negotiation
- Custom proposals
- High-value or unusual requirements
- Complaints
- Unsupported questions
- AI uncertainty
- Commercial exceptions
- Customer-requested human conversation

---

# 5. Reference Architecture

```text
Website / Ads / WhatsApp / Referral
                ↓
           Lead Capture
                ↓
      Validation + Normalization
                ↓
              CRM
                ↓
        Existing Contact?
          ↙           ↘
        Yes            No
         ↓              ↓
       Update         Create
          ↘           ↙
          Preserve Source
                ↓
         AI Interpretation
                ↓
       Structured Validation
                ↓
          Business Rules
                ↓
           Qualification
          ↙      ↓       ↘
     Qualified  Clarify  Human Review
          ↓
        Routing
          ↓
   Approved Acknowledgement
          ↓
     Consultation / Follow-Up
          ↓
       Human Sales Team
          ↓
          Pipeline
          ↓
        Measurement
```

---

# 6. Example Lead

A fictional enquiry:

```text
Name: Arjun Mehta

Company: Northstar Advisory

Phone: +91 98XXXXXX21

Email: arjun@example.com

Source: Google Ads

Message:
"We are getting around 80-100 enquiries a month from our
website and ads. We need a CRM and automated WhatsApp
follow-up because the sales team is missing leads."
```

This record is fictional.

---

# 7. Trigger

The workflow starts when:

```text
New eligible inbound lead is received
```

Possible trigger sources:

- Website webhook
- CRM form submission
- Advertising lead integration
- Messaging integration

---

# 8. Entry Conditions

Example:

```text
Lead has a usable contact identifier
AND
Automation Status != Paused
AND
Event has not already been processed
```

Additional business-specific conditions could be added as required.

---

# 9. Exclusion Conditions

Do not enter normal automated qualification when:

```text
Contact is suppressed from applicable communication
OR
Existing active customer requires account-management routing
OR
Human already owns the active conversation
OR
Duplicate event has already been processed
```

---

# 10. Step 1 — Normalize Input

Example transformations:

```text
Phone
→ Normalize to consistent format

Email
→ Trim and normalize where appropriate

Service Field
→ Map allowed values

Source
→ Preserve original attribution

Message
→ Preserve original text for interpretation
```

---

# 11. Step 2 — Duplicate Check

Example:

```text
Search CRM by normalized phone/email
↓
Existing Contact?
├── Yes → Update according to field policy
└── No → Create new contact
```

The workflow should not create multiple contacts simply because the same person submits another enquiry.

---

# 12. Step 3 — Preserve Attribution

For this example:

```text
Original Source = Google Ads
Current Conversation Channel = Website
```

If the lead later replies through WhatsApp:

```text
Original Source remains Google Ads
Current Conversation Channel becomes WhatsApp
```

The acquisition source is not overwritten.

---

# 13. Step 4 — AI Interpretation

The AI receives only the context needed for the task.

Example input:

```text
Customer message:
"We are getting around 80-100 enquiries a month from our
website and ads. We need a CRM and automated WhatsApp
follow-up because the sales team is missing leads."

Allowed service categories:
- SEO
- CRM Automation
- Paid Media
- Unknown
```

---

# 14. Example AI Instruction

```text
TASK:
Extract the customer's primary service interest and create
a short factual requirement summary.

RULES:
- Use only information explicitly contained in the enquiry.
- Do not invent budget, location, company size or timeline.
- Choose service_interest only from the allowed categories.
- If the service cannot be determined, return "Unknown".
- Set needs_human_review to true if the request does not fit
  the supported categories.

OUTPUT:
Return the required structured JSON only.
```

---

# 15. Expected Structured Output

```json
{
  "service_interest": "CRM Automation",
  "requirement_summary": "Needs a CRM and automated WhatsApp follow-up for inbound website and advertising leads.",
  "needs_human_review": false
}
```

This output is an example, not a claim about any particular model's guaranteed behavior.

---

# 16. Output Validation

Before using the result:

```text
Valid JSON?
↓
Required fields present?
↓
service_interest is allowed value?
↓
Summary within expected length?
↓
needs_human_review is boolean?
```

If any validation fails:

```text
Do not write invalid output
↓
Log failure
↓
Retry only if appropriate
↓
Human review if unresolved
```

---

# 17. CRM Field Mapping

Example:

| Information | CRM Field | Source |
|---|---|---|
| Name | Contact Name | User supplied |
| Phone | Phone | User supplied |
| Email | Email | User supplied |
| Original Source | Lead Source | System |
| Service Interest | Service Interested In | AI-assisted extraction |
| Requirement Summary | Lead Summary | AI-assisted |
| Qualification | Qualification Status | Business rules |
| Owner | Assigned Owner | Routing rules |
| AI Review | AI Review Status | Workflow |

AI-derived fields should be identifiable where that distinction matters operationally.

---

# 18. Qualification Rules

Assume the fictional company requires:

```text
Valid Contact
+
Supported Service
+
Business Requirement Present
```

Example:

```text
Valid contact?
├── No → Invalid / Review
└── Yes
     ↓
Supported service?
├── No → Human Review
└── Yes
     ↓
Requirement present?
├── No → Ask Clarification
└── Yes → Qualified for Initial Sales Follow-Up
```

AI helps interpret the enquiry.

The qualification policy remains deterministic.

---

# 19. Information the AI Must Not Invent

The example enquiry does not provide:

```text
Budget
Location
Timeline
Decision-maker status
Company revenue
```

Therefore the CRM should preserve:

```text
Budget = Unknown
Location = Unknown
Timeline = Unknown
```

rather than generating likely values.

---

# 20. Routing Rules

Example:

```text
Existing Owner?
├── Yes → Preserve Existing Owner
└── No
     ↓
Service Interest?
├── SEO → SEO Sales Queue
├── CRM Automation → Automation Sales Queue
├── Paid Media → Performance Sales Queue
└── Unknown → Sales Coordinator Review
```

The AI identifies the service category.

Deterministic rules select the destination.

---

# 21. Example Routing Result

For the fictional lead:

```text
Service Interest = CRM Automation
↓
Existing Owner = No
↓
Route to Automation Sales Queue
```

The AI does not select an individual salesperson.

---

# 22. CRM Update

Example record after processing:

```text
Contact:
Arjun Mehta

Company:
Northstar Advisory

Original Source:
Google Ads

Service Interest:
CRM Automation

Requirement Summary:
Needs a CRM and automated WhatsApp follow-up for inbound
website and advertising leads.

Qualification Status:
Qualified for Initial Sales Follow-Up

Owner:
Automation Sales Queue

AI Review Status:
Validated
```

All names and values in this example are fictional.

---

# 23. Approved Customer Acknowledgement

The workflow can send a controlled acknowledgement.

Example:

```text
Hi Arjun,

Thanks for getting in touch.

We have received your enquiry regarding CRM and lead follow-up
automation. A member of the team can review your requirements
with you and discuss the appropriate next steps.

You can also choose a consultation time here:
[Approved Booking Link]
```

The message does not claim that a human has already reviewed the enquiry.

---

# 24. Appointment Path

```text
Qualified Lead
↓
Correct Consultation Calendar
↓
Booking Link
↓
Appointment Created?
├── Yes
│   ↓
│ CRM Updated
│   ↓
│ Confirmation / Reminder Workflow
│
└── No
    ↓
  Follow-Up According to Policy
```

Availability should come from the scheduling system, not AI invention.

---

# 25. Follow-Up Logic

Example:

```text
Acknowledgement Sent
↓
Wait Defined Period
↓
Customer Replied or Booked?
├── Yes → Stop Automated Follow-Up
└── No
     ↓
Eligible for Follow-Up?
├── No → Stop
└── Yes → Send Approved Follow-Up
```

The production team would define actual timing and maximum attempts.

---

# 26. Stop Conditions

Stop the automated sales follow-up when:

- Customer replies meaningfully
- Human takes over
- Appointment is booked
- Opportunity reaches an excluded stage
- Customer opts out
- Lead becomes invalid
- Maximum follow-up attempts are reached

---

# 27. Human Handoff Triggers

The fictional workflow escalates when:

```text
Customer explicitly requests a human
OR
AI cannot classify service
OR
AI output fails validation
OR
Complaint detected
OR
Pricing negotiation begins
OR
Custom/unsupported requirement appears
OR
Business rule requires senior review
```

---

# 28. Example Handoff Scenario

Customer replies:

```text
"We need integrations with our internal ERP and a custom
approval workflow. Can I speak to someone about the technical
architecture and pricing?"
```

The system should not attempt to design or price the custom project automatically.

---

# 29. Handoff Flow

```text
Custom Requirement Detected
↓
AI Active = FALSE
↓
Handoff Status = Open
↓
Generate Factual Summary
↓
Assign Automation Sales / Technical Owner
↓
Create CRM Task
↓
Notify Owner
↓
Human Continues
```

---

# 30. Example Handoff Summary

```text
Contact:
Arjun Mehta

Company:
Northstar Advisory

Original Requirement:
CRM and automated WhatsApp follow-up for inbound leads.

New Request:
Customer asked about an internal ERP integration, custom
approval workflow, technical architecture and pricing.

Handoff Reason:
Custom technical requirement + pricing discussion.

Current Status:
Qualified lead.

Recommended Next Action:
Human technical/sales discovery.
```

The summary reports what the customer asked for without claiming purchase intent.

---

# 31. Human Takeover

When the employee takes over:

```text
AI Active = FALSE
Human Owner = Assigned Employee
Handoff Status = In Progress
```

Relevant automated conversational responses pause.

---

# 32. Resume Logic

After the human completes the interaction, possible outcomes include:

```text
Remain Human-Owned
OR
Move to Proposal Workflow
OR
Return to Approved Automation
OR
Close Opportunity
```

AI should not automatically resume without a defined state.

---

# 33. Example Opportunity Creation

Assume the fictional company's policy is:

```text
Create opportunity only after initial qualification
```

Then:

```text
Qualification = Qualified
↓
Create Opportunity
↓
Pipeline = B2B Services
↓
Stage = New Qualified Opportunity
```

This is a business rule, not an AI decision.

---

# 34. Pipeline Movement

Reliable events can update the pipeline.

Example:

```text
Consultation Booked
→ Discovery Scheduled

Discovery Completed
→ Discovery Completed

Proposal Sent
→ Proposal Sent

Confirmed Payment / Contract Event
→ Won
```

Avoid moving stages solely because AI believes the lead “sounds interested.”

---

# 35. Example Failure — AI API Unavailable

```text
AI Request
↓
Timeout
↓
Limited Retry
↓
Still Failed?
├── No → Continue
└── Yes
     ↓
Set AI Review Status = Required
↓
Route to Sales Coordinator
↓
Log Failure
```

The lead should not disappear because AI is unavailable.

---

# 36. Example Failure — CRM Write Fails

```text
CRM Update
↓
Failure
↓
Retry if Safe
↓
Still Failed?
↓
Log Error
↓
Create Recovery Alert
↓
Do Not Send Downstream Message That Depends on Missing CRM State
```

---

# 37. Example Failure — Duplicate Webhook

```text
Webhook Event Received
↓
Event ID Already Processed?
├── Yes → Stop
└── No → Continue
```

This prevents duplicate contacts, messages and opportunities.

---

# 38. Example Message Collision

Before sending a follow-up:

```text
Human replied recently?
Appointment booked?
Customer opted out?
Opportunity closed?
Another workflow already sent?
```

If any stop condition applies:

```text
Do Not Send
```

---

# 39. Logging

Example operational log:

```text
Execution ID:
WF-2026-EXAMPLE-001

Workflow:
Inbound Lead Qualification

Workflow Version:
1.0

Contact ID:
EXAMPLE-123

Trigger:
Website Lead

AI Output:
Valid

Service:
CRM Automation

Routing:
Automation Sales Queue

Handoff:
No

Final Status:
Qualified / Acknowledgement Sent
```

Do not expose unnecessary customer information in logs.

---

# 40. Measurement Plan

The fictional company would establish a real baseline before claiming improvement.

Suggested metrics:

## Reliability

- Workflow success rate
- AI output validity
- CRM write failures
- Duplicate event rate

## Efficiency

- Median time to qualification
- Median time to assignment
- Manual review rate

## AI Quality

- Service classification accuracy
- Requirement-summary correction rate
- Human review rate
- Missed handoff rate

## Business

- Qualification completion
- Appointment booking
- Qualified opportunities
- Pipeline progression

---

# 41. Example Baseline Table

This table intentionally contains placeholders rather than fabricated performance results.

| Metric | Before | Pilot | Post-Launch |
|---|---:|---:|---:|
| Median First Response Time | TBD | TBD | TBD |
| Median Qualification Time | TBD | TBD | TBD |
| Correct Routing Rate | TBD | TBD | TBD |
| Human Review Rate | TBD | TBD | TBD |
| Appointment Rate | TBD | TBD | TBD |
| Workflow Failure Rate | N/A | TBD | TBD |

Real implementation data should replace these placeholders.

---

# 42. AI Quality Review

A sample of AI-processed leads can be reviewed manually.

Example review fields:

| Review Item | Pass / Fail |
|---|---|
| Correct service category | |
| Factual summary | |
| Missing data not invented | |
| Correct human-handoff decision | |
| Correct downstream routing | |

Record the sample size and review period.

---

# 43. QA Test Cases

## Test 1 — Clear CRM Automation Enquiry

Input:

```text
"We need a CRM and WhatsApp follow-up for our sales leads."
```

Expected:

```text
Service = CRM Automation
Human Review = No
```

---

## Test 2 — Clear SEO Enquiry

Input:

```text
"We need technical SEO and help improving organic visibility."
```

Expected:

```text
Service = SEO
```

---

## Test 3 — Missing Requirement

Input:

```text
"Please contact me."
```

Expected:

```text
Do not invent service.
Ask approved clarification or send to review.
```

---

## Test 4 — Multiple Services

Input:

```text
"We need SEO as well as CRM automation."
```

Expected:

```text
Follow defined multi-service policy.
Do not arbitrarily discard one requirement.
```

---

## Test 5 — Human Request

Input:

```text
"Can I speak with someone?"
```

Expected:

```text
Human handoff.
AI pauses.
```

---

## Test 6 — Pricing Negotiation

Input:

```text
"Can you reduce your price if we sign for six months?"
```

Expected:

```text
Human handoff according to pricing policy.
No invented discount.
```

---

## Test 7 — Unsupported Service

Input:

```text
"We need a custom ERP built from scratch."
```

Expected:

```text
Unknown / Human Review according to business policy.
```

---

## Test 8 — Duplicate Event

Input:

```text
Same webhook event ID received twice.
```

Expected:

```text
Second event does not repeat consequential actions.
```

---

## Test 9 — AI Failure

Input:

```text
AI API unavailable.
```

Expected:

```text
Fallback to human review.
Lead remains visible.
```

---

## Test 10 — Existing Owner

Input:

```text
Existing active contact already assigned to salesperson.
```

Expected:

```text
Preserve ownership according to policy.
```

---

# 44. Security Controls

The example production design should include:

- Least-privilege API access
- Secure credential storage
- No secrets in prompts
- No secrets in source control
- Validated webhooks where applicable
- Limited AI context
- Protected operational logs
- Appropriate employee permissions

---

# 45. Privacy Controls

The AI should receive only the information required for its task.

For this example:

```text
Needed:
- Enquiry text
- Allowed service categories
- Limited relevant CRM context

Not automatically needed:
- Full CRM history
- Unrelated customer records
- Payment credentials
- Confidential employee notes
```

Actual requirements depend on the implementation.

---

# 46. Deployment Approach

A practical rollout could be:

```text
Internal Testing
↓
Test Contacts
↓
Limited Pilot
↓
Manual QA Sampling
↓
Fix Failures
↓
Controlled Production Rollout
↓
Monitor
↓
Expand if Reliable
```

Do not immediately automate every inbound lead if the workflow has not been validated.

---

# 47. Rollback Plan

Example:

```text
If critical failure occurs:

1. Disable automated AI qualification.
2. Route new leads to manual sales review.
3. Pause automated customer messaging if affected.
4. Identify impacted workflow executions.
5. Correct CRM records if required.
6. Resolve root cause.
7. Run regression tests.
8. Redeploy only after approval.
```

---

# 48. 30-Day Pilot Review

At the end of the pilot, review:

```text
How many eligible leads entered?

How many workflows completed successfully?

How many AI outputs required correction?

How many handoffs occurred?

Were any required handoffs missed?

How quickly were leads assigned?

Did CRM data quality improve or decline?

Were customer messages appropriate?

What was the operating cost?

Should the workflow:
[ ] Expand
[ ] Continue Pilot
[ ] Be Modified
[ ] Be Paused
```

---

# 49. What This Example Demonstrates

This implementation combines:

```text
AI Automation Readiness
        ↓
Opportunity Discovery
        ↓
Workflow Specification
        ↓
CRM Integration
        ↓
AI Interpretation
        ↓
Deterministic Business Rules
        ↓
Human Handoff
        ↓
QA
        ↓
Measurement
```

AI is only one component of the system.

---

# 50. What AI Does Not Control

In this example, AI does not independently control:

- Pricing
- Discounts
- Contracts
- CRM ownership policy
- Final commercial qualification
- Appointment availability
- Opportunity value
- Won/lost decisions
- Customer consent state
- High-risk exceptions

This keeps important business policy explicit.

---

# 51. Core Implementation Principles

1. **Preserve the CRM as the operational system of record.**
2. **Use AI for interpretation of unstructured information.**
3. **Use deterministic rules for business policy.**
4. **Do not allow AI to invent missing customer data.**
5. **Validate structured AI output before downstream actions.**
6. **Protect existing ownership and attribution.**
7. **Build human handoff into the workflow from the beginning.**
8. **Design failures so leads remain recoverable.**
9. **Test duplicate events and workflow collisions.**
10. **Measure results against a real baseline before claiming improvement.**

---

# 52. Complete Example Architecture

```text
INBOUND LEAD
     ↓
VALIDATE
     ↓
NORMALIZE
     ↓
DEDUPLICATE
     ↓
CRM
     ↓
PRESERVE ATTRIBUTION
     ↓
AI INTERPRETATION
     ↓
OUTPUT VALIDATION
     ↓
BUSINESS RULES
     ↓
QUALIFICATION
  ↙    ↓     ↘
YES  CLARIFY  REVIEW
 ↓             ↓
ROUTING      HUMAN
 ↓             ↓
ACKNOWLEDGE ← OWNERSHIP
 ↓
APPOINTMENT
 ↓
FOLLOW-UP
 ↓
OPPORTUNITY
 ↓
PIPELINE
 ↓
OUTCOME
 ↓
MEASUREMENT
```

The purpose of the architecture is not maximum automation.

It is to create a **reliable lead-to-revenue workflow where AI handles narrow interpretation tasks, automation handles repeatable logic, and humans retain control of judgment and commercial decisions**.

---

# Related Resources

- [AI Automation Readiness Checklist](ai-automation-readiness-checklist.md)
- [AI Automation Strategy Framework](ai-automation-strategy-framework.md)
- [AI Automation Opportunity Worksheet](ai-automation-opportunity-worksheet.md)
- [AI Workflow Design Framework](ai-workflow-design-framework.md)
- [AI Workflow Specification Template](ai-workflow-specification-template.md)
- [AI Lead Qualification Framework](ai-lead-qualification-framework.md)
- [CRM + AI Automation Framework](crm-ai-automation-framework.md)
- [WhatsApp + AI Automation Framework](whatsapp-ai-automation-framework.md)
- [AI Agent Human Handoff Framework](ai-agent-human-handoff-framework.md)
- [AI Automation QA Checklist](ai-automation-qa-checklist.md)
- [AI Automation Measurement Framework](ai-automation-measurement-framework.md)
- [AI Automation Playbooks](README.md)

---

## About the Repository

This implementation example is part of **[AI Automation Playbooks](README.md)**, maintained by **[Prashant Rajput](https://github.com/prashant6788)**, Founder of [Touchstone Infotech](https://www.touchstoneinfotech.com/).

The repository focuses on practical systems for:

**AI · Automation · CRM · Lead Management · Workflow Automation · System Integration · Revenue Operations**

---

## Important Note

This document is a fictional and sanitized educational example.

Names, companies, contact details, workflow identifiers and example values are illustrative. No performance figures or customer results are claimed.

Production implementations should be adapted to the specific business process and validated against current platform documentation, security and privacy requirements, applicable regulations, business policies, data sensitivity and real-world testing.

---

## License

This resource is intended to follow the license applicable to the **AI Automation Playbooks** repository.

See [LICENSE](LICENSE) for license details once the repository license is published.
