# AI Automation Opportunity Worksheet

## Practical Worksheet for Identifying, Evaluating and Prioritizing AI Automation Opportunities

Use this worksheet before building an automation.

Its purpose is to help teams identify where automation can create measurable value, distinguish deterministic automation from genuine AI use cases, assess implementation readiness, understand risk, and prioritize the right opportunities.

This worksheet can be used for:

- Internal automation discovery
- Client automation audits
- CRM and revenue operations
- Sales and marketing workflows
- Customer support processes
- AI implementation planning
- Automation workshops
- Process improvement sessions

> **Principle:** Start with the business process and outcome—not the AI model or automation tool.

---

# 1. Opportunity Information

```text
Opportunity Name:

Business / Department:

Process Owner:

Prepared By:

Date:

Current Status:
[ ] Idea
[ ] Discovery
[ ] Approved for Investigation
[ ] Planned
[ ] In Development
[ ] Existing Process Review
```

---

# 2. Business Problem

## What problem are we trying to solve?

```text
____________________________________________________________

____________________________________________________________

____________________________________________________________
```

## Why does this problem matter?

```text
____________________________________________________________

____________________________________________________________
```

## Who is affected?

- [ ] Customers
- [ ] Sales
- [ ] Marketing
- [ ] Support
- [ ] Operations
- [ ] Finance
- [ ] Management
- [ ] Other: ______________________

---

# 3. Desired Business Outcome

What should improve if this automation works?

- [ ] Response time
- [ ] Processing time
- [ ] Manual workload
- [ ] Data accuracy
- [ ] Lead qualification
- [ ] Lead routing
- [ ] Follow-up completion
- [ ] Appointment booking
- [ ] Customer experience
- [ ] Pipeline visibility
- [ ] Conversion
- [ ] Revenue attribution
- [ ] Reporting
- [ ] Other: ______________________

### Primary Outcome

```text
____________________________________________________________
```

### How will success be measured?

```text
Metric:

Current Baseline:

Target / Direction of Improvement:

Measurement Source:
```

Do not invent a baseline if reliable historical data is unavailable.

---

# 4. Current Process

Describe how the process works today.

```text
Trigger
↓
____________________________________________________________
↓
____________________________________________________________
↓
____________________________________________________________
↓
____________________________________________________________
↓
Current Outcome
```

### Current Process Notes

```text
____________________________________________________________

____________________________________________________________

____________________________________________________________
```

---

# 5. Process Trigger

What starts the process?

- [ ] Form submission
- [ ] Incoming message
- [ ] Incoming email
- [ ] Phone call / missed call
- [ ] New CRM record
- [ ] CRM field/stage change
- [ ] Appointment event
- [ ] Payment event
- [ ] Support request
- [ ] API / webhook event
- [ ] Scheduled time
- [ ] Employee action
- [ ] Other: ______________________

### Exact Trigger

```text
____________________________________________________________
```

---

# 6. Current Manual Actions

List repetitive human actions.

| Step | Manual Action | Role | Approx. Time | Frequency |
|---|---|---|---:|---:|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |

### Total Estimated Manual Time

```text
Per Case: ____________________

Cases per Week / Month: ____________________

Estimated Total Time: ____________________
```

Treat time savings as estimates until validated.

---

# 7. Friction Analysis

Which problems occur today?

- [ ] Slow response
- [ ] Repetitive data entry
- [ ] Missed follow-up
- [ ] Inconsistent decisions
- [ ] Duplicate records
- [ ] Manual lead assignment
- [ ] Disconnected systems
- [ ] Repetitive customer questions
- [ ] Poor reporting
- [ ] Employee dependency
- [ ] Manual status checking
- [ ] Data-quality problems
- [ ] High processing volume
- [ ] Frequent errors
- [ ] Other: ______________________

### Biggest Friction Point

```text
____________________________________________________________
```

### Business Impact of This Friction

```text
____________________________________________________________
```

---

# 8. Frequency

How often does this process occur?

- [ ] Multiple times per hour
- [ ] Multiple times per day
- [ ] Daily
- [ ] Weekly
- [ ] Monthly
- [ ] Occasionally

### Approximate Volume

```text
Cases per day: __________

Cases per month: __________
```

Higher frequency can increase automation value, but frequency alone does not justify automation.

---

# 9. Repeatability

How standardized is the process?

