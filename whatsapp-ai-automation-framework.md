# WhatsApp + AI Automation Framework

## Practical Framework for Designing CRM-Connected WhatsApp Automation With AI and Human Handoff

WhatsApp can become an important operational channel when conversations are connected to CRM data, workflow state, business rules, approved automation and clear human ownership.

AI can add useful interpretation and conversational assistance, but it should not be given uncontrolled authority over customer communication or business decisions.

This framework provides a practical methodology for designing reliable WhatsApp + AI automation systems for lead management, customer communication, appointments and revenue operations.

It is designed for:

- Founders and business owners
- Marketing and sales operations teams
- CRM implementation teams
- Automation consultants
- Customer support teams
- AI implementation teams
- Agencies building WhatsApp-connected business systems

The objective is to move from:

**WhatsApp Message → Identity → CRM Context → Intent → Rules + AI → Action → Human Handoff → CRM Update → Measurement**

---

# 1. Define WhatsApp's Role

Do not automate WhatsApp before deciding what the channel should do.

Possible roles include:

- Lead acknowledgement
- Lead qualification
- FAQ assistance
- Appointment booking
- Appointment reminders
- Rescheduling
- No-show recovery
- Sales follow-up
- Payment-related notifications
- Customer support triage
- Re-engagement where appropriate
- Human sales conversations

Avoid making one automation responsible for every possible customer interaction.

---

# 2. Define the Business Objective

Each workflow should have a clear outcome.

Examples:

| Business Problem | Desired Outcome |
|---|---|
| Leads wait for a reply | Reduce first-response time |
| Sales repeatedly asks the same qualification questions | Capture initial qualification consistently |
| Appointments are missed | Send controlled reminders |
| No-shows are not recovered | Offer a rebooking path |
| Conversations are disconnected from CRM | Synchronize contact and conversation context |
| AI cannot handle unusual questions | Escalate with context |
| Sales misses high-intent replies | Notify the correct owner |
| Customers receive irrelevant follow-ups | Use lifecycle and conversation state |

The goal is not “send more WhatsApp messages.”

The goal is to improve a defined customer or operational process.

---

# 3. Use the Appropriate WhatsApp Business Infrastructure

Production automation should use an approved WhatsApp Business integration appropriate to the business and implementation.

The exact setup may vary by provider and platform.

Before deployment, verify current requirements for:

- Business account setup
- Phone number
- User consent / opt-in
- Message templates
- Conversation rules
- Supported message types
- Quality and messaging limits
- Data handling
- Provider-specific restrictions

WhatsApp policies and platform capabilities change over time. Always verify current official documentation before implementation.

---

# 4. Consent and Communication Eligibility

Automation should not assume that possessing a phone number automatically permits every type of WhatsApp communication.

Record relevant communication state in the CRM where appropriate.

Example:

```text
WhatsApp Number
Consent / Eligibility State
Consent Source
Consent Timestamp
Last Customer Interaction
Communication Status
Opt-Out Status
```

The exact data required depends on the business, jurisdiction and implementation.

---

# 5. Contact Identity

Incoming messages must be associated with the correct CRM record.

Example:

```text
Incoming WhatsApp Message
↓
Normalize Phone Number
↓
Find CRM Contact
├── Found → Load Relevant Context
└── Not Found → Create / Identify According to Policy
```

Avoid creating a new contact for every message.

---

# 6. Normalize Phone Numbers

Phone formatting differences can create duplicates.

Normalize according to an appropriate international format before matching records.

Possible inputs:

```text
9876543210
+91 98765 43210
0091-9876543210
```

should not automatically become three separate contacts when they represent the same number.

---

# 7. Preserve Conversation Context

A useful WhatsApp workflow may need:

- Contact identity
- Current lifecycle stage
- Service/product interest
- Assigned owner
- Appointment status
- Recent conversation
- Current workflow state
- Relevant verified business information

Only provide AI with the context necessary for the task.

Do not expose unrelated CRM data.

---

# 8. Define Conversation State

Do not rely solely on AI memory.

Store operational state explicitly.

Example:

```text
New Enquiry
↓
Awaiting Requirement
↓
Requirement Captured
↓
Awaiting Qualification
↓
Qualified
↓
Appointment Offered
↓
Appointment Booked
```

Other states may include:

```text
Human Handoff
Customer
Support
Opted Out
Closed
```

Conversation state helps prevent repeated or contradictory messages.

