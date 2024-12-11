![Service Ownership Functions](/assets/images/headers/FSO-Functions.png)

> "Cease dependence on mass inspection to achieve quality. Improve the process and build quality into the product in the first place." - W. Edwards Deming

Full-service ownership is a shared responsibility across cross-functional parts of your organization. Engineers who wrote code aren't the only people accountable for ownership of a service. This section outlines the different functions necessary to manage ownership of a service.

As opposed to labeling roles, functions are outlined to help organizations better understand all of the considerations that must be managed. Defining availability might be considered the role of "ops" people in some organizations, whereas it might be handled by "devs" in some, or even by managers in others. This guide lays out essential functions and it's up to you to figure out how to build the right cross-functional teams to ensure these considerations are properly managed.

!!! tip
    You may not have everything in place to support cross-functional teams as you're initially developing a model of full-service ownership, but your team should strive to follow a standard process for each service. It's vital that your organization agrees to your version of these considerations, even if they're managed by folks with different titles in various teams. It's more important to agree that these considerations are met in a standard way than it is to agree on who will do them in a standard way.

## Service Documentation
Aside from writing code, there are key functional concerns for owning a service that extend well beyond checking code into a shared repo with a sparse README that maybe explains what the repo contains. Documentation provided should explain what the code does, in addition to a contract that other services can understand if they need to interact with the service.

Remember, you are not the only person who will interact with this service. Make sure your code is reviewed by other members of your team, with whichever code review process they prefer. You won't always be around to answer questions about what your code is intended to do. It's your responsibility to make it understandable so that you aren't a single point of contact (or failure). The documentation for your service should make sense to other people who will interact with it.

!!! tip
    It's important to note that service documentation is a shared responsibility among every engineer contributing to the code base, not a duty to be relegated to someone else. You wrote it, you document it.

Use each section below to document your service so that others may understand it.

### Service Name
They say the two hardest things in computer science are caching strategies and naming — and they're not wrong. It's completely normal to want to use silly names (e.g., Greek mythological figures, pop culture references, space missions, inside jokes, etc.) as fun service names. When you have a small organization, it's natural to think that everyone will remember your clever reference and chuckle when they interact with your service.

But as your organization grows and new teammates join, not everyone will be privy to your sharp wit and clever reference to old inside jokes. Instead, they'll mostly be confused, and your clever wit gets replaced with frustrated repetition as you have to keep explaining what your service is and maybe why you once thought that was funny.

Instead, consider naming your service something descriptive; for example, naming it to explain what it does. If you already have some services with less-than-descriptive names, don't panic. You don't have to change them all at once. Fix forward and start naming new services with clearer and more descriptive names.

We understand that naming is not a trivial task. Ask your colleagues what they would expect this thing you built to be named. Default to long-ish names instead of shorter ones, but not too long. Names that are too long often get shortened into acronyms, and acronyms are just as hard to understand.

Here are some examples of names that are descriptive:

- _"User authenticator"_
- _"Payment processor"_
- _"Shopping cart"_
- _"Login"_
- _"Report generator"_
- _"Email tracking code"_

Here are some examples of names that are not descriptive:

- _PacMan_ (unless you're actually building PacMan)
- _Apollo_
- _BurgunDB_
- _Artemis_ (true story: one of our teammates has worked for four different organizations that have named a service "Artemis")

### Description
Every service should have a description that clearly communicates what it does and why it exists to anyone that interacts with it. At a minimum, you should answer the following questions when creating a description for your service.

- What is the intent of this service, component, this slice of functionality?
- How does this thing deliver value?
- What does it contribute to?
- If this is part of a customer-facing feature, explain how this will impact customers and how it rolls up to the larger business component.

It's tempting to also want to mention the other components that this service may interact with in your description. But remember that external components beyond your control may change as other service owners make changes without necessarily notifying you. We recommend defaulting to not listing external components. If you absolutely must mention these, ensure you have a process in place to account for tracking external changes when they occur.

### Other Components
Every service will not need to have all of these components documented. However, some other common considerations for what should end up in your documentation include the following:

- **Dependencies**. It may be impractical to list all of your dependencies, but important things to call are things like single points of failure, possibly circular dependencies, and critical path components likely to fail.
- **APIs**. List the functionality that you guarantee for consumers of this service. In this section it's important to set expectations around public APIs that should rarely change vs. private APIs that may change frequently. This section isn't meant to establish API best practices; it's just meant to set consumer expectations and/or point to more robust in-depth docs.
- **Deployment Mechanisms**. Some teams may have their own (non-standard) deployment mechanisms in place. Let others in your organization know how to see the status of your latest deployment (or rollback … or better yet, roll forward!) so that it can assist them with troubleshooting their own services if they notice unexpected behavior from yours.

## Service Availability
Every service should set realistic expectations for its availability with a set of clearly defined metrics. The most common method for defining availability is to set service level indicators (SLI), objectives (SLO), and agreements (SLA). No service can, or will be, available 100% of the time.

The goal with SLI/SLO/SLAs is to set both internal and external expectations for the behavior of your service. Internally, service owners must have a measure for gauging whether or not their service is behaving as expected so that they can make decisions around investing time and effort toward improving availability if expectations are unmet. Externally, service consumers must also understand your expected availability so that they can make decisions around investing time and effort in managing failures that may occur as a result of consuming your service.

SLAs should be consistent for each service. If you have more than one SLA for a service, consider splitting up the service. Each service should only be accountable to one SLA, though it may have multiple SLOs. For more about how to define service availability, we recommend reading [Chapter 4 of the Google SRE book](https://landing.google.com/sre/sre-book/chapters/service-level-objectives/){:target="_blank" }.

### Service Tiers
Defining service tiers may be an alternate way to set organization-wide expectations to reduce the overhead of individual service teams. By agreeing on the definition of what services in a particular tier will provide, it can more quickly and effectively accomplish the task of setting expectations in a standardized way.

Defining service tiers typically involves working with product owners and engineering leadership to set expectations.

At PagerDuty, a Tier 1 service has the strictest expectation of latency, uptime, and availability. Tier 1 services should perform at the highest level of delivery that customers require. Our Tier 1 services typically require 24/7 on-call schedules, multiple levels of robustness, a disaster recovery plan, and always-current runbook documentation.

We also have Tier 2 and Tier 3 services. Tier 2 services, for example, have support hours that only span across weekdays. These types of services may provide additional functionality that is not critical or may be new services that have not yet been rolled out to general availability in production.

Your tier definitions may be different (or sometimes, [even our own!](https://www.pagerduty.com/blog/how-to-manage-a-tier-zero-service/){:target="_blank" }). For example, some organizations have a strictly binary sense of tier levels: critical path or not critical path. Your organizational definitions may vary, but establishing them can quickly help set expectations across teams.

## Runbooks
Things will go wrong. Services will fail for any variety of reasons. As you learn about the different nuances of your service, you should keep a record of what you've successfully done in the past that might resolve common issues in the future. In an ideal world, you have the ability to resolve these common issues at the source of the problem within your code. But sometimes, a procedural fix may be necessary until you reach that ideal state. [Runbooks](https://www.pagerduty.com/resources/learn/what-is-a-runbook/){:target="_blank" } are a great place to store these types of procedural fixes.

Always remember that a runbook is not comprehensive — it's not possible to consider every type of incident or issue that a service may encounter, and due to the nature of complex systems, there isn't always a common procedure for every incident that occurs. However, it can be helpful to capture repeated processes or initial approaches to troubleshooting.

When changes are made to how the service functions or is implemented, or when previous recurring issues are fixed, the runbook may become out of date and the procedures within them suddenly become invalidated. A stale procedure in a runbook can sometimes be more dangerous than no procedure at all because incident responders trust your previous experience and may try these invalidated procedures without the typical scrutiny during a moment of crisis. The previous "fix" might now instead inflict additional damage. To avoid this, be sure to include a step or stage for updating runbooks into your release process.

## Production Operations
Owning a service also means operating it in production. The service team is responsible for setting up monitoring and alerts (focus on ensuring your SLOs are met), setting up and maintaining supporting tools, and ensuring an appropriate level of robustness and reliability.

Some organizations use a combination of a centralized infrastructure support team (e.g., SRE) in tandem with support that comes from within the service ownership team. Some organizations have service ownership teams that own the entire stack soup to nuts. The level of responsibility here will vary. However, a number of effective guides to running software in production are available, and we recommend turning to the [Google SRE book](https://landing.google.com/sre/sre-book/toc/){:target="_blank" } for in-depth guidance when operating in production.

## Project Management
Full-service ownership extends well beyond the practices of software development and operating software in production. Software is neither written nor run in a vacuum. How the business supports ongoing development is a critical function of enabling full-service ownership.

How does your service handle unforeseen circumstances? There's an element of unpredictability in full-service ownership. When things go wrong and an incident occurs, you will discover new things via outcomes and action items from your [postmortems](https://postmortems.pagerduty.com){:target="_blank" }. Hopefully, your team might discover necessary changes before an incident occurs. But how and when does your development team perform proactive maintenance? Project managers are an integral part of full-service ownership because they have to be mindful about building in necessary buffers for unplanned work.

Project managers can help make full-service ownership manageable for their development teams in several ways:

- Defining what "done" is
- Being aware how much stress the team is under and shielding them from [executive swoop-and-poop](https://response.pagerduty.com/training/courses/incident_response/#executive-swoop){:target="_blank" }
- Understanding and mitigating dependencies by doing connective tissue work between different teams and features
- Bringing awareness of what it means to pull people away from other projects to solve a problem

Project management is an essential function of a full-service ownership team. Depending on the needs of the team, this may be a full-time role embedded within the team or a role filled by a person whose time is shared between different service ownership teams.

## Product Ownership
Product owners are responsible for translating the requirements of the customers—such as uptime, performance, and security—beyond what something looks like or what it is capable of. Customers will tell product owners what they want a product to do, but they'll rarely specifically ask for uptime, performance, or security in an interview or user forum.

Without uptime, a customer can't get to the new wonderful feature you've delivered. Without performance, they'll leave your site or app in frustration, tired of waiting for the feature to load. Without security, they won't trust that new feature. So in reality, customers are always asking for uptime, performance, and security—they just don't usually use those words.

Product owners must work with developers to ensure that uptime, performance, and security requirements for services meet the needs of customers. Like project managers, this may be a full-time role embedded within the team or a role filled by a person whose time is shared between different service ownership teams.

## Senior Leadership
Full-service ownership works best when it's championed by senior leadership and when it's consistent across the entire product and engineering organization. Senior leadership plays a role in the needs of every service ownership team by doing things like making room in the roadmap for investing in technical debt, encouraging a culture of cooperation and sharing, and enabling everyone to do their jobs well by providing the tools they need.

Leaders also help set objectives that balance business priorities against achievable engineering goals. For example, if senior leadership expects 100% uptime for your main product, it will be incredibly challenging to create a reasonable plan for how the various underlying services can possibly support that. A plan with zero room for failure is a plan that is destined to fail. Senior leadership must help strike the right balance between zero downtime business goals and no SLA or a "do your best" policies that set the business on a path toward failure.
