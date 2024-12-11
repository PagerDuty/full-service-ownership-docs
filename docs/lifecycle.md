![Service Lifecycle](/assets/images/headers/FSO-Lifecycle.png)

> "The various segments of the system of profound knowledge cannot be separated. They interact with each other. For example, knowledge about psychology is incomplete without knowledge of variation." - W. Edwards Deming

The various roles necessary for successful ownership of a service each contribute differently throughout the various points of the lifecycle of a service. Three major phases of the lifecycle of a service include design, runtime, and sunsetting.

## Design Phase
While existing (or brownfield) projects may be a [worthwhile place to get started](/getting_started#greenfield-vs-brownfield), greenfield projects provide full-service ownership teams a good opportunity to design a new world as they see fit. Teams working on greenfield projects should ensure these considerations are met during the design phase.

### Customer needs
Even if this service is an internally facing subcomponent of functionality deep in a stack that is never seen by paying customers, it bears a reminder that everything should be treated as a "product."

Full-service ownership teams must work toward an understanding of their customers. Remember that customers aren't only external people that pay your company money. Customers are anyone that consumes the service and expects a given output. Internal employees are just as important as external paying (or non-paying, if your service is free to use) customers.

The service ownership team must be [innately tuned to the needs of its customers](https://www.pagerduty.com/blog/employee-spotlight-sre-product-owner/){:target="_blank" } throughout the entire service lifecycle. But it all starts in the design phase. [Product management principles](https://medium.com/pminsider/product-vs-project-managers-marty-cagans-twelve-best-lessons-for-product-team-work-548d706b3f74){:target="_blank" } should be applied to the ongoing design of every service.

### Pre-production
Service teams must have pre-production environments available on which to test new changes destined to run in production. As practically as possible, any pre-production environments should closely resemble their production counterparts (e.g., resembling the same scale may not be practical). For example, if this service is not deployed using a container-based solution in production, development teams should not be running testing environments in containers in pre-production.

These pre-production environments are where teams will test proposed changes and service functionality. Reducing the number of variables between these environments and production is critical. Additionally, following the principles of [Continuous Delivery](https://continuousdelivery.com/){:target="_blank" } can help ensure a more effective, safe, and reliable pre-production development experience when introducing changes to your codebase.

### Production readiness
When preparing to initially release your service to production (i.e., to be consumed by others), exact procedures for these key areas should be addressed in advance.

* **Engage with necessary production teams.** Having defined and understood the bounds of [production responsibility](/functions#production-operations) for managing this service, if other teams will be involved (e.g., SRE, Operations, Sustainability Teams), now is the time to ensure that inter-team communication processes are also defined. Ensure a clear process exists for pertinent information sharing, escalation paths, and periodic opportunities to review and improve the established communication mechanisms.

* **Define (and test) alert notifications.** While it's impossible to predict every possible failure/degradation condition, it's helpful to go through an exercise to list and identify areas of concern. Define these alerts in your monitoring and alerting tools (and test them!). At a minimum, draft a matrix that considers the following for each area of concern:

| Area of concern            | What to determine                                                                       |
|----------------------------|-----------------------------------------------------------------------------------------|
| **Triggers**               | Conditions that should trigger a notification of this failure/degraded state.           |
| **Information to include** | Information that is helpful to anyone investigating this failure/degraded state.        |
| **Recipients**             | The team(s) responsible for responding to the likely contributing factors for this failure/degraded state. Limit notifications only to team(s) empowered to take investigative action during this failure/degraded state. |
| **Tips for responders**    | When a notification for this failure/degraded state is triggered, are there any suggested (if applicable) troubleshooting or resolution steps that responders would find useful? |

* **Drafting an initial runbook.** The [runbook for a service](/functions#runbooks) will adapt and change over time as you learn more about how your service behaves. However, even at the time of initial release for your service, there are likely already ideas on suggested troubleshooting/resolution steps that will be helpful when responding to incidents. Even if you cannot fathom such steps in the beginning, **a minimal runbook is better than no runbook**. Starting with something, even if minimal, will make it a known reference point that can more easily receive contributions or be maintained as the service evolves.

* **Internal reviews.** Readiness checks of your service by other design phase stakeholders should occur prior to promotion into production. This can include things like information security audits, approval from the sustainability team(s), or any other reviews required by your organization. However, it's worth noting that these aren't necessarily "later-stage" or even "final-stage" reviews. These reviews can benefit greatly from being incorporated into your ongoing work.

!!! tip
    An example anti-pattern of collaboration would be to have a "hardening sprint" be the last last sprint of a project, when all security tests are performed and identified issues may or may not be fully remediated. In contrast, performing these reviews continuously throughout the entire development phase would surface information security concerns at a time when they're likely much less integrated in the service and, therefore, more difficult to remediate.

## Runtime
Launching a service into production requires far more than just ensuring availability. Day-to-day operation of your service requires maintenance, iteration, and deploying updates. Services are never "done." Any service that is actively consumed to a reasonable degree—especially those newly launched—requires ongoing improvements, either to address new features requested by customers, resolve newly discovered software bugs, or improve issues such as security or reliability. The following areas of concern should be addressed throughout the runtime phase of a service.

### Versioning
If your service presents an API, it's incredibly useful to expose it in a versioned manner. Versioning your API allows you to release new versions of the service without impacting its availability for API consumers that have yet to test/validate the new changes.

A common example would be a RESTful API endpoint with major versions exposed. For instance, a service might present major versions with a path like `https://yourcompany.com/mycoolservice/v2`. When a new version of API functionality is released, it can be accessed at `https://yourcompany.com/mycoolservice/v3`. Consumers of the service can test the new v3 functionality without impacting any integrations currently relying on v2. Once those changes are validated, any integrations can be readied to consume the new functionality at their leisure.

Software that is not published as an API endpoint or service (such as those made available as libraries or packages), often follow practices like [Semantic Versioning](https://semver.org/){:target="_blank" } to help customers understand which updates they should consume (e.g., when a change is considered "breaking"). Similarly, [Semantic API Versioning](https://www.fourkitchens.com/blog/development/semantic-api-manifesto-versioning-apis/){:target="_blank" } can help service consumers more granularly understand how they are impacted by released changes.

### Customer Communication
The specific requirements for customer communication will vary according to many factors (e.g., service tier, customer type, organizational requirements, community expectations, etc.). But typically, it's prudent to have a method (or several methods) of informing customers when changes to a service are deployed, especially when those changes are considered "breaking changes."

Two low-effort and high-touch methods for establishing that type of communication are providing both mailing lists and changelogs. An opt-in mailing list for customers provides a mechanism to receive change notifications, but also provides a useful mechanism for relaying any relevant announcements about a service that aren't directly related to a released change.

Actively maintaining a detailed [changelog](https://keepachangelog.com/en/1.0.0/){:target="_blank" } in a predictable and accessible location also provides an ad-hoc/opt-in mechanism where interested consumers can reference released changes. A changelog should be a part of the release notes that accompany your service (e.g., in an app store, if applicable, or linked to via the README in the service's code repository).

### Reliability Maintenance
In addition to the maintenance required as part of introducing new features/changes to a service running in production, an additional class of maintenance comes in the form of service reliability.

When service incidents occur, an essential practice is [regularly performing postmortems](https://postmortems.pagerduty.com){:target="_blank" } to understand what happened. When action items are discovered as part of a postmortem, they need to be prioritized into the [service team's workstream](/functions#project-management). Service team [Product Owners](/functions#product-ownership) should participate in postmortem meetings in order to fully contextualize and help prioritize these action items.

Not every action item identified in a postmortem may end up in a service team's workstream. However, these action items should be acknowledged and evaluated in a timely manner. It may be tempting to create a policy that all postmortem action items must be completed within a certain amount of time. However, that anti-pattern can inadvertently incentivize practitioners to only identify action items that they believe can be completed within a limited scope of time. Conversely, encouraging the creation of any and all action items, some of which may later be closed without a decision to act on them, allows teams to identify temporary fixes/workarounds that can be documented in runbooks, or allows them to scope more achievable action items that may be eventually incorporated into a longer-term solution.

## Sunsetting
All good things must come to an end. For a multitude of reasons, your team or organization may decide to deprecate or retire a service. The act of sunsetting a service should have a fully defined process that extends beyond the semi-popular approach of just "turning it off."

### Deprecation vs. Retirement
If it's decided to no longer make investments that improve a service, that may not necessarily mean it gets completely shut down. Deprecating a service is a way of defining a new set of expectations with consumers. In a deprecated state, no new functionality is added to a service. However, an expectation may be set with consumers that the service may continue to provide bug fixes or security remediations for some amount of time to come.

Retiring a service implies that it will be shut down completely and it will cease to be available after a defined date. It's common to first deprecate a service for a specified period of time prior to its complete retirement.

### Identifying Customers
Prior to retiring a service, service owners should work to identify their current/active customers. Activity logs are a good place to start the identification process. Component services (e.g., add-on portions of a parent product) may be able to work with external customer-facing teams to determine contractual obligations and current users. Service owners should take all pragmatic measures to create a customer list to understand the impact of retiring their service.

For a variety of reasons, it's not always possible for service owners to uniquely identify and reach out to all of their current/active customers. Even if those customers can't be identified by name, understanding metrics like monthly active users, volume of requests, and unique sources of connections can help service owners make informed decisions about the impact of retiring a service.

### Business Impact
Once any active customers of a service have been identified, decisions about the business impact of its deprecation or retirement can be made. Service owners should utilize their connection with [senior leadership](/functions#senior-leadership) to help communicate and quantify business impact. Service owners may not have all the direct information necessary to understand the impact of sunsetting their service. Senior leadership should help facilitate discussions with other parts of the organization (e.g., Sales, Support, Customer Success, etc.) to create a more complete understanding of the business impact for sunsetting a service.

### Offboarding customers
Once business impact is understood and the decision to sunset a service has been made, how that decision is communicated to customers has a vital impact on customer satisfaction and the overall customer perception of your organization. Customers typically need more than ample time to react to and adapt in preparation for the retirement of a service.

Consider the cycle time necessary for your organization to identify and reach the necessary customers, for those customers to figure out a response plan, get that plan into their workstreams (your service is likely not the only one they have to manage), validate that change with their own internal teams/stakeholders, release that change into production, and transition their own customer traffic to consume this new change with ample time to validate they are not creating any inadvertent downstream impacts to their customers. Consider what that cycle time is like for your customers, then double it or triple it. That's probably just under the least amount of notice your customers expect to prepare them for the retirement of a production service they rely on.

In addition to providing sufficiently advanced notice, customers would benefit from service owners or the business providing alternative options including, but not limited to, migration plans to help ensure continuous availability for their needs. For example, if another service (or API) your company/organization offers can fulfill the needs of the service being retired, ensure that a fully validated migration plan is communicated as part of the retirement date announcement. Clearly communicating customer offboarding procedures will make or break customer satisfaction during these precarious operations.