---

# 9. Separate Rules, AI and Human Decisions

## Rules

Use deterministic logic for:

- Eligibility
- Routing
- Appointment status
- Follow-up timing
- Existing ownership
- Stop conditions
- Opt-out handling

## AI

Use AI for:

- Intent classification
- Requirement extraction
- Conversation summarization
- FAQ interpretation
- Language understanding
- Suggested response generation

## Humans

Use humans for:

- Complex negotiations
- Complaints
- Sensitive situations
- High-value sales conversations
- Exceptions
- Low-confidence or unsupported requests

A robust architecture combines all three.

---

# 10. AI Intent Classification

Example:

```text
Incoming Message
↓
AI Intent Classification
↓
Allowed Categories:
- New Sales Enquiry
- Existing Lead Follow-Up
- Appointment
- Support
- Pricing Question
- Human Request
- Other
```

Validate the returned category before routing the workflow.

Unknown intent should have a fallback path.

---

# 11. AI Requirement Extraction

Example message:

```text
"We run two salons and want automatic follow-up
for Instagram leads and appointment reminders."
```

Possible structured output:

```json
{
  "business_type": "salon",
  "locations": 2,
  "requirement": [
    "lead follow-up",
    "appointment reminders"
  ],
  "lead_source": "Instagram"
}
```

Do not store inferred information as verified fact unless appropriate.

---

# 12. AI Response Boundaries

Define what AI may and may not do.

### AI May

- Answer approved FAQs
- Ask approved qualification questions
- Summarize requirements
- Explain standard services
- Offer approved next steps
- Help locate an appropriate booking path

### AI May Not

- Invent pricing
- Promise discounts
- Guarantee outcomes
- Confirm unavailable appointments
- Make contractual commitments
- Expose internal notes
- Reveal private customer data
- Continue when escalation is required

Technical controls should enforce important boundaries where possible.

---

# 13. Approved Knowledge

AI responses should use reliable business information.

Potential sources:

- Service descriptions
- Product documentation
- FAQs
- Locations
- Business hours
- Approved pricing information
- Appointment policies
- Cancellation policies
- Qualification rules

Knowledge should be current and maintained.

Do not assume a language model's general knowledge is an authoritative source for business-specific facts.

---

# 14. Structured AI Output

When AI controls downstream workflow logic, prefer structured output.

Example:

```json
{
  "intent": "appointment_request",
  "service": "consultation",
  "location": "chennai",
  "human_handoff": false
}
```

Validate the schema and allowed values before using the result.

---

# 15. Lead Capture From WhatsApp

Example:

```text
New WhatsApp Enquiry
↓
Identify / Create Contact
↓
Preserve Source
↓
Capture Requirement
↓
Update CRM
↓
Qualification
↓
Routing
↓
Next Action
```

If WhatsApp is not the original acquisition source, do not overwrite original attribution automatically.

---

# 16. Qualification Workflow

A conversational qualification flow may collect:

```text
Requirement
Location
Product / Service
Timeline
Budget or Fit Information
Preferred Appointment
```

Only ask questions that affect the next business action.

Avoid turning WhatsApp into an unnecessarily long form.

---

# 17. Example AI Qualification Architecture

```text
Incoming Enquiry
↓
CRM Contact Match
↓
AI Identifies Intent
↓
Required Information Available?
├── No → Ask Approved Clarifying Question
└── Yes
     ↓
AI Extracts Structured Information
↓
Validate Output
↓
Apply Business Rules
↓
Qualified?
├── Yes → Route + Appointment / Sales
├── No → Appropriate Alternative / Nurture
└── Uncertain → Human Review
```

---

# 18. Lead Routing

Routing may depend on:

- Service
- Geography
- Language
- Existing owner
- Business unit
- Lead status
- Qualification
- Availability

Example:

```text
Qualified Lead
↓
Service?
├── SEO → SEO Owner
├── CRM Automation → Automation Owner
└── Other → Sales Coordinator
```

Always define a fallback owner.

---

# 19. Human Handoff

The user should be able to reach a person when appropriate.

Example:

```text
Customer Requests Human
↓
Set AI Status = Paused
↓
Assign Owner
↓
Generate Conversation Summary
↓
Create CRM Task
↓
Notify Owner
↓
Human Continues in Same Channel
```

Do not make customers repeatedly fight the automation to reach a person.

---

# 20. Handoff Triggers

Examples:

- Explicit human request
- Complaint
- Pricing negotiation
- Sensitive request
- High-value opportunity
- AI uncertainty
- Repeated misunderstanding
- Unsupported topic
- Payment dispute
- Workflow error

A handoff is a designed path, not necessarily a failure.

---

# 21. Handoff Summary

A useful internal summary can contain:

```text
Contact:
Current Status:
Intent:
Requirement:
Service Interest:
Location:
Appointment Status:
Key Questions:
Important Context:
Recommended Next Action:
```

Only include information supported by the conversation or verified systems.

---

# 22. Human Takeover State

When a human takes over:

```text
AI Active = FALSE
Human Owner = Assigned
Automation State = Human Handoff
```

Define when AI can resume.

Examples:

- Human explicitly closes the handoff
- Conversation becomes inactive and a defined workflow restarts
- CRM status changes

Do not allow AI and a salesperson to respond simultaneously without coordination.

---

# 23. Appointment Booking

Example:

```text
Qualified Enquiry
↓
Identify Correct Calendar / Location
↓
Offer Booking Path
↓
Appointment Booked
↓
CRM Updated
↓
Confirmation
↓
Reminder Workflow
```

The system should verify actual availability rather than allowing AI to invent time slots.

---

# 24. Appointment Reminders

A reminder workflow may include one or more scheduled messages.

Design based on the business context rather than sending excessive reminders.

```text
Appointment Created
↓
Confirmation
↓
Scheduled Reminder(s)
↓
Appointment Status Check
↓
Stop if Cancelled / Rescheduled
```

Every reminder should check the current appointment state before sending.

---

# 25. Rescheduling

Example:

```text
Customer Requests Reschedule
↓
Identify Existing Appointment
↓
Provide Approved Rescheduling Path
↓
New Appointment Confirmed
↓
Update CRM / Calendar
↓
Cancel Old Reminder Path
↓
Start New Reminder Path
```

Avoid maintaining reminders for the old appointment.

---

# 26. No-Show Recovery

```text
Appointment Marked No-Show
↓
Verify Status
↓
Recovery Already Sent?
├── Yes → Stop
└── No
     ↓
Send Rebooking Message
↓
Customer Rebooks?
├── Yes → Update CRM
└── No → Follow Defined Recovery Policy
```

This workflow usually requires rules more than AI.

---

# 27. Follow-Up Automation

Example:

```text
Lead Waiting for Response
↓
Defined Wait Period
↓
Customer Replied?
├── Yes → Continue Conversation
└── No
     ↓
Eligible for Follow-Up?
├── No → Stop
└── Yes → Send Follow-Up
```

Define:

- Maximum attempts
- Timing
- Business hours
- Eligibility
- Stop conditions
- Human ownership

---

# 28. Avoid Message Collisions

Before sending, check:

```text
Has a human replied recently?
Is another workflow sending a message?
Has the customer already completed the goal?
Has the appointment changed?
Has the opportunity closed?
Has the customer opted out?
```

This reduces contradictory communication.

---

# 29. Message Deduplication

Use appropriate markers to prevent repeated sends.

Possible controls:

- Workflow execution ID
- Message-purpose flag
- Event ID
- Appointment ID
- Last-sent timestamp
- CRM workflow status

Example:

```text
No-Show Event Received
↓
Recovery Message Already Sent for Appointment ID?
├── Yes → Stop
└── No → Send
```

---

# 30. Template-Based Communication

Where approved templates are required, separate:

```text
Business Event
↓
Template Eligibility
↓
Correct Approved Template
↓
Variable Validation
↓
Send
```

Never place unvalidated AI-generated text into template variables if it could create inaccurate or inappropriate communication.

---

# 31. Personalization

Useful personalization may include verified:

- Name
- Service
- Appointment date/time
- Location
- Assigned advisor
- Booking link

Avoid excessive personalization based on inferred or sensitive information.

---

# 32. Multi-Language Conversations

AI may assist language understanding, but design language state explicitly.

Example:

```text
Preferred Language:
English / Hindi / Tamil / Other
```

Validate important business information in supported languages.

Do not assume automatic translation is always accurate enough for sensitive or consequential communication.

---

# 33. Voice Notes and Media

If the implementation supports media processing, define separate workflows for:

- Voice notes
- Images
- Documents
- Video

Example:

```text
Voice Note
↓
Transcription
↓
Validate / Interpret
↓
Intent Classification
↓
Response / Handoff
```

