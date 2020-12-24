---
cover:
description: The basics of Full-Service Ownership. Why this level of ownership matters in today's world and why teams struggle to make the shift.
---
![Defining a Service](../assets/img/headers/FSO-Defining.png)

> A service is a discrete piece of functionality that provides value and is wholly owned by one team.

## Shared Understanding
At PagerDuty, we think about a service as **a discrete piece of functionality that provides value and that is wholly owned by a team**. Our definition is this specific because it refers to an infrastructure composed of distinct services that are written as separate pieces of code, but it also applies to parts of our monolithic codebase, and even to external tools. With that universality in mind, we find this definition to be particularly helpful regardless of your current architectural model, and we encourage its use.

For your organization, a key first step is to come to a shared understanding of the boundaries of a given service and to figure out who its key stakeholders are. If there are multiple teams contributing, maintaining, and supporting the given service, understanding the boundaries and stakeholders becomes even more important.

Take the following steps to help create that shared understanding:

1. **Define the team that will own the service.** Start by considering who is responsible for the service you are defining. A service should be wholly owned by the team that will be supporting it via an on-call rotation. If multiple teams share responsibility for a service, it's better to split that service up into separate services (if possible). Some organizations call this "service mitosis"—splitting one cell into two separate cells, each looking very similar to the former whole. There are several methods for deciding how to separate services like, for example, splitting them up based on team size or volume of code they manage. You can read more about [how we did that at PagerDuty](https://www.pagerduty.com/blog/well-formed-delivery-teams/).

1. **Set up the on-call rotation for this service.** Ensure that the people on the team share responsibility for ensuring availability of the service in production. Create on-call schedules that rotate individuals and back-up responders on a regular cadence, as well as policies that include escalation contacts.

1. **Ensure the team is sized correctly.** Services should be set up granularly enough so that the members of that team are able to quickly help identify the source of problems. This can apply to creating a service with a scope so large that the knowledge necessary to support it is beyond what's contained within the team. But it also applies to scoping a team in a way that is too small. For example, if two microservices effectively behave as one, and fixing a problem on one means also fixing it on another, then it might make sense to combine them.

!!! tip
    If you have a monolith, consider how you will address on-call responsibilities for it. Monoliths tend to be the cause of a lot of incidents, both actionable and non-actionable. If one team owns the monolith, they usually don't own any other services unless the on-call load for the monolith is low.

    If multiple teams share responsibility for the monolith, consider gradually identifying different sources of functionality and routing those alerts to teams that have the right context. Although the monolith shares the same code base, each logical source of functionality you identify can be considered its own service. That logical service can be represented as a different service for your documentation, runbooks, and wikis, along with your on-call ownership in PagerDuty.

## What About Dependencies?
Don't worry about dependencies between services at the beginning—focus instead on whether something represents something you and your team are responsible for. You can add dependencies, relationships, and more after you sort out what a service means for your organization.
