# AI Automation Measurement Framework

## Practical Framework for Measuring Reliability, Efficiency, AI Quality and Business Impact

AI automation should not be judged by how many workflows run or how many messages are sent.

The real question is:

> Does the automation improve the underlying business process in a reliable, measurable and economically useful way?

This framework provides a practical measurement system for AI-assisted automation across operations, CRM, sales, customer communication and revenue workflows.

It is designed for:

- Founders and business owners
- Revenue operations teams
- Sales and marketing operations
- CRM teams
- Automation consultants
- AI implementation teams
- Product and support operations
- Agencies delivering automation systems

The objective is to measure:

**Reliability → Efficiency → AI Quality → Human Intervention → Conversion → Pipeline → Revenue → Improvement**

---

# 1. Start With the Business Outcome

Do not begin with workflow metrics.

Begin with the intended business result.

Examples:

| Automation Use Case | Primary Outcome |
|---|---|
| Lead acknowledgement | Faster first response |
| AI qualification | More consistent qualification |
| Lead routing | Faster assignment |
| Appointment reminders | Fewer missed appointments |
| No-show recovery | More recovered appointments |
| AI support triage | Faster resolution and better routing |
| CRM synchronization | Less manual data entry |
| Sales follow-up | Higher follow-up completion |
| AI summaries | Reduced employee review time |
| Revenue workflow | Better source-to-revenue visibility |

The metric system should reflect the purpose of the workflow.

---

# 2. Create a Baseline Before Automation

Without a baseline, improvement claims are difficult to support.

Record the current process before deployment.

Example:

| Metric | Before Automation | After Automation |
|---|---:|---:|
| Median First Response Time | | |
| Manual Processing Time | | |
| Qualification Completion Rate | | |
| Lead Assignment Time | | |
| Follow-Up Completion Rate | | |
| Appointment Rate | | |
| No-Show Rate | | |
| Error Rate | | |
| Human Intervention Time | | |

Do not estimate baselines after deployment if reliable historical data is unavailable.

Mark missing data honestly.

---

# 3. Measurement Layers

A useful automation measurement model includes six layers.

## Layer 1 — System Reliability

Did the workflow execute correctly?

## Layer 2 — Operational Efficiency

Did it reduce repetitive effort or processing time?

## Layer 3 — AI Quality

Were AI-assisted outputs accurate and useful?

## Layer 4 — Human Intervention

Did the workflow escalate appropriately?

## Layer 5 — Customer / Revenue Outcomes

Did the process improve conversion, appointments, pipeline or customer experience?

## Layer 6 — Economics

Did the value justify implementation and operating cost?

---

# 4. System Reliability Metrics

Measure whether the automation works technically.

Possible metrics:

- Workflow executions
- Successful executions
- Failed executions
- Workflow success rate
- API errors
- Authentication failures
- Retry rate
- Timeout rate
- Duplicate event rate
- Recovery rate
- Average processing time
- Queue backlog

A workflow that produces strong business outcomes only when it runs correctly is not reliable enough.

---

# 5. Workflow Success Rate

Simple formula:

```text
Successful Workflow Executions
÷
Total Eligible Workflow Executions
×
100
```

Example:

```text
940 successful
÷
1,000 eligible executions
=
94% workflow success rate
```

Define what “successful” means for each workflow.

A technical HTTP success response does not necessarily mean the business workflow succeeded.

---

# 6. End-to-End Success

Measure the complete workflow, not just individual API calls.

Example:

```text
Lead Captured
↓
CRM Updated
↓
AI Classification Completed
↓
Owner Assigned
↓
Acknowledgement Sent
```

A workflow should be considered successful only if all required critical steps complete or an approved fallback path is used.

---

# 7. Failure Classification

Classify failures.

Example:

| Failure Type | Examples |
|---|---|
| Input | Missing/invalid data |
| Integration | API unavailable |
| Authentication | Expired credential |
| AI | Invalid/unsupported output |
| Business Rule | No valid route found |
| Communication | Message send failed |
| Duplicate | Event already processed |
| Human Dependency | Required review not completed |

Failure categories make root-cause analysis possible.

---

# 8. Recovery Metrics

Measure:

- Failures recovered automatically
- Failures requiring human intervention
- Time to recovery
- Unresolved failures
- Repeat failures by type