Consider privacy, accuracy, file type, size and retention.

---

# 34. CRM Synchronization

Important WhatsApp events should update CRM state where appropriate.

Examples:

| WhatsApp Event | CRM Action |
|---|---|
| New enquiry | Create/update contact |
| Requirement captured | Update fields |
| Qualified | Update qualification |
| Owner assigned | Update owner |
| Appointment booked | Update appointment/lifecycle |
| Human handoff | Create task/status |
| Opt-out | Update communication status |
| Sale completed | Update opportunity |

Avoid storing critical business state only inside the messaging platform.

---

# 35. Source Attribution

Preserve original acquisition source.

Example:

```text
Original Source = Meta Ads
Current Conversation Channel = WhatsApp
```

Do not automatically change:

```text
Original Source → WhatsApp
```

simply because the lead replied there.

---

# 36. Internal Notifications

Notify teams only when action is needed.

Example:

```text
High-Intent WhatsApp Lead

Contact: [Name]
Requirement: [Summary]
Service: [Service]
Owner: [Owner]
Reason for Alert: Requested consultation
CRM: [Record Link]
```

Avoid flooding internal channels with every automated message.

---

# 37. Error Handling

Plan for:

- WhatsApp provider/API failure
- Invalid phone number
- Template rejection
- Missing variable
- CRM failure
- AI timeout
- Invalid AI output
- Calendar failure
- Webhook duplication
- Authentication expiry

Example:

```text
Send Attempt
↓
Success?
├── Yes → Record Delivery Attempt
└── No
     ↓
Classify Failure
↓
Retry if Appropriate
↓
Still Failed?
↓
Log + Recovery / Alert
```

---

# 38. Retry Strategy

Different failures need different treatment.

```text
Temporary API Error
→ Limited Retry

Invalid Number
→ Do Not Retry Automatically

Authentication Failure
→ Alert Administrator

Invalid Template Variable
→ Stop + Review
```

Do not create infinite retries.

---

# 39. Webhook Reliability

Incoming events may be delayed, duplicated or arrive out of order.

Where relevant:

- Validate webhook authenticity
- Store event IDs
- Deduplicate events
- Handle retries
- Check current CRM state
- Avoid assuming event order

Design downstream actions to tolerate repeated events where practical.

---

# 40. Logging and Auditability

Useful operational fields:

```text
Execution ID
Contact ID
Conversation ID
Message ID
Timestamp
Direction
Workflow
Intent
AI Output Category
Template / Message Type
Owner
Handoff Status
Delivery Status
Error
Final Outcome
```

Do not log sensitive content unnecessarily.

---

# 41. Security and Privacy

Review:

- API credentials
- Webhook security
- CRM permissions
- AI data exposure
- Personal information
- Conversation retention
- Employee access
- Export permissions
- Vendor data handling

Never place credentials or tokens in prompts, public repositories or plain-text workflow documentation.

---

# 42. Opt-Out Handling

Define an immediate stop path.

```text
Opt-Out / Communication Withdrawal
↓
Update CRM
↓
Stop Applicable Automation
↓
Prevent Future Ineligible Sends
```

The exact implementation should follow applicable platform and legal requirements.

---

# 43. Safety for Sensitive Use Cases

Additional safeguards may be required for:

- Healthcare
- Financial services
- Legal services
- Minors
- High-risk transactions
- Sensitive personal data

AI should not be used to make regulated or high-impact decisions merely because the conversation happens on WhatsApp.

---

# 44. Measurement Framework

## Operational

- Workflow success rate
- Message send failures
- AI processing failures
- Human handoff rate
- Median response time
- Manual actions eliminated

## Conversation

- Meaningful reply rate
- Qualification completion
- Handoff completion
- Appointment booking
- Opt-out rate

## Sales

- Qualified leads
- Appointments
- Opportunities
- Won customers
- Pipeline influenced
- Revenue attributed where reliable

## AI Quality

- Intent classification accuracy
- Extraction accuracy
- Human correction rate
- Unsupported-response rate
- Escalation quality

---

# 45. Establish a Baseline

Before automation, record existing performance.

| Metric | Before | After |
|---|---:|---:|
| First Response Time | Baseline | Measure |
| Manual Qualification Time | Baseline | Measure |
| Qualification Completion | Baseline | Measure |
| Appointment Booking Rate | Baseline | Measure |
| No-Show Recovery | Baseline | Measure |
| Human Workload | Baseline | Measure |

