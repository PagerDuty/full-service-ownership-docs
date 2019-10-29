![Getting Tactical](../assets/img/FullService_GettingTactical.png)

While going on-call for the first time can be intimidating, proper preparation will allow for a much more positive experience. This section will detail the required items to have when you are on call, setting notification preferences and alerting rules, communication channels, and what to do when you get paged.

## Responsibilites and Planning
While it is the engineers responsibility to answer notifications while on-call or work with teammates to schedule around events, it is essential to remember that life happens. Notifications may get missed before the escalation process kicks in. The engineer's responsibility is to be available during their shift to the best of their ability. Beyond acknowledging the notification, an on-call engineers' responsibility is to triage the situation but does not always mean they can fix the problem. Depending on the severity level of the incident, engineers may need to get others involved.

## Pre On-Call Planning
Proper preparation reduces stress and chaos when going on-call. The first step to going on-call is to understand exactly what you will need, so you aren't fumbling around at 3 am when a call comes in. Below is a checklist to help you get started:

* Cell Phone: Double check you aren't going anywhere where there won't be cell phone service. Depending on how you have your notifications set up, your cell phone may be the first message you receive.
* Laptop: When you are on-call, you must have your laptop with you at all times. Even if you are at a restaurant or a movie, your laptop should be within a short reach.
* Chargers: Have an extra set of chargers with you for all devices, and consider investing in a USB charger. The last thing you want during an incident is to have your phone, computer or Mifi die on you.
* Internet: Whether it is Wifi, Mifi, a personal hotspot, confirming you will have connectivity before your shift saves you time and stress during an incident.
* Logins/VPN: Double check your access to any systems you may need at least 24 hours before your shift, a midnight run to the office or a call to your service desk is easily avoidable. This includes but is not limited to passwords, VPN's, and systems. Also make sure you have access to the relevant documentation, runbooks, and playbooks.

### Notification Preferences
Notification preferences determine how and when you are notified and is a fundamental piece to going on-call. Most alert preferences can be set to notify users via SMS, Call, Email, and Push with the ability to stagger times in between notifications. Provided you have already set your alert and escalation policies as detailed above, follow these steps to ensure you aren't missing notifications.

### Do not disturb settings, Adding Numbers, and Ringtones
As incidents do not abide by the normal work hours common step missed when setting notification preferences is ensuring calls, SMS, and Push notifications bypass do not disturb settings on mobile phones and have their own unique ringtone to avoid confusion with day-to-day calls and activity.

*   Add contact numbers into the phone: It is important to add the contact number for notifications into the contacts and mark them as favorites on mobile devices being used which will allow for the second step of bypassing Do Not Disturb settings.
*   Bypass Do Not Disturb:
    *   For iPhone users, follow [these](https://support.apple.com/en-us/HT204321) steps to customize your settings.
    *   Android phone users, follow [these](https://support.google.com/android/answer/9069335?hl=en) steps to customize your settings.
    *   For Android apps, follow [these](https://www.techrepublic.com/article/how-to-allow-an-app-notification-to-override-do-not-disturb-in-android-nougat/) steps to allow apps such as slack and email bypass your DND settings.
*   Customize your ringtone: Chose something obvious and different from normal phone notifications, this will minimize confusion.

### Notification Staggering
A commonly overlooked element is notification staggering. If all your notifications come in at the same time, you have an increased risk of missing them, especially if you are in bed, sound asleep. Your notification preferences must be less than your escalation policy. It is recommended that you use incident severity or priority levels to determine your notification preferences.

*   Going on and off call: Set notifications 24-48 hours in advance of going on/off-call.
*   Notification Staggering: Set a minimum of two notification rules for high level incidents

## During On-Call
You are about to go on-call; now what? You wake up at 2 am to the sound of a foghorn as your phone alerts you to a potential incident; your eyes are foggy, and your heart is racing. It sounds like a terrible situation, but it won't be if you and the team have followed the outlined steps above. During an on-call shift, you are responsible for acknowledging alerts, triaging the situation, fixing the problem (if you have the ability to), improving the process, and supporting the team through handoffs.

### Triaging
During the triage process, on-call individuals will evaluate situations should they arise.  It is important to think broadly during the triage phase by asking yourself a few key questions:
* Have you checked your chat platforms (Slack etc..) for current activity?
* Does the alert and your initial investigation indicate a general problem or an issue with a specific service that your team is responsible for?
    *   If it does not look like a problem your team is responsible for escalate to the appropriate team.
* Are customers affected by the issue?
* Is this something that requires immediate action? If yes, have you escalated into a major incident?
* Is this tactical work that can wait until normal work hours?

If the issue is not a major incident but does require you to fix it, complete the necessary work, and document the steps you took. In the case of an actionable alert, or one that does not require immediate attention, silence the notification and work on it during appropriate hours.

### Fixing
The key component of full-service ownership is the empowerment of individuals to act and make decisions. Individuals on the on-call team need to be aware they have the authority to dive right in to fix what needs to be fixed and involve other teammates as necessary and escalate to an appropriate severity level if needed. This means For non-time sensitive and non-impacting issues, team members can prioritize remediation based on other priority work.

Keeping clear documentation during all stages will assist in the postmortem process for high severity incidents. However, documentation should not be left to only those incidents. As part of the full-service ownership team; on-call individuals should constantly be looking for ways to improve both the system and the alerting principles. If a particular issue keeps happening; if an issue alerts often but turns out to be a preventable non-issue – perhaps improving this should be a longer-term task. If information is difficult/impossible to find, write it down. Continuously refactor and improve the knowledge base and documentation. Add redundant links and pointers if your mental model of the wiki/codebase does not match the way it is currently organized.