A strong workflow is not one that never fails.

It is one that fails visibly and recovers predictably.

---

# 9. Processing Time

Measure:

```text
Trigger Timestamp
→
Workflow Completion Timestamp
```

Possible metrics:

- Median processing time
- 90th percentile processing time
- Maximum processing time
- Time by workflow stage

For customer-facing workflows, time-to-action may matter more than total workflow duration.

---

# 10. Operational Efficiency

Measure whether the workflow reduced manual work.

Potential metrics:

- Manual actions eliminated
- Employee minutes saved
- Data entry reduced
- Number of systems manually updated
- Manual follow-ups reduced
- Review time reduced
- Cases handled per employee
- Processing throughput

Avoid assuming all saved time becomes financial savings.

---

# 11. Time Saved

A simple estimation model:

```text
Manual Time Per Task
-
Human Time After Automation
=
Time Saved Per Task
```

Then:

```text
Time Saved Per Task
×
Number of Tasks
=
Estimated Time Saved
```

Example:

```text
5 minutes manual
-
1 minute review
=
4 minutes saved

4 minutes
×
500 monthly cases
=
2,000 minutes
=
33.3 hours
```

Label modeled estimates clearly.

---

# 12. Automation Rate

Useful operational metric:

```text
Cases Completed Without Human Intervention
÷
Total Eligible Cases
×
100
```

Do not optimize this number blindly.

A lower automation rate may be appropriate for high-risk workflows.

---

# 13. Human Intervention Rate

```text
Cases Requiring Human Action
÷
Total Eligible Cases
×
100
```

Break intervention into:

- Planned human review
- Customer-requested handoff
- AI uncertainty
- Workflow error
- Policy escalation
- High-value commercial escalation

These categories have different meanings.

---

# 14. AI Quality Metrics

AI-assisted workflows should measure the quality of the AI task.

Possible metrics:

- Classification accuracy
- Extraction accuracy
- Structured-output validity
- Summary correction rate
- Response approval rate
- Unsupported-response rate
- Human override rate
- Escalation accuracy

Use task-specific metrics rather than one generic “AI accuracy” score.

---

# 15. Classification Accuracy

For classification tasks:

```text
Correct AI Classifications
÷
Reviewed Classifications
×
100
```

Use a manually reviewed sample where full review is impractical.

Document:

- Sample size
- Review criteria
- Reviewer
- Time period

---

# 16. Extraction Accuracy

Example fields:

- Service interest
- Location
- Timeline
- Budget
- Product
- Appointment request

Measure per field where possible.

Example:

| Field | Correct | Total Reviewed | Accuracy |
|---|---:|---:|---:|
| Service | | | |
| Location | | | |
| Timeline | | | |

A workflow may be strong on one field and weak on another.

---

# 17. Structured Output Validity

If AI returns JSON or another structured format:

```text
Valid Outputs
÷
Total AI Outputs
×
100
```

Also track:

- Schema failures
- Missing required keys
- Invalid allowed values
- Wrong data types

A syntactically valid output can still be factually wrong.

---

# 18. Summary Quality

For AI summaries, consider:

- Factual accuracy
- Missing critical context
- Unsupported inference
- Clarity
- Usefulness to employee

Example review scale:

```text
2 = Accurate and useful
1 = Usable with correction
0 = Incorrect or misleading
```

Track average and correction rate.

---

# 19. Unsupported Response Rate

Track responses that contain claims not supported by:

- Customer conversation
- CRM data
- Approved knowledge
- Business rules

Formula:

```text
Unsupported Responses
÷
Reviewed AI Responses
×
100
```

This metric is particularly important in customer-facing workflows.

---

# 20. Handoff Quality

A handoff should be measured on more than volume.

Possible metrics:

- Correct escalation rate
- False handoff rate
- Missed handoff rate
- Correct routing rate
- Reassignment rate
- Human response time
- Handoff resolution rate
- Summary correction rate

For deeper methodology, see the [AI Agent Human Handoff Framework](ai-agent-human-handoff-framework.md).

---

# 21. False Handoff Rate

A false handoff occurs when a case was escalated unnecessarily.

```text
Unnecessary Handoffs
÷
Reviewed Handoffs
×
100
```

Do not reduce this metric at the expense of safety.

---

# 22. Missed Handoff Rate

More important:

```text
Cases That Should Have Escalated But Did Not
÷
Reviewed Cases Requiring Escalation
×
100
```

Examples:

- Customer asked for human
- Complaint stayed automated
- AI improvised pricing
- Sensitive request remained automated

Missed handoffs are often high-priority QA findings.

---

# 23. Customer Experience Metrics

Depending on the workflow:

- First-response time
- Meaningful response time
- Resolution time
- Appointment confirmation
- Follow-up completion
- Customer reply rate
- Rebooking rate
- Opt-out rate
- Complaint rate
- Escalation rate

Do not use response rate alone as proof of a good customer experience.

---

# 24. First Response Time

Measure from:

```text
Eligible Customer Event
→
First Meaningful Response
```

Distinguish:

- Automated acknowledgement
- Meaningful answer
- Human response

These are not always equivalent.

---

# 25. Follow-Up Completion

```text
Eligible Follow-Ups Completed
÷
Total Eligible Follow-Ups
×
100
```

Compare before and after automation.

---

# 26. Lead Qualification Metrics

Possible funnel:

```text
Inbound Leads
↓
Qualification Started
↓
Qualification Completed
↓
Qualified
↓
Appointment
↓
Opportunity
```

Track:

- Qualification completion rate
- Qualified lead rate
- Time to qualification
- Human review rate
- Qualification-to-appointment rate

---

# 27. Routing Metrics

Useful measures:

- Assignment time
- Correct routing rate
- Reassignment rate
- Unassigned lead count
- Leads assigned to fallback queue
- Owner response time

Routing speed is useful only if routing quality remains high.

---

# 28. Appointment Metrics

For booking workflows:

- Appointment booking rate
- Time to booking
- Confirmation delivery rate
- Reminder delivery
- Attendance rate
- Cancellation rate
- Reschedule rate
- No-show rate
- No-show recovery rate

---

# 29. No-Show Recovery Rate

Example:

```text
No-Shows Who Rebooked
÷
Eligible No-Shows Contacted
×
100
```

Measure recovered appointments, not only recovery messages sent.

---

# 30. CRM Data Quality Metrics

Automation should improve, not damage, CRM quality.

Track:

- Duplicate contacts
- Missing required fields
- Incorrect field values
- Invalid lifecycle states
- Unassigned records
- Attribution completeness
- Stage inconsistencies
- AI-generated fields corrected by humans

---

# 31. Pipeline Metrics

For sales-related automation:

- Qualified opportunities
- Opportunity creation rate
- Pipeline value
- Average opportunity value
- Stage progression
- Win rate
- Sales cycle length
- Lost reason distribution

Do not attribute pipeline improvement to automation without considering other changes.

---

# 32. Revenue Metrics

Where attribution is reliable:

- Revenue from automation-assisted leads
- Revenue from recovered opportunities
- Revenue influenced by automated workflows
- New customers
- Revenue per qualified lead
- Revenue per appointment

Clearly define the attribution model.

---

# 33. Attribution Levels

Use categories such as:

## Directly Attributed

Automation is directly linked to a measurable outcome.

Example:

```text
No-show recovery workflow
→
Customer rebooks
→
Appointment converts
```

## Assisted

Automation contributed but was not the sole cause.

Example:

```text
AI qualification
→
Human salesperson closes deal
```

## Operational Contribution

Automation improved the process but direct revenue attribution is not reliable.

Example:

```text
Automated CRM synchronization
```

Avoid forcing all automation into direct-revenue attribution.

---

# 34. Cost Measurement

Track operating costs such as:

- Automation platform
- CRM
- AI model/API usage
- Messaging cost
- Integration platform
- Infrastructure
- Implementation time
- Maintenance
- Human review time

Do not exclude human oversight from cost calculations.

---

# 35. AI Cost per Workflow

Example:

```text
Monthly AI/API Cost
÷
Successful AI-Assisted Cases
=
AI Cost per Successful Case
```

For token/API-based systems, also monitor cost by:

- Workflow
- Model
- Customer
- Conversation
- Task

---

# 36. Cost per Qualified Lead

Where relevant:

```text
Automation Operating Cost
÷
Qualified Leads Generated / Processed
```

Interpret carefully because many workflows support leads created by other channels.

---

# 37. Automation Value Model

A practical value equation:

```text
Estimated Labor Value
+
Recovered Opportunities
+
Conversion Improvement
+
Error Reduction Value
+
Service Capacity Increase
-
Software Costs
-
AI/API Costs
-
Messaging Costs
-
Implementation Costs
-
Maintenance Costs
-
Human Review Costs
```

Not every component can be converted reliably into money.

Use conservative assumptions.

---

# 38. ROI

Simple model:

```text
Measured / Attributed Benefit - Total Cost
------------------------------------------
               Total Cost
× 100
```

Do not report ROI where benefits are mostly speculative.

For some workflows, use operational KPIs instead.

---

# 39. Payback Period

```text
Implementation Cost
÷
Monthly Net Measured Benefit
=
Estimated Payback Period
```

Use only when monthly benefit is reasonably stable and measurable.

---

# 40. Capacity Improvement

Automation may increase throughput without reducing headcount.

Example metrics:

- Leads processed per employee
- Support cases per employee
- Appointments managed per coordinator
- Conversations handled per salesperson
- Manual tasks per case

This may be more useful than “hours saved.”

---

# 41. Quality vs Efficiency Trade-Off

Do not optimize speed at the expense of quality.

Example:

```text
Response Time improves 80%
BUT
Incorrect Qualification rises 20%
```

The automation may be worse overall.

Report efficiency and quality together.

---

# 42. Balanced Scorecard

Use four dimensions:

| Dimension | Example Metrics |
|---|---|
| Reliability | Success rate, errors, recovery |
| Efficiency | Time saved, processing time, throughput |
| Quality | AI accuracy, human corrections, missed handoffs |
| Business | Qualified leads, appointments, pipeline, revenue |

A workflow should not be judged on one dimension alone.

---

# 43. Workflow-Level Dashboard

Example:

```text
Workflow:
AI Lead Qualification

This Month:
Eligible Leads: ______
Workflow Success Rate: ______
AI Classification Accuracy: ______
Human Review Rate: ______
Median Time to Qualification: ______
Qualified Leads: ______
Appointments: ______
Opportunities: ______
Estimated Operating Cost: ______
```

---

# 44. Portfolio-Level Dashboard

For multiple automations:

| Workflow | Reliability | Efficiency | Quality | Business Impact | Status |
|---|---:|---:|---:|---:|---|
| Lead Qualification | | | | | |
| Lead Routing | | | | | |
| Appointment Reminders | | | | | |
| No-Show Recovery | | | | | |
| AI Support Triage | | | | | |

This helps identify which workflows should be optimized, expanded or retired.

---

# 45. Status Model

Possible workflow health:

```text
Green
Reliable and meeting intended outcome

Amber
Useful but needs improvement

Red
Unreliable, risky or failing business objective
```

Define actual thresholds internally.

Do not use arbitrary universal thresholds.

---

# 46. Before vs After Analysis

Compare equivalent periods where possible.

Example:

| Metric | Before | After | Change |
|---|---:|---:|---:|
| First Response | | | |
| Qualification Time | | | |
| Follow-Up Completion | | | |
| Human Review | | | |
| Appointment Rate | | | |

Consider:

- Seasonality
- Lead-source changes
- Staffing changes
- Campaign changes
- Product changes

Do not automatically attribute every improvement to automation.

---

# 47. Controlled Testing

Where appropriate, consider:

- Pilot group
- Limited rollout
- A/B workflow variants
- Manual vs automated comparison
- Time-period comparison

Ethical, operational and customer constraints should guide the test design.

---

# 48. Sample Review

Full manual review may be impractical.

Use periodic sampling for:

- AI classifications
- Summaries
- Responses
- Handoffs
- Routing decisions

Document:

```text
Sample Period
Sample Size
Selection Method
Reviewer
Pass Criteria
Findings
```

---

# 49. QA Sampling Frequency

Frequency may depend on:

- Risk
- Workflow volume
- Recent changes
- Model changes
- Error history
- Customer impact

Higher-risk workflows deserve more frequent review.

---

# 50. Drift Monitoring

AI and business conditions can change.

Watch for:

- Accuracy decline
- New customer language
- New products/services
- Changed policies
- Model changes
- New failure patterns
- Increased handoffs

A workflow that performed well three months ago may need revalidation.

---

# 51. Version Tracking

Record major changes:

```text
Workflow Version
Prompt Version
Model
Rules Version
Knowledge Version
Deployment Date
Change Reason
```

Measurement becomes difficult if implementation changes are undocumented.

---

# 52. Measurement After Changes

When changing prompts, models, rules or routing:

```text
Change
↓
Validate
↓
Monitor
↓
Compare to Prior Version
↓
Keep / Roll Back / Improve
```

Do not change multiple major variables at once if you want to understand impact.

---

# 53. Alerting

Define operational alerts for:

- Failure spike
- Authentication failure
- Queue backlog
- Cost spike
- Duplicate-event spike
- AI invalid-output spike
- Missed handoff
- Messaging failure

Alerts should indicate action, not just noise.

---

# 54. Monthly Automation Review

Recommended agenda:

```text
1. Business outcome
2. Reliability
3. AI quality
4. Handoffs
5. Operational efficiency
6. Customer outcomes
7. Pipeline / revenue
8. Costs
9. Incidents
10. Next improvements
```

---

# 55. Executive Summary Template

```text
Automation:
Period:

Primary Objective:

What Improved:

What Declined:

Reliability:

AI Quality:

Human Intervention:

Business Impact:

Cost:

Key Risk:

Next Priority:
```

---

# 56. Automation Incident Review

For significant failures:

```text
Incident:
Date:
Workflow:
Affected Cases:

What happened?

Why?

Customer/business impact?

How was it recovered?

What change prevents recurrence?

Owner:

Validation:
```

Incidents are valuable learning inputs.

---

# 57. Stop or Retire Criteria

Not every automation should remain active forever.

Consider retiring when:

- Business process no longer exists
- Error/risk exceeds value
- Manual process is simpler
- Operating cost exceeds benefit
- Better system replaces it
- Volume is too low to justify maintenance

Automation is not automatically permanent.

---

# 58. Expansion Criteria

Expand when:

- Workflow is reliable
- Quality is acceptable
- Failure recovery works
- Business outcome is positive
- Team understands ownership
- Measurement is available
- Additional volume does not create uncontrolled risk

Do not scale unstable workflows.

---

# 59. AI Automation Measurement Scorecard

| Area | Score |
|---|---:|
| Baseline Quality | /10 |
| Reliability | /10 |
| Error Recovery | /10 |
| Operational Efficiency | /10 |
| AI Quality | /10 |
| Human Handoff Quality | /10 |
| Customer Outcome | /10 |
| Pipeline / Revenue Measurement | /10 |
| Cost Visibility | /10 |
| Continuous Improvement | /10 |
| **Total** | **/100** |

This is an internal management score, not a universal AI automation benchmark.

---

# 60. Measurement Checklist

## Baseline

- [ ] Business objective defined
- [ ] Pre-automation baseline recorded
- [ ] Comparison period defined

## Reliability

- [ ] Eligible executions measured
- [ ] Success rate measured
- [ ] Failures categorized
- [ ] Recovery measured
- [ ] Processing time measured

## AI Quality

- [ ] Task-specific quality metric defined
- [ ] Review sample defined
- [ ] Invalid outputs tracked
- [ ] Human corrections tracked
- [ ] Unsupported outputs tracked

## Human Handoff

- [ ] Handoff reasons tracked
- [ ] False handoffs reviewed
- [ ] Missed handoffs reviewed
- [ ] Response time measured
- [ ] Outcomes tracked

## Operations

- [ ] Manual effort measured
- [ ] Time savings estimated conservatively
- [ ] Throughput measured
- [ ] Data-quality effects monitored

## Business

- [ ] Qualification measured
- [ ] Appointments measured where relevant
- [ ] Opportunities measured where relevant
- [ ] Revenue attribution defined where possible

## Cost

- [ ] Platform cost tracked
- [ ] AI/API cost tracked
- [ ] Messaging cost tracked
- [ ] Human review cost considered
- [ ] Maintenance cost considered

## Governance

- [ ] Workflow versions documented
- [ ] Major changes annotated
- [ ] Review cadence defined
- [ ] Incident process exists
- [ ] Retire/expand criteria defined

---

# 61. Example Measurement Model — AI Lead Qualification

```text
Inbound Leads
      ↓
Eligible for AI Qualification
      ↓
Workflow Success
      ↓
Valid AI Output
      ↓
Qualification Decision
      ↓
Human Review if Needed
      ↓
Qualified Lead
      ↓
Appointment
      ↓
Opportunity
      ↓
Customer
```

