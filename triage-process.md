# Triage
Triage is a part of incident management that quickly assesses and classify issues determining its severity and impact.

## What should I do in managing incident?

1. Identify and raise
2. Assess and classify
3. Respond and mitigate
4. Close and process improvement

### Identify and raise
If we become aware of potential technology incident, for example a customer reported an issue (reactive) or we noticed an alert in our monitoring channel (proactive), then we must raise an incident ticket.

- Is there an existing alert that correlates with what the customer reported?
- How many users reported the issue?
- What's the timeline of the alert vs customer report?

### Assess and classify
At this point, start evaluating the situation, scope, and the business impact (whether operational, financial, etc.).

Start calling out relevant stakeholder and SMEs. This way we can break things up into streams and delegate tasks accordingly.
- Is there any recent deployment for the last 48 hours?
- Upstream dependency issue?
- Infrastructure change?

We start communicating early and often. Must provide the status of what's happening and the next update. If the product has a customer-facing banner or ad, leverage it.

- We are aware of what's happening. We're currently investigating the issue. Next update in 30 minutes.

### Respond and mitigate
Prioritize mitigation as the customer is our priority. If we have identified a potential fix-forward for the issue, we must timebox it. This must also depend on the RTO (Recovery Time Objective). 

Otherwise, rollback to the latest stable version.

### Restore and close
When the issue is resolved, ensure that the following information is recorded:
- What was the issue?
- When was the issue occurred?
- Why it happened?
- Impact
- Fix

At this point, we must also able to provide actionable steps to reduce the probability or prevent the same issue happening again:
- If no alert reported in the channel, then fill that gap. We must always respond first before the customer.
- Action items to prevent the same issue happening again. Put it in the backlog.
- Runbooks to write. If the same alert occurred again, then what should I do? 