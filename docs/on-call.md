---
cover: assets/img/headers/FullService_OnCall.png
description: A step-by-step guide to prepare full-service ownership teams to go on-call for the first time.
---
![Going On-Call](../assets/img/headers/FullService_OnCall.png)

> My greatest fear is getting a high priority page while on-call in a packed Broadway theater, and PagerDuty plays a progressively louder and louder quacking siren, and Alexander Hamilton himself comes up to slap me and my phone out of my hand, and walks me out of the theater” via [Twitter](https://twitter.com/JulianVModesto/status/1222279149819256832)

Going on-call for the first time can seem intimidating. But with proper preparation and practice, incident responders can have a positive experience that provides useful hands-on experience they can use to build more resilient production services. This section details how to prepare for going on-call and what to do during your shift in the on-call rotation.

## Before Going On-call
Relax. Breathe. While you're on-call, for the duration of your shift, it's your responsibility to acknowledge notifications, at any time, whenever they occur. However, it's also essential to remember that life happens. If you know you may be unavailable in advance, work with your teammates to schedule around these events and ensure coverage when you're unavailable. If you're not available when the moment happens, for whatever reason, know that escalation policies exist to ensure that someone will eventually respond if you should be unable.

### Expectations
If you're on-call, you're expected to be available during your shift to the best of your ability. Beyond acknowledging notifications, an on-call responder is expected to have the skills necessary to triage an incident and determine an appropriate course of action. Sometimes, the appropriate course of action is to determine that you're unable to resolve the incident on your own. It is also expected that responders will page additional engineers, as needed, in order to resolve an incident.

### Be Prepared
Proper preparation reduces stress and anxiety when going on-call. It also helps mitigate chaos if and when an incident occurs. The first step to going on-call is to understand exactly what you will need so that you aren't fumbling around at 3 a.m. when a notification comes in. Use this checklist to help you get started:

- **Mobile Phone**. Double check that you won't be going [anywhere that won't have mobile phone service](https://www.opensignal.com/networks). If you're going any place where you're expected to silence your phone (e.g., a movie theater), make sure you have an alternate device that allows you to still receive notifications without disturbing others (e.g., a smartwatch).

- **Laptop**. When you're on-call, you're likely going to need a terminal of some sort. For most of us, that means having a laptop with you at all times. Wherever you go, your laptop should be within a one-minute reach.

- **Chargers**. Always ensure you have a set of chargers necessary for all your devices (phone, headset, laptop, etc.) at all times. Consider investing in a good portable battery for all those times you won't be able to easily find a power outlet. The last thing you want during an incident is to have your phone, computer, or hotspot run out of juice.

- **Internet**. Whether it's WiFi at home, public WiFi, a personal hotspot, or a tethered phone, ensure that you have a reliable plan for Internet connectivity at all times.

- **Logins/VPN/Dashboards**. At least one business day prior to the start of your on-call shift, double check your access to any systems you may need. This includes, but is not limited to, password vaults, VPNs, dashboards, log aggregators, and relevant systems. On the subject of dashboards, be sure you understand what the data on those dashboards means (e.g., what's a nominal state and what's an abnormal state). Also make sure you have access to the relevant documentation and runbooks.

### Notification Preferences
Notification preferences determine how and when you will be notified when an incident occurs. Alert preferences can typically be set to notify you in a variety of ways including via SMS, phone call, email, or app push notifications. Be sure that any method you've chosen is one that will always be available and will get your attention throughout your on-call shift.

### Customized Phone Settings
Incidents don't care about your normal work hours. You should take extra steps to ensure that incident notifications are always surfaced at any time.

- **Add Contact Numbers**. Add the originating contact number for notifications to your phone's list of favorites. Adding these numbers to favorites can help you bypass your Do Not Disturb settings.

- **Bypass Do Not Disturb**. Follow the right procedure to ensure that any numbers in your favorites list will bypass Do Not Disturb for [iOS](https://support.apple.com/en-us/HT204321), [Android](https://support.google.com/android/answer/9069335?hl=en), or for [Android Apps](https://www.techrepublic.com/article/how-to-allow-an-app-notification-to-override-do-not-disturb-in-android-nougat/) (such as allowing Slack and email to bypass).

- **Customize Ringtones**. The setting you both love and hate! Choosing something obvious and different from your normal phone notifications will help surface the notifications you care about. Bonus: you'll never hear that sound the same way after your first few incidents.

### Notification Staggering
If the various notification methods you've chosen are set to all alert you at the same time, you have an increased risk of missing all of them. For example, you might be in bed, sound asleep. Staggering notifications can help get your attention successfully. For example, start with an SMS notification. One minute later, send an app push notification. One minute after that, call your phone. And so on.

## During On-Call
You've started your on-call shift. Now what? You wake up at 2 a.m. to the sound of a foghorn as your phone alerts you to an incident. Your eyes are foggy and your heart is racing. It could be a terrible situation. But it won't be because you used the advice above to prepare ahead of time. You acknowledge the notification. Now we get to work!

### Triage
During the triage process, responders are expected to evaluate the situation at hand. The following non-exhaustive list may be useful to ensure a few basic sanity checks when responding to an incident and beginning your triage.

- Have you verified the source of the notification is correct?
- Have you checked for any current or unusual activity (e.g., checked Slack or email)?
- Is this something that requires immediate action?
- Does your initial investigation indicate a problem/issue with a specific service that your team is responsible for?
- If your team is responsible for this problem, are you able to determine the right course of action to resolve the issue?
- If this problem is beyond your abilities, can you page another member of your team to assist?
- Is the problem beyond the scope of what your team is responsible for or can do to resolve the issue?

### Taking Action
Do what needs to be done to restore the service to full operational status. You have the authority to dive right in to fix what needs to be fixed, involve other teammates as needed, and escalate to an appropriate severity level if necessary. You also have the authority to delay additional work for non-time sensitive and non-impacting issues.

While resolving a minor incident, you should keep basic notes when practical. It is vital to share information with your team, such as the symptoms that initially triggered the incident, investigative steps you took, and the actions taken to successfully resolve the incident. These notes can be immensely helpful in keeping your runbooks up-to-date. You should strive to continuously refactor and improve your team's knowledge base and documentation. Add redundant links and pointers if your mental model of the docs or codebase don't match what you discover during the course of the incident.

If a minor incident is beyond the scope of what your team is responsible for or can do to resolve the issue, you may need to initiate a [major incident](https://response.pagerduty.com).

## After On-Call
At the end of an on-call shift, responders should have an [On-Call Review Meeting](https://reviews.pagerduty.com/reviews/oncall/). Practicing a proper on-call handoff provides the team an opportunity to learn directly from the responder(s) coming off the previous shift. The meeting allows your team to catch problems before they become trends or contribute significant negative impact.

Are there noisy alerts that need to be cut down to reduce alert fatigue? Is this service needlessly sending notifications for non-actionable events? The primary purpose of this review is to understand the on-call load for this shift, identify any sources of pain, transfer knowledge between responders, and plan for improvements of future on-call shifts.

### On-Call Etiquette
A bit of extra consideration can  make the on-call experience better for everyone involved. A few helpful on-call etiquette tips are listed below:

- Be kind to folks currently on-call. If they come into work looking tired at noon, they probably got paged in the middle of the night.

- Be mindful when acknowledging incidents. If you're not on-call and you see an incident, be careful not to acknowledge receipt if you haven't coordinated that response with whoever is on-call. It's a bit counterintuitive because you may just want to help. You can help by jumping onto the incident bridge or proactively reaching out to let whoever is on-call know you're available. But it's their show to run.

- If you're experimenting with production services or performing actions that may likely trigger a notification, you should "take the pager" for the duration of your experiment. Notify the person on-call and schedule an override.

- Never hesitate to escalate when you need additional help. There's no shame in doing whatever is needed to resolve incidents quickly. Likewise, never look down on someone else if they ask you for help. Managers should actively support this policy.

- Always consider covering for someone else on-call if they request it and you're able. We all have messy, unpredictable, human lives. Pay it forward because, sooner or later, it'll be you who needs that favor returned.

- If you're paged to respond to an incident during your shift, you're responsible for riding it out—even if there's only a few minutes left in your shift. You can hand off an incident to the next person on-call if they agree, but you never assume someone else will take over your responsibility.