Do not claim improvement without a meaningful comparison.

---

# 46. Example End-to-End Architecture

```text
Ads / Website / Referral
          ↓
       Lead
          ↓
         CRM
          ↓
WhatsApp Conversation
          ↓
Identity + State + Context
          ↓
Intent Classification
     ↙          ↓          ↘
   Rules        AI        Human
     ↘          ↓          ↙
       Qualification
          ↓
        Routing
          ↓
Communication / Appointment
          ↓
     Human Sales
          ↓
      Opportunity
          ↓
       Revenue
          ↓
      Measurement
```

---

# 47. Example New-Lead Workflow

```text
WhatsApp Message Received
↓
Normalize Number
↓
Find / Create CRM Contact
↓
Check Communication State
↓
Identify Intent
↓
Existing Customer?
├── Yes → Existing Customer Path
└── No
     ↓
Capture Requirement
↓
AI Extracts Structured Information
↓
Validate
↓
Apply Qualification Rules
↓
Route
↓
Send Appropriate Response
↓
Appointment / Human Handoff / Follow-Up
↓
Update CRM
```

---

# 48. Example Human-Handoff Workflow

```text
Incoming Message
↓
AI Detects Human Request
↓
Set AI Active = FALSE
↓
Set Status = Human Handoff
↓
Generate Factual Summary
↓
Assign CRM Owner
↓
Create Task
↓
Notify Owner
↓
Human Responds
↓
Handoff Closed When Appropriate
```

---

# 49. Example Appointment Workflow

```text
Customer Wants Appointment
↓
Identify Service / Location
↓
Select Correct Calendar
↓
Retrieve / Provide Valid Booking Path
↓
Appointment Created
↓
CRM Updated
↓
Confirmation
↓
Reminder(s)
↓
Outcome
├── Attended
├── Rescheduled
├── Cancelled
└── No-Show → Recovery
```

---

# 50. WhatsApp + AI QA Checklist

## Infrastructure

- [ ] Appropriate WhatsApp Business setup confirmed
- [ ] Current platform requirements reviewed
- [ ] Webhooks secured
- [ ] Credentials stored securely
- [ ] Provider failure path defined

## Contact & CRM

- [ ] Phone normalization tested
- [ ] Duplicate handling tested
- [ ] Contact matching tested
- [ ] Original attribution preserved
- [ ] Conversation state stored
- [ ] Source of truth defined

## Communication

- [ ] Eligibility/consent logic reviewed
- [ ] Approved templates configured where required
- [ ] Variables validated
- [ ] Message collision prevention tested
- [ ] Stop conditions tested
- [ ] Opt-out handling tested

## AI

- [ ] Intent categories defined
- [ ] AI task narrowly scoped
- [ ] Approved knowledge defined
- [ ] Structured output validated
- [ ] Missing data not fabricated
- [ ] Disallowed behavior documented
- [ ] Unsupported requests escalate

## Human Handoff

- [ ] Human-request trigger tested
- [ ] AI pauses appropriately
- [ ] Correct owner receives case
- [ ] Summary is factual
- [ ] Resume/close logic defined

## Appointments

- [ ] Correct calendar selected
- [ ] Availability not invented
- [ ] Confirmation tested
- [ ] Reminder cancellation tested
- [ ] Rescheduling tested
- [ ] No-show recovery deduplicated

## Reliability

- [ ] API failure tested
- [ ] CRM failure tested
- [ ] AI failure tested
- [ ] Duplicate webhook tested
- [ ] Retry limits defined
- [ ] Logs available
- [ ] Recovery path documented

## Measurement

- [ ] Response time measurable
- [ ] Qualification measurable
- [ ] Handoff measurable
- [ ] Appointment outcomes measurable
- [ ] Opportunity/revenue connection defined where possible

---

# 51. WhatsApp + AI Automation Scorecard

| Area | Score |
|---|---:|
| Business Objective | /10 |
| WhatsApp Infrastructure | /10 |
| CRM Integration | /10 |
| Conversation State | /10 |
| AI Task Design | /10 |
| Communication Controls | /10 |
| Human Handoff | /10 |
| Reliability & Recovery | /10 |
| Privacy & Governance | /10 |
| Measurement | /10 |
| **Total** | **/100** |

This is an internal implementation-review score, not an official WhatsApp, Meta or AI-platform score.

---

# 52. 90-Day Implementation Model