- [ ] Highly repeatable
- [ ] Mostly repeatable with some exceptions
- [ ] Frequently requires judgment
- [ ] Highly variable
- [ ] Not yet understood

### Which steps follow clear rules?

```text
____________________________________________________________
```

### Which steps require interpretation?

```text
____________________________________________________________
```

### Which steps require human judgment?

```text
____________________________________________________________
```

---

# 10. Automation vs AI Assessment

For every major task, decide what is actually required.

| Task | Rule-Based Automation | AI-Assisted | Human | Notes |
|---|:---:|:---:|:---:|---|
| | [ ] | [ ] | [ ] | |
| | [ ] | [ ] | [ ] | |
| | [ ] | [ ] | [ ] | |
| | [ ] | [ ] | [ ] | |
| | [ ] | [ ] | [ ] | |

### Rule

Use normal automation when the task can be handled reliably with deterministic logic.

Use AI when the task genuinely requires interpretation, classification, extraction, summarization or language generation.

Keep a human involved where judgment, approval or risk requires it.

---

# 11. Potential AI Tasks

Does the process require any of these?

- [ ] Intent classification
- [ ] Text classification
- [ ] Requirement extraction
- [ ] Structured data extraction
- [ ] Conversation summarization
- [ ] Document summarization
- [ ] Suggested response
- [ ] FAQ interpretation
- [ ] Language understanding
- [ ] Content generation
- [ ] Next-action suggestion
- [ ] No AI required
- [ ] Other: ______________________

### Proposed AI Task

```text
AI should:

____________________________________________________________

AI should NOT:

____________________________________________________________
```

Keep the AI responsibility narrow and testable.

---

# 12. AI Input

What information would the AI need?

- [ ] Customer message
- [ ] Form submission
- [ ] CRM fields
- [ ] Conversation history
- [ ] Approved knowledge base
- [ ] Product/service information
- [ ] Document
- [ ] Call transcript
- [ ] Other: ______________________

### Required AI Context

```text
____________________________________________________________
```

### Is any sensitive information included?

- [ ] No
- [ ] Yes
- [ ] Unsure

If yes or unsure, review privacy, security and vendor requirements before implementation.

---

# 13. Expected AI Output

What should AI return?

```text
____________________________________________________________
```

Can the output be constrained?

- [ ] Yes — structured output
- [ ] Yes — approved categories
- [ ] Partially
- [ ] No
- [ ] Unsure

### Example Output

```text
____________________________________________________________
```

### Fallback if AI cannot produce a reliable output

```text
____________________________________________________________
```

---

# 14. Systems Involved

List every system involved.

| System | Purpose | Data Read | Data Written | Integration Available? |
|---|---|---|---|---|
| CRM | | | | |
| Website / Form | | | | |
| Messaging | | | | |
| Calendar | | | | |
| Payment | | | | |
| Analytics | | | | |
| Other | | | | |

---

# 15. Integration Readiness

How can systems communicate?

- [ ] Native integration
- [ ] API
- [ ] Webhook
- [ ] Integration platform
- [ ] Database
- [ ] File import/export
- [ ] Manual only
- [ ] Unknown

### Known Integration Constraints

```text
____________________________________________________________
```

---

# 16. Source of Truth

Define the authoritative system.

| Data | Source of Truth |
|---|---|
| Contact | |
| Lead source | |
| Qualification | |
| Owner | |
| Appointment | |
| Payment | |
| Opportunity | |
| Conversation | |
| Other | |

Do not automate critical updates until ownership of important data is clear.

---

# 17. Data Readiness

Rate current data quality.

```text
[ ] Strong
[ ] Acceptable
[ ] Weak
[ ] Unknown
```

Check:

- [ ] Required fields exist
- [ ] Field definitions are clear
- [ ] Duplicates are controlled
- [ ] Data formats are consistent
- [ ] Historical data is usable
- [ ] Source attribution exists
- [ ] Ownership data is reliable
- [ ] Consent/communication state exists where required

### Main Data Gap

```text
____________________________________________________________
```

---

# 18. Human Handoff

Does the workflow need human escalation?

- [ ] Yes
- [ ] No
- [ ] Unsure

Potential triggers:

- [ ] Customer requests human
- [ ] AI uncertainty
- [ ] Complaint
- [ ] High-value opportunity
- [ ] Pricing negotiation
- [ ] Sensitive request
- [ ] Unsupported topic
- [ ] Workflow failure
- [ ] Approval required
- [ ] Other: ______________________