Measure:

```text
Technical Success
+
AI Accuracy
+
Human Review
+
Qualification Speed
+
Appointment Conversion
+
Pipeline
```

---

# 62. Example Measurement Model — Appointment Reminders

```text
Appointments Scheduled
      ↓
Eligible Reminders
      ↓
Messages Successfully Sent
      ↓
Customer Response
      ↓
Attended / Cancelled / Rescheduled / No-Show
```

Measure:

- Delivery
- Attendance
- No-show rate
- Rescheduling
- Customer opt-out
- Operating cost

---

# 63. Example Measurement Model — Human Handoff

```text
AI Conversations
      ↓
Handoff Trigger
      ↓
Correctly Routed
      ↓
Human Responds
      ↓
Resolved
      ↓
Business Outcome
```

Measure:

- Handoff rate
- Correct routing
- Human response time
- Missed handoffs
- False handoffs
- Resolution
- Outcome

---

# 64. Common Measurement Mistakes

## Measuring Workflow Runs

Execution count is activity, not impact.

## Claiming Hours Saved Without a Baseline

Measure the old process first.

## Ignoring AI Quality

Fast incorrect automation is not an improvement.

## Ignoring Human Review Cost

Human oversight is part of the operating model.

## Attributing All Revenue to Automation

Separate direct, assisted and operational contribution.

## Optimizing Automation Rate

Some cases should remain human.

## No Failure Classification

A failure total without causes is hard to improve.

## No Version History

You cannot compare results if the workflow changed silently.

## Reporting ROI From Speculative Benefits

Use conservative, supported calculations.

---

# 65. Core Principles

1. **Measure the business process, not automation activity.**
2. **Establish a baseline before claiming improvement.**
3. **Reliability is a prerequisite for scale.**
4. **AI quality must be measured at the task level.**
5. **Human intervention is a metric, not automatically a failure.**
6. **Measure missed handoffs as carefully as excessive handoffs.**
7. **Connect automation to customer and revenue outcomes where possible.**
8. **Include operating and review costs.**
9. **Annotate implementation changes.**
10. **Use measurement to decide whether to improve, expand or retire a workflow.**

---

# 66. The AI Automation Measurement System

```text
Business Objective
       ↓
Baseline
       ↓
Workflow Deployment
       ↓
Reliability
       ↓
AI Quality
       ↓
Human Intervention
       ↓
Operational Efficiency
       ↓
Customer Outcome
       ↓
Pipeline / Revenue
       ↓
Cost
       ↓
Net Value
       ↓
Improve / Expand / Retire
```

The objective is not to prove that automation works.

The objective is to **measure whether a specific automation improves a specific business process enough to justify its complexity, cost and risk**.

---

# Related Resources

- [AI Automation Strategy Framework](ai-automation-strategy-framework.md)
- [AI Workflow Design Framework](ai-workflow-design-framework.md)
- [CRM + AI Automation Framework](crm-ai-automation-framework.md)
- [WhatsApp + AI Automation Framework](whatsapp-ai-automation-framework.md)
- [AI Agent Human Handoff Framework](ai-agent-human-handoff-framework.md)
- [AI Lead Qualification Framework](ai-lead-qualification-framework.md)
- [AI Automation Readiness Checklist](ai-automation-readiness-checklist.md)
- [AI Automation Playbooks](README.md)

---

## About the Repository

This framework is part of **[AI Automation Playbooks](README.md)**, maintained by **[Prashant Rajput](https://github.com/prashant6788)**, Founder of [Touchstone Infotech](https://www.touchstoneinfotech.com/).

The repository focuses on practical systems for:

**AI · Automation · CRM · Lead Management · Workflow Automation · Measurement · System Integration · Revenue Operations**

---

## Important Note

AI models, APIs, automation platforms, CRM systems and operating costs change continuously.

This framework is intended as a practical measurement methodology. Metrics should be adapted to the business process, implementation, risk level, data quality and available attribution.

Correlation should not automatically be treated as causation, and estimated savings or revenue impact should be labeled clearly.

---

## License

This resource is intended to follow the license applicable to the **AI Automation Playbooks** repository.

See [LICENSE](LICENSE) for license details once the repository license is published.