## Days 1–30 — Foundation

- [ ] Define WhatsApp use cases
- [ ] Review current platform requirements
- [ ] Define consent/eligibility handling
- [ ] Connect CRM
- [ ] Normalize contact data
- [ ] Define conversation states
- [ ] Map human ownership
- [ ] Establish baseline metrics

## Days 31–60 — Automation & AI

- [ ] Build inbound workflows
- [ ] Add intent classification
- [ ] Add qualification
- [ ] Configure routing
- [ ] Add approved knowledge
- [ ] Build human handoff
- [ ] Connect appointments
- [ ] Implement logging and failure handling

## Days 61–90 — Optimization

- [ ] Review AI quality
- [ ] Analyze handoffs
- [ ] Measure appointments
- [ ] Review message failures
- [ ] Improve qualification questions
- [ ] Reduce unnecessary automation
- [ ] Compare against baseline
- [ ] Prioritize next workflow

---

# 53. Common Mistakes

## Automating Before Defining Consent and Eligibility

Communication controls should be part of the architecture.

## Treating WhatsApp as the CRM

Important customer and pipeline state should live in the appropriate system of record.

## Letting AI Answer Everything

Define supported topics and escalation paths.

## AI and Human Replying Simultaneously

Use explicit takeover state.

## Excessive Follow-Up

Automation should not become spam.

## Ignoring Appointment State

Do not send reminders for cancelled or rescheduled appointments.

## Overwriting Original Lead Source

Conversation channel and acquisition source are different concepts.

## No Deduplication

Repeated events can create repeated messages and tasks.

## No Error Monitoring

Messaging failures need visible recovery paths.

## Measuring Only Message Volume

Measure qualification, appointments, opportunities and customer outcomes.

---

# 54. Core Principles

1. **Define the business purpose of WhatsApp before automating it.**
2. **Use current approved WhatsApp Business infrastructure and policies.**
3. **Keep CRM state separate from conversational memory.**
4. **Use rules where decisions are deterministic.**
5. **Give AI narrow, testable responsibilities.**
6. **Never allow AI to invent business facts.**
7. **Make human handoff immediate and contextual.**
8. **Prevent duplicate messages and workflow collisions.**
9. **Respect communication eligibility, opt-outs and customer state.**
10. **Measure business outcomes, not message volume.**

---

# 55. The WhatsApp + AI Automation System

```text
Customer Message
       ↓
Identity
       ↓
CRM Context
       ↓
Conversation State
       ↓
Intent
       ↓
Rules + AI
       ↓
Qualification / Service
       ↓
Routing
       ↓
Response / Appointment
       ↓
Human Handoff if Required
       ↓
CRM Update
       ↓
Pipeline
       ↓
Outcome
       ↓
Measurement
       ↓
Optimization
```

The objective is not to replace human conversations.

The objective is to create a **controlled, CRM-connected communication system that uses automation for speed, AI for appropriate interpretation, and humans for judgment and relationship ownership**.

---

# Related Resources

- [AI Automation Strategy Framework](ai-automation-strategy-framework.md)
- [AI Workflow Design Framework](ai-workflow-design-framework.md)
- [CRM + AI Automation Framework](crm-ai-automation-framework.md)
- [AI Lead Qualification Framework](ai-lead-qualification-framework.md)
- [AI Automation Readiness Checklist](ai-automation-readiness-checklist.md)
- [AI Automation Playbooks](README.md)

---

## About the Repository

This framework is part of **[AI Automation Playbooks](README.md)**, maintained by **[Prashant Rajput](https://github.com/prashant6788)**, Founder of [Touchstone Infotech](https://www.touchstoneinfotech.com/).

The repository focuses on practical systems for:

**AI · Automation · CRM · Lead Management · WhatsApp Automation · Workflow Automation · System Integration · Revenue Operations**

---

## Important Note

WhatsApp Business requirements, Meta policies, messaging rules, AI models, APIs and automation platforms change continuously.

This framework is intended as a practical architecture and implementation methodology. It is not a substitute for current Meta/WhatsApp documentation, legal advice, privacy review or security review.

Production implementations should be evaluated against current official platform requirements, applicable laws and communication rules, business policies, data sensitivity, vendor capabilities and real-world testing.

---

## License

This resource is intended to follow the license applicable to the **AI Automation Playbooks** repository.

See [LICENSE](LICENSE) for license details once the repository license is published.
