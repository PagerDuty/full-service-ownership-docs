![Escalation Policies](/assets/images/headers/FSO-Escalation.png)

> "Organizations which design systems will produce designs which are copies of the communication structures of these organizations." - Conway's Law

When incidents occur and an immediate response is necessary, the escalation policy represents the order of responsibility for reacting to issues detected on a service. How these escalations are set up effectively dictates your incident response patterns. The system you choose to build should mirror the needs of your specific organization.

There are several different approaches to how you can coordinate the triage, acknowledgement, and ownership of the response. Your organization's escalation policy may differ based upon your own unique business constraints.

At PagerDuty, we find that a three-tiered approach is common amongst our customers. Your mileage may vary.

## Three-Tiered Escalation
This escalation policy has at least 3 levels of escalation for critical path services, starting with the team who is currently maintaining that service.

### First Level
The first level of an escalation policy in an organization that has adopted full-service ownership is someone on the team that currently maintains the service (remember: you may be on-call for a service you didn't originally build—and that's normal). This person should come from a rotation of folks on the team who are ready to respond to issues for that specific service.

Some teams treat the first level of the escalation policy as the primary point of contact for questions about the service. When paged, that person has become the "interrupt handler" and the role of "standby interrupt handler" shifts to another person within the on-call rotation. Additionally, whenever the service they own is impacted, the service they own is affected by an incident within another service, or if they're considered a stakeholder, the first-level responder will also be brought in as the subject matter expert (SME).

Often, there are multiple people on the first level—the primary responder and a shadow, who should be observing and learning from the primary responder. As new people join the team, they should have the opportunity to shadow so they can ramp up and be prepared to deal with incidents on their own. At PagerDuty, we practice shadowing and reverse shadowing](https://www.pagerduty.com/blog/on-call-shadow-practice/).

### Second Level
The second level of escalation is meant to catch notifications that weren't acknowledged. Most organizations understand that everyone is human. Sometimes the person on call can't work on the current problem. If the first-level responder is unavailable, escalation to the second level typically activates within a time period determined by the service's tier level and the SLOs.

At PagerDuty, the second level of the escalation policy is comprised from the same pool of people that are in the first level. It's not uncommon to set up the second level as another rotation of folks on the same team. For example, at PagerDuty the second level escalation is the same set of people as the primary level, but the schedules are offset by a week. The secondary on-call person for a given week was the primary on-call person from the week before. Our logic is that the second-level escalation still has context from being primary the week before.

Responding to an incident is a team's responsibility, not just that of a single person who is on call. The first-level responder may be the first person to start working on the problem, but no requirement says that person must be the only incident resolver. If the first-level responder is unable to resolve, or is even just uncomfortable with, the current issue, it is reasonable and encouraged that they manually escalate to the second-level. At PagerDuty, we want first-level responders to feel comfortable asking for help as soon as possible, so we maintain that the second-level responder should be someone that the first-level responder feels safe with.

!!! tip
    Think very carefully about the timeframe between when an incident gets escalated from the first to second level. A very short timeframe for activating a second-level escalation doesn't make your service any more reliable. In fact, decreasing time to escalate is a bit of a trade-off. The faster you escalate to the next level, the more trauma it can cause that team. No one likes feeling like they missed an important call. The second-level responder may get irked that they're picking up the slack, and the first-level responder has an added layer of anxiety on top of the stress they experience when responding to an incident.

### Third Level
The third level of the escalation typically includes technical team leaders, as defined for the service. For some teams, this may include their engineering manager, the tech lead, and the (technical) product owner.

!!! tip
    At PagerDuty, for Tier 2 and Tier 3 services, most escalation policies use a three-tiered system. Tier 1 services have an escalation policy that may include a fourth-level escalation comprised of people from the engineering senior leadership team.