### Handoff Owner

```text
____________________________________________________________
```

### Context the Human Needs

```text
____________________________________________________________
```

---

# 19. Risk Assessment

Rate each risk.

| Risk | Low | Medium | High | Notes |
|---|:---:|:---:|:---:|---|
| Incorrect AI output | [ ] | [ ] | [ ] | |
| Wrong customer communication | [ ] | [ ] | [ ] | |
| Data overwrite | [ ] | [ ] | [ ] | |
| Duplicate action | [ ] | [ ] | [ ] | |
| Privacy / sensitive data | [ ] | [ ] | [ ] | |
| Financial consequence | [ ] | [ ] | [ ] | |
| Legal / regulatory | [ ] | [ ] | [ ] | |
| Customer experience | [ ] | [ ] | [ ] | |
| Integration failure | [ ] | [ ] | [ ] | |
| Human dependency | [ ] | [ ] | [ ] | |

### Highest-Risk Failure

```text
____________________________________________________________
```

### Required Safeguard

```text
____________________________________________________________
```

---

# 20. Failure Impact

What happens if the automation fails?

- [ ] Minor inconvenience
- [ ] Manual recovery required
- [ ] Lead/customer may be missed
- [ ] Incorrect communication may be sent
- [ ] Data may become incorrect
- [ ] Revenue opportunity may be affected
- [ ] Significant customer impact
- [ ] High-risk consequence

### Recovery Path

```text
____________________________________________________________
```

---

# 21. Error Handling Requirements

Check what is needed.

- [ ] Input validation
- [ ] Duplicate prevention
- [ ] Retry logic
- [ ] API failure handling
- [ ] AI failure fallback
- [ ] Human recovery task
- [ ] Error logging
- [ ] Administrator alert
- [ ] Rollback
- [ ] Manual override

---

# 22. Communication Assessment

Does the workflow send customer communication?

- [ ] Yes
- [ ] No

If yes:

- [ ] Channel eligibility reviewed
- [ ] Consent/permission considered
- [ ] Approved messaging available
- [ ] Stop conditions defined
- [ ] Opt-out handling defined
- [ ] Human takeover defined
- [ ] Business hours considered
- [ ] Message collision prevention required

### Channel(s)

```text
____________________________________________________________
```

---

# 23. Volume and Scale

Expected volume:

```text
Daily: __________

Monthly: __________

Peak Volume: __________
```

Could volume create:

- [ ] API limits
- [ ] Messaging limits
- [ ] AI/API cost concerns
- [ ] Human-review backlog
- [ ] Queue delays
- [ ] CRM performance issues
- [ ] No known issue

---

# 24. Cost Estimate

### One-Time

```text
Discovery / Design: ____________________

Implementation: ____________________

Testing: ____________________

Other: ____________________
```

### Recurring

```text
Automation Platform: ____________________

CRM: ____________________

AI / API: ____________________

Messaging: ____________________

Infrastructure: ____________________

Maintenance: ____________________

Human Review: ____________________
```

Use ranges when exact costs are unknown.

---

# 25. Expected Value

Potential value may come from:

- [ ] Time saved
- [ ] Faster response
- [ ] Error reduction
- [ ] Better follow-up
- [ ] Better qualification
- [ ] Recovered opportunities
- [ ] Increased capacity
- [ ] Better customer experience
- [ ] Improved reporting
- [ ] Revenue impact
- [ ] Other: ______________________

### Expected Value

```text
____________________________________________________________
```

Separate measurable value from assumptions.

---

# 26. Automation Opportunity Score

Score each area from 1 to 5.

```text
1 = Weak
3 = Moderate
5 = Strong
```

| Factor | Score |
|---|---:|
| Process Frequency | /5 |
| Manual Effort | /5 |
| Repeatability | /5 |
| Business Impact | /5 |
| Data Readiness | /5 |
| Integration Readiness | /5 |
| Measurement Readiness | /5 |
| AI Suitability (if AI is needed) | /5 |
| Human Handoff Readiness | /5 |
| Operational Ownership | /5 |

### Positive Opportunity Score

```text
____ / 50
```

This score is an internal prioritization aid, not a universal automation benchmark.

---

# 27. Complexity Score

