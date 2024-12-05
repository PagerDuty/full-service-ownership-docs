![Next Steps](/assets/images/headers/FSO-NextSteps.png)

Although the practices we've talked about are effective no matter what platform you’re using, it can help to see how these concepts are applied in practice. This section shows how PagerDuty can be used to practice the steps recommended in this guide.

!!! tip
    If you are currently searching for a solution and are not a PagerDuty customer, you can sign up for a [14-day free trial](https://www.pagerduty.com/sign-up-free/?type=free){:target="_blank" }. This section is here to help PagerDuty customers jumpstart implementation of full-service ownership, with steps on how to define services, as well as understanding dependencies in PagerDuty, and setting up on-call rotations and escalations policies for a service.

Full-service ownership has many benefits, as outlined in this guide. If you are a PagerDuty customer, there are a number of capabilities and features that will make your journey to full-service ownership easier to manage.

### Service Setup in PagerDuty

There are many benefits to configuring your services to be specific and reflective of your infrastructure. With the right setup, teams will experience reduced noise, surface relevant context, see improved MTTA and MTTR, and reduce duplication and manual configuration errors, to name just a few of the benefits. PagerDuty services can be used to reflect different kinds of components, like microservices, vertical applications, or shared infrastructure layers. Additionally, PagerDuty services can be used to act as support queues, represent specific customers, or for other use cases where you need to represent a scope of ownership for a team.

At PagerDuty, we recommend some best practices for naming services, escalation policies, and service dependencies, which are detailed below.

### Naming Services
As previously mentioned in this guide under [Service Documentation](/functions/#service-name), service names should be descriptive and have enough context that anyone interacting with the service understands what it is meant to represent.

- Examples: “Shopping Cart” or “Shopping Cart - App Server”.
- Leave out words like “PagerDuty” or “Alert.” These words are already included when PagerDuty sends notifications.
- Avoid including the name of the monitoring tool in the service name. This information is already included in the incident and does not describe what the incident is affecting.

!!! tip
    Avoid using only acronyms, as they lead to confusion more often than not.

Include helpful information in the service description to help new team members or people outside your team.

- Information can include what the service is, what it is for, and how it affects the business or end users.
- Links can be included in descriptions, so add links to additional documentation, runbooks, or code repositories.
- We also encourage teams to include their service-level SLAs, SLOs, and SLIs, as well as communication channels where other teams can ask questions.

To get started setting up services inside PagerDuty, navigate to the Services tab, then click on New Service.

![service directory image](/assets/images/service-directory.png)

From there, use the above best practices to give the service a name and a description.

![add a service image](/assets/images/add-a-service.png)

Once you have added a name and description, you will have the ability to configure your Integration Settings. After you have configured your Integration Settings, the next step is Incident Settings. Incident Settings is where you will select the Escalation Policy (described in more detail below) and [Response Plays](https://support.pagerduty.com/docs/response-automation){:target="_blank" }.


Response Plays are available on the [Business or Digital Operations plans](https://www.pagerduty.com/pricing/){:target="_blank" }. Response Plays provide a powerful mechanism to drastically reduce the time taken to execute the incident response process by automating actions such as assembling a response team of multiple on-call responders and an [Incident Commander](https://response.pagerduty.com/), and subscribing stakeholders to an incident. To learn more about Response Plays, check out the [Response Plays Knowledge Base article](https://support.pagerduty.com/docs/response-automation){:target="_blank" }.

### Escalation Policies in PagerDuty

Escalation policies allow you to mobilize the right people at the right time by connecting services to on-call schedules. A best practice with any escalation policy is to have a multi-tiered approach; at PagerDuty, we have three tiers of escalation policies for services.

!!! tip
    Individuals should never be assigned to an escalation policy; instead, a schedule should be assigned. For example, if your CEO is the final escalation point, put the CEO on an on-call schedule titled “CEO On-Call” and have that schedule be the final escalation path.


Once the escalation policies are created, services should be attached to those policies. A sample policy is below.

Example escalation policy for an Application Team:

![escalation policy image](/assets/images/application-team-escalation-policy.png)

### Understanding Dependencies in PagerDuty
Service Dependencies can be used to define other technical or business services that your services uses or that consume your services. As [mentioned earlier](functions/#other-components) in this guide, it may be impractical to list all of the dependencies for a service; however, things to consider calling out are single points of failure, possible circular dependencies, and critical path components that are likely to fail.

Within PagerDuty, if an issue arises on your service or on one of the dependencies you have configured, you can use the Impact tab to quickly assess the scope of the impact.

![service dependency image](/assets/images/service-dependencies.png)

You can expand each technical service to see details such as the associated escalation policy and who is currently on-call.

To learn how to add or remove Service Dependencies via the web app, check out this handy [Knowledge Base article](https://support.pagerduty.com/docs/service-profile#service-dependencies){:target="_blank" }. You will also find information on Suggested Service Dependencies. Suggested Service Dependencies use machine learning to suggest other services that may depend on your service or that your service depends on.


If incidents on your service tend to be followed by incidents on another service, or vice versa, Suggested Technical Service Dependencies will be provided. This feature ensures that a service’s dependency topography is continually up-to-date as your technical infrastructure evolves and changes. You may view Suggested Service Dependencies on individual services’ Impact tabs or on an active incident, which will have a blue dot with the number of suggested dependencies, if they are available.

If you are interested in more information about how to effectively set up PagerDuty, please reach out to [sales@pagerduty.com](mailto:sales@pagerduty.com).