Score from 1 to 5.

```text
1 = Low Complexity
5 = High Complexity
```

| Factor | Score |
|---|---:|
| Number of Systems | /5 |
| Integration Complexity | /5 |
| Data Complexity | /5 |
| AI Complexity | /5 |
| Exception Frequency | /5 |
| Security / Privacy Complexity | /5 |
| Human Workflow Complexity | /5 |
| Maintenance Requirement | /5 |

### Complexity

```text
____ / 40
```

---

# 28. Risk Score

Score from 1 to 5.

```text
1 = Low Risk
5 = High Risk
```

| Factor | Score |
|---|---:|
| Customer Impact | /5 |
| Incorrect AI Output Impact | /5 |
| Data Risk | /5 |
| Financial Risk | /5 |
| Compliance / Policy Risk | /5 |
| Recovery Difficulty | /5 |

### Risk

```text
____ / 30
```

Do not combine these scores mechanically into an automated go/no-go decision.

High-risk opportunities may still be valuable but require stronger controls.

---

# 29. Priority Matrix

Place the opportunity into one category.

## Quick Win

```text
High Value
Low–Moderate Complexity
Manageable Risk
```

## Strategic Automation

```text
High Value
Higher Complexity
Worth Structured Investment
```

## Operational Improvement

```text
Moderate Value
Useful Efficiency Gain
```

## Investigate Further

```text
Potential Value
But Important Information Missing
```

## Defer

```text
Low Value
or
High Complexity / Risk Without Sufficient Benefit
```

### Selected Category

```text
[ ] Quick Win
[ ] Strategic Automation
[ ] Operational Improvement
[ ] Investigate Further
[ ] Defer
```

---

# 30. Automation Recommendation

Select one.

```text
[ ] Automate with deterministic rules only

[ ] Use rules + limited AI assistance

[ ] Use AI + deterministic controls + human handoff

[ ] Improve the manual process before automating

[ ] Run a small pilot first

[ ] Do not automate at this stage
```

### Reason

```text
____________________________________________________________

____________________________________________________________
```

---

# 31. Proposed Future Workflow

Sketch the recommended workflow.

```text
Trigger
↓
________________________________________
↓
Validation
↓
________________________________________
↓
Rules / AI
↓
________________________________________
↓
Action
↓
________________________________________
↓
Human Handoff if Required
↓
________________________________________
↓
System Update
↓
________________________________________
↓
Measurement
```

---

# 32. Minimum Viable Automation

What is the smallest useful version?

```text
____________________________________________________________

____________________________________________________________
```

### What should NOT be included in Version 1?

```text
____________________________________________________________

____________________________________________________________
```

Start with the smallest workflow that can prove value safely.

---

# 33. Pilot Plan

```text
Pilot Scope:

Users / Records Included:

Duration:

Workflow Owner:

Technical Owner:

Success Metrics:

Failure Threshold / Stop Condition:

Review Date:
```

---

# 34. Success Metrics

Choose only metrics relevant to this opportunity.

### Reliability

- [ ] Workflow success rate
- [ ] Error rate
- [ ] Recovery rate

### Efficiency

- [ ] Processing time
- [ ] Manual time
- [ ] Human intervention rate
- [ ] Throughput

### AI Quality

- [ ] Classification accuracy
- [ ] Extraction accuracy
- [ ] Valid structured output
- [ ] Human correction rate
- [ ] Unsupported response rate

### Business

- [ ] Response time
- [ ] Qualified leads
- [ ] Appointments
- [ ] Follow-up completion
- [ ] Opportunities
- [ ] Pipeline
- [ ] Revenue
- [ ] Customer outcome

---

# 35. Ownership

```text
Business Owner:

Technical Owner:

CRM Owner:

Human Handoff Owner:

Reporting Owner:

Approver:
```

Every production automation should have an accountable owner.

---

# 36. Dependencies

What must happen before implementation?

- [ ] CRM cleanup
- [ ] API access
- [ ] Webhook access
- [ ] Messaging approval
- [ ] Knowledge-base creation
- [ ] Data mapping
- [ ] Security review
- [ ] Privacy review
- [ ] Business-rule approval
- [ ] Staff training
- [ ] Reporting setup
- [ ] Other: ______________________

### Critical Dependency

```text
____________________________________________________________
```

---

# 37. Final Opportunity Summary

```text
Opportunity:

Problem:

Primary Outcome:

Current Manual Effort:

Recommended Automation Type:

AI Role:

Human Role:

Key Systems:

Primary Risk:

Primary Safeguard:

Opportunity Score: ____ / 50

Complexity Score: ____ / 40

Risk Score: ____ / 30

Priority:

Pilot Recommended?
[ ] Yes
[ ] No

Decision:
[ ] Proceed
[ ] Investigate
[ ] Defer
[ ] Reject
```

---

# 38. Executive One-Page Version

For quick discovery sessions:

```text
PROCESS
What process are we reviewing?

PROBLEM
What is slow, repetitive, inconsistent or error-prone?

VOLUME
How often does it happen?

MANUAL EFFORT
How much human work is involved?

BUSINESS IMPACT
Why does it matter?

RULES
Which decisions are deterministic?

AI
Which tasks require interpretation?

HUMAN
Where is judgment required?

SYSTEMS
Which tools need to connect?

DATA
Is the required data reliable?

RISK
What happens if automation is wrong?

MEASUREMENT
How will improvement be proven?

RECOMMENDATION
Automate / Pilot / Improve Process / Defer
```

---

# 39. Example Opportunity — Inbound Lead Qualification

> Illustrative example only.

### Problem

Salespeople manually review every inbound enquiry before assigning it.

### Current Process

```text
Website Form
↓
CRM
↓
Sales Coordinator Reads Enquiry
↓
Identifies Service
↓
Checks Location
↓
Assigns Salesperson
↓
Sends Acknowledgement
```

### Opportunity

Use:

```text
Rule-Based Validation
+
AI Requirement Extraction
+
Deterministic Routing
+
Human Review for Exceptions
```

### AI Role

```text
Extract:
- service interest
- requirement summary
- relevant information contained in free text
```

### AI Does Not

```text
Decide pricing
Promise service eligibility
Negotiate
Create unsupported customer facts
```

### Human Handoff

Trigger when:

- Intent is unclear
- High-value/custom requirement appears
- Customer asks for human
- AI output fails validation

### Measurement

- Median qualification time
- Classification accuracy
- Human-review rate
- Assignment time
- Qualified-to-appointment rate

---

# 40. Common Opportunity-Discovery Mistakes

## Starting With a Tool

Do not begin with:

> We bought an AI platform. What can we automate?

Start with the process.

---

## Automating Every Repetitive Task

Some tasks are too rare or low-value to justify maintenance.

---

## Using AI for Deterministic Logic

If a rule solves the problem reliably, use the rule.

---

## Ignoring Exceptions

A workflow that works only on the happy path is not production-ready.

---

## No Human Owner

Automation does not remove operational accountability.

---

## No Baseline

Without baseline measurement, value is difficult to prove.

---

## Ignoring Integration Complexity

A simple business idea can require difficult system integration.

---

## Treating Time Saved as Guaranteed Profit

Saved time creates capacity; it does not automatically create cash savings.

---

# 41. Core Principles

1. **Start with the business problem.**
2. **Map the current process before designing the future one.**
3. **Use rules where rules are sufficient.**
4. **Use AI only for tasks that benefit from interpretation.**
5. **Keep human judgment where consequences require it.**
6. **Assess data and integration readiness before implementation.**
7. **Design failure and recovery paths early.**
8. **Prioritize value relative to complexity and risk.**
9. **Pilot uncertain automations before scaling.**
10. **Measure the business outcome after deployment.**

---

# Related Resources

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

This worksheet is part of **[AI Automation Playbooks](README.md)**, maintained by **[Prashant Rajput](https://github.com/prashant6788)**, Founder of [Touchstone Infotech](https://www.touchstoneinfotech.com/).

The repository focuses on practical systems for:

**AI · Automation · CRM · Lead Management · Workflow Automation · System Integration · Revenue Operations**

---

## Important Note

This worksheet is a planning and prioritization tool.

Its scores are internal decision aids and should not be interpreted as universal AI readiness, risk or ROI benchmarks.

Production implementations should be evaluated against the specific business process, current platform documentation, security and privacy requirements, applicable regulations, data sensitivity, technical constraints and real-world testing.

---

## License

This resource is intended to follow the license applicable to the **AI Automation Playbooks** repository.

See [LICENSE](LICENSE) for license details once the repository license is published.
