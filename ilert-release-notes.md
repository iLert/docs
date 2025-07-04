---
description: >-
  This page contains release notes for new features and improvements released
  after April, 2020.
---

# ilert Release Notes

{% hint style="success" %}
These notes get usually updated retrospectively within the first week of the following month _e.g. all November releases are added by 5th December_.
{% endhint %}

## May 2025

### New features and improvements

* We have launched our new feature **Event Flows** in closed **BETA** :tada:, [reach out to us](contact.md) if you like to try it out; its like call flows, but for your events
* We have launched a new **AI agent** "Alert Investigator" in closed **BETA** :tada:, which uses MCP servers to gather information e.g. ELK Logs or Github Deployment related source code to provide responders with a root-cause analysis right in their ilert alert detail view, reach out to us if you like to try it out.

### Integration updates

* **Autotask** outbound has been revamped
* **ServiceNow** outbound has been revamped
* bidirectional alert source creation no longer relies on redirects (multi forms) the whole creation now happens within the alert source wizard
* New inbound integration [LibreNMS](integrations/inbound-integrations/librenms.md)
* New inbound integration [Panther](integrations/inbound-integrations/panther.md)
* New inbound integration [TeamCity](integrations/inbound-integrations/teamcity.md)

## April 2025

### New features and improvements

* **AI postmortem generation** now supports **deployments** as well
* Coverage requests now send an email to receivers that do not have the mobile app installed
* The email alert action will now immediately stop sending emails if we detect bounces
* Alert and incident list views now provide you with a little search shortcut which open the AI global search in category mode

### Mobile app

* Coverage request push notifications now support user avatars on iOS as well
* Navigation for push notification reactions has been improved
* All push notification sounds are now available in a short and long variant
* Push notification settings UI has been reworked
* Coverage requests now stay visible for the last 24 hours after taken any action on them
* Account page design has been reworked
* Call flow calls and call log insights are now available

### Integration updates

* New inbound integration [Gatus](integrations/inbound-integrations/gatus.md)
* New inbound integration [Rollbar](integrations/inbound-integrations/rollbar.md)

## March 2025

### New features and improvements

* **Support hours** now support exceptions (absolute date-time ranges) and **holiday** calendar imports
* The ROUTE\_CALL call flow node, now skips agent confirmation if the target is no responder but an external phone number; this helps with connecting your call flows to third-party call hotlines. Note: number targets are an enterprise plan feature
* Alert report fetch times have been improved using a new approach to validating access permissions on large amount of entities
* We have introduced 4 new templates for alert source customization: **alert key extraction** and **event type (3) condition matching** (for now these are only active on types: API and EMAIL2)
* **ITL** now supports 2 **new regex functions** (this is helpful for less complex event payloads e.g. emails with subject and body text fields, to help extract specific information)
* We continue to improve default templates for alert source content customization
* We have introduced a new call option for the ROUTE\_CALL call flow node: "simultaneous calling", you may use this to call all targets at once, instead of escalating through them
* Whatsapp notifications have been moved to a new infrastructure, making their delivery more stable (while still lying under the good will of Meta though ;) )

### Integration updates

* We have **reworked our email alert source** (EMAIL2) to enable the same features that our API based event integrations provide, you may now use AI similarity grouping, content templating and other features like the event explorer. Old (EMAIL) alert sources will keep working as usual and may be updated through the old UI, new email alert sources will no longer show the "Advanced settings" menu tab, instead you can use the general templating mechanism to customize behaviour.
* New inbound integration [Dash0](integrations/inbound-integrations/dash0.md)
* New inbound integration [Apica](integrations/inbound-integrations/apica.md)

## February 2025

### New features and improvements

* We have launched a **new signup and onboarding experience**
* The **user edit view** and **profile edit view** have been **overhauled** and use the new UI stack
* We now show **user profile cards** on hover in alert and incident views
* The **alert source create wizard** has new category options and **improved** search and setup features
* **Status pages** support **Posthog** and **Google Analytics** tags
* Static schedule edit view is now on the new UI stack

### Mobile app

* Completely **new alert list and alert detail experience** with tab separation and floating action toolbar
* **Coverage request** now support **avatars** on iOS push notifications
* Contact sync now respects and supports limited access to contacts

### Integration updates

* **ArgoCD** deployment pipeline integration
* **checkmk** now supports **bidirectional** integrations
* **SAP** Focused Run inbound integration
* **IT-Conductor** inbound integration

## January 2025

### New features and improvements

* New **heartbeat** experience is in closed **BETA**, supporting millions of heartbeats with sub minute ping intervals and additional features like assigning multiple heartbeats to the same alert source for individual grouping mechanics
* We have launched our **new alert reports in GA**, it is the first report that gets updated, stay tuned as we overhaul the rest of the reports with a completely new UI stack and additional features in the next weeks
* We have released a new iteration of **Audience Specific Status Pages**, enhancing many of its features (such as branding or notification content filters) and making it even easier to setup complex pages
* We added a new **detailed** information widget to incident coms **publish info**, showing exactly which resources and susbcribers are notified

### Integration updates

* **Site24x7** inbound integration
* Autotask outbound supports custom body fields now
* SNS inbound integration has been enhanced to support a new \_ilert.parsedMessage field, which can be used to access the keys of JSON messages in ilert templating configurations
* Cisco Meraki now supports auto resolving of alerts

## December 2024

### New features and improvements

* ilert now supports **Coverage Requests**, starting with the mobile app, you may now request a shift override from one of your on-call buddies, with the tap on a button your colleagues are notified immediately and can choose to accept or decline the request while you will receive another notificatin depending on their decision.
* We have optimized the **call flow builder experience**, lots of internal and external feedback has been used to shape an even better UX when building flows, especially larger flows
* Call flow "Route call" nodes now support a dedicated choice for **agent call timeout**s and the default has been reduced from 60 to 45 seconds (Note: the legacy call routing solution has always used 60 seconds)
* There is a new call flow node **Agentic Concierge**, it has moved into closed BETA. It replaces your IVR menus and more; use a real-time AI agent to communicate with your caller to identify the callers intent and gather additional information, use the identified intent to decide your branch flow. Let us know if you would like to try it out, before it moves into GA.
* We launched **ilert wrapped 2024, hope you had a great year with us** :)

## November 2024

### New features and improvements

* We have introduced a [new templating language "ICL"](rest-api/icl-ilert-condition-language.md) for alert source templating. While improving the syntax, we now also support conditional blocks and loops.
* A new internal alert action is available "Re-route" you may use this in combination with the unresolved or escalation ended alert events to automate a reroute action, assigning the alert to a different escalation policy.
* **Audit logs** have moved into closed BETA, the long awaited enterprise feature. Let us know if you would like to try it out before it moves into GA.
* Call flows now support a new node: **Block numbers**, it can be used to block unwanted incoming callers

### Integration updates

* We have overhauled the Raygun inbound integration, it now supports multi-alert scenarios as well
* There is a new deployment integration: [Gitlab](deployment-integrations/gitlab.md)

## October 2024

### New features and improvements

* We have launched the all new [**deployment events**](integrations/deployment-integrations/), by setting up deployment pipelines and integrating them with your **CI & CD** tools, ilert shows you insights of the latest potentially related deployments right in your alert details to provide even more context and help reduce MTTR. To kick-off we support 4 different options in integrating with [**Github actions**](integrations/deployment-integrations/github.md), while additional integrations e.g. Gitlab or Jenkins will follow up soon. Feel free to use the request option in the deployment pipeline list view, to share your integration request with our team.
* The email alert action now supports CC and BCC fields
* The [ilagent](rest-api/client-libraries/ilagent.md) has been updated to support Apache Kafka proxying from the CLI
* Alert actions now support [ICL](rest-api/icl-ilert-condition-language.md) conditions, alertFilter has been deprecated, but will continue to work - we recommend migrating though, as the new conditions are a lot more powerful + allow for dynamic filtering of an alert's event payload content

### Integration updates

* New inbound integration [Rapidspike](inbound-integrations/rapidspike.md)
* New inbound integration [Honeybadger](inbound-integrations/honeybadger.md)
* New inbound integration [Healthchecks.io](integrations/inbound-integrations/healthchecks-io.md)
* New inbound integration [Mezmo](inbound-integrations/mezmo.md)
* New inbound integration [Serverguard2024](integrations/inbound-integrations/serverguard24.md)
* New inbound integration [Apache Kafka](inbound-integrations/kafka.md)
* New inbound integration [MQTT](inbound-integrations/mqtt.md)
* We now support [Cisco Thousandeyes](integrations/inbound-integrations/thousandeyes.md) for inbound events

## September 2024

### New features and improvements

* **ilert search** is now out of closed beta and available to all ilert users

<figure><img src=".gitbook/assets/Search (1).gif" alt=""><figcaption></figcaption></figure>

* The i**lert dashboard** is now available to all ilert users in its **editable** mode, you can now create, customize and share your own dashboards with specific users or the whole account
* We have introduced a new feature to the **alert resolve bulk** action that automatically **suggest similar open alerts** based on ilert AI
* Alert detail markdown rendering has been adjusted to require explict header syntax `#` instead other inline versions e.g. `--` which caused confusion

### Integration updates

* Github action check runs have been fixed to include the Failure subtype
* We have added the [Ansible AWX ](integrations/inbound-integrations/awx.md)inbound integration

## August 2024

### New features and improvements

* We have launched a new type of status page: "**Audience specific**" use it to let your status page show services and incidents dynamically based on the context of the current viewer
* We have completely overhauled the **critical alert push notification experience on Android devices**, now allowing for the same smooth in-app setup as iOS users have already experienced for the last years
* the ilert [Microsoft Teams](chatops/microsoft-teams/chat/) bot now automatically **adds user replies** (text, links and images) to the alert card thread in the chat tool as **comments** to the related ilert alert. (Note that this only works if your users in ilert are using the same email addresses in both tools and for images to be rendered properly they need to be marked as public/shared)
* the Header header banner messages have been moved to a new API to longer affect UI performance
* we have fixed a performance issue that occured on on-call schedules with a huge amount of overrides

### Integration updates

* We have added a new inbound integration [ClusterControl](integrations/inbound-integrations/clustercontrol.md)
* We have added a new inbound integration [NetData](integrations/inbound-integrations/netdata.md)
* We have improved the Samsara integration experience
* We have improved the UptimeRobot integration experience
* The 4me inbound integration now supports automation rules
* The Cloudwatch inbound integration now supports test notifications (even if invalid JSON is provided)

## July 2024

### New features and improvements

* We have added a new feature to status pages: [Announcements](incident-comms-and-status-pages/status-pages/#faq-1), you may now add **announcements** to your page and the widget
* We have finalized our migration of all alert source event integrations to the new events API, enabling the event explorer feature for 99% of integrations (_HTTP request validation is slightly more strict, keep an eye out for your custom integrations, especially if you are unsure about: utf-8 compatibility, content-type / host header or API key integrity; reach out to support if needed_)
* We have made **ilert AI available for all customers**, by providing a service that automatically chooses EU mainland hosted large language models on ilert infrastructure for EU customers, making all of the ilert AI uses cases available to every user (customers may still choose to opt-out, to deactivate the features)
* The **ilert Search BETA** is now available for non ADMIN users as it now individually validates permissions to all search results on demand for the current user
* **ilert AI** now automatically **generates TTS audio content** for your **call flow** node texts
* We have introduced a **new alert source detail view**, which also provides insights into how effective grouping is used for the specific source

### Integration updates

* We have introduced a new inbound integration for [Postman](integrations/inbound-integrations/postman-monitors.md) Monitors
* We have improved the checkmk inbound integration to support additional event types
* We have improved the GCP alerts (former Stackdriver) integration in support alert key extraction for GCP Error events

## June 2024

### New features and improvements

* We have overhauled the **event payload experience in the alert detail** view, it now shows information in regards to grouping and expected future grouping, as well giving a pagination over all alert related events and not just the event that created the alert initially - it is also interlinked with the event explorer feature, helping you to jump right into the explorer at the point in time of the event
* We have added a new alert action event type **unresolved** to act on alerts that have not been resolved in a given time window
* We have added additional **filters** to the **call flow** session (**Calls**) view to filter for specific to-numbers as well as from-numbers
* The public status page SMS subscribers experience has been overhauled
* Errors during manual alert action triggers on alerts will now expose the original error message of the third party system

### Integration updates

* We have introduced a new inbound integration [HetrixTools](integrations/inbound-integrations/hetrixtools.md)
* We have introduced a new inbound integration [Ubidots](integrations/inbound-integrations/ubidots.md)
* We have introduced a new inbound integration KeepHQ
* The Jira inbound integration has been improved, there is now an option to chose the behaviour in case of ticket reopenings
* We have introduced new versions of the Slack and Microsoft Teams standalone webhook outbound integrations

## May 2024

### New features and improvements

* We have introduced [event filters](alerting/alert-sources.md#event-filter) for alert source, you can now add custom conditions to create or drop alerts
* We have introduced the [ICL ilert conditional language](rest-api/icl-ilert-condition-language.md)
* We have introduced a new ilert AI feature [event content similarity grouping for alert sources](ilert-ai/using-ilert-ai-for-alert-grouping.md)
* Private status pages now support a new authorization procedure, through magic link emails, you can define one or multiple domains (or specific emails) to allow users outside of your ilert organization to access the private status page (look for **email based login** in the Authorization tab)
* We have reworked the Jira outbound integration
* The Stackdriver/GCP inbound integration now supports the Error reporting payload
* The MongoDB inbound integration has been updated to support new event types
* We have introduce a new [inbound integration 4me](integrations/inbound-integrations/4me.md)
* We have improved the alert source throttling API warning display and added it to the alert source list



## April 2024

### New features and improvements

* We have reworked the setup flow for Alert actions and Connectors, admins will now find a hugely **improved Connector UX**
* We have launched **incident timelines** that give fine grained audit insights into what has changed by whom on an incident during its lifecycle
* We have launched **call logs for call flows** (call routing 2.0) providing fine grained audit insights into what has happend during and outside of the call
* The incident list will now live update, similar to the alert list
* We have added a new inbound integration: Victoria Metrics
* We have added a new inbound integration: Honeycomb
* We have improved the inbound Email integration, now providing custom alert templates e.g. to include the sender in the alert summary



## March 2024

### New features and improvements

* We have launched Call Flows aka **Call Routing 2.0** as closed BETA for selected customers, offering a completely new way to build and configure your call routing experience, reach out if you wish to join the BETA
* **AI assisted schedule creation** is now in open BETA
* We have added a new UI for Account owners and Admins to get information on the current plan, quota and usage of the account (find it via: Navigation -> Cog -> Usage and limits)
* Public status pages now remind subscribers of their missing opt-in up to 1 week
* Public status page subscriptions can now apply a filter to choose to subscribe to specific services only
* We have added a new inbound integration: HaloITSM
* We have added a new inbound integration: Kibana
* We have reworked the Elastic Watcher integration



## February 2024

### New features and improvements

* The Datadog integration has been improved
* The reports API has been improved
* The Slack and Microsoft Teams alert actions UI has been reworked
* We have added **HaloPSA** as new inbound integration
* We have added **InfluxDB** as new inbound integration
* The NCentral integration has been improved



## January 2024

### New features and improvements

* **Alert actions v2** is now in GA, offering a global top level alert action experience, team ownerships and multiple alert sources per alert action
* The Telegram integration has been improved
* Alert sources now offer an **Event Explorer** to discover and debug event traffic as well as alert creation
* Status page SMS opt-ins now use ilert's link shortner service
* Private status pages now send notifications to public subscriptions in IP range scenarios
* There is now an option to export Teams as CSV for admins
* The User CSV export has been improved



## December 2023

### New features and improvements

* The **notification aggregation** and suppression has been **reworked**, each notification channel now supports a unique suppression style e.g. voice calls now 3 per 3 minutes per alert source or push notifications now up to 20 per minute as long as their content is unique (_find out more in Alerting -> Understanding event flows -> Notification aggregation_)
* AI assisted **postmortems** is now in **open beta**, enable ilert AI in the account owner's account settings and visit an incident to try it out
* Status pages now support themes: feel free to switch to our new **status page dark theme** if it fits your branding
* The repeating schedules API has been stabilised for Terraform use cases
* We have launched **ilert wrapped 2023** (check out your responder year recap, it will be available until 12.01.24)

## November 2023

### New features and improvements

* We have introduced a new feature for SSO SAML users to prevent auto-provisioning on the SdP side for certain users called: **provisioning required attribute**
* The integrations API has been reworked to support a better catalogue experience and more information in the app's wizards
* We have improved the unverified contact log entries in the alert timeline to properly identify which contact was not verified
* We have added **dynamic priority templates to alert sources**, using these you can extract payload fields from your events and map them to the priority of your alerts
* We have added **dynamic links templates to alert sources**, using these you can extract links directly from the event payload of your alerts
* We have added a faster way to login to the ilert **mobile app using QR codes** (you can find the link in the push token area of your notification preferences in the web app)
* Over the lifetime of a recurring on-call schedule it can accumulate a large sum of ended layers, that can reduce performance, we have introduced a new **layer archiving** feature that automatically archives older ended layers, keeping the schedule fast.

### Status page updates

* We have added a **localized public status page subscription** experience for German status page visitors
* We have added a new **layout option for status page structures: responsive columns** this works especially well when displaying a large amount of services on your status page or when you want to render your status page horizontally
* The **status page opt-in and opt-out pages** are no longer landing pages on the global webapp (app.ilert.com) but instead are **hosting on your status page directly**, allowing for less of break of CI for your customers
* In addition to the new status page responsive layout, you may now decide if a group should open by default, as well as defining to display the SLA graph or not unrelated to the service's SLA history setting
* We have also added countless improvements to the rendering experience of status pages e.g. font or colors

### New and updated integrations

* New inbound integration: **Tulip**
* New inbound integration: **Graylog**
* New inbound integration: **Catchpoint**
* New inbound integration: **Loki**
* New inbound integration: **Mimir**
* New inbound integration: **Cortex**
* We have **improved the Datadog** inbound integration to support different event type flavors e.g. downtimes
* **MS Teams, Autotask and ServiceNow** alert actions can now be more easily managed through the API

## October 2023

### New features and improvemens

* **Support hours** have been moved out of alert sources into their **own entity**, you can now share a support hour across multiple sources and use team ownerships to controll access
* We have added a new **Mute notifications** feature in web and mobile app, responders can now mute their notifications for specified or customized time periods
* The **AI assisted incident postmortems** feature has reached closed BETA, reach out if you are interested in using before its GA
* We have introduced a feature that autmatically archives historical layers of large repeating on-call schedules, to keep performance steady no matter the use-case
* Integration icon and logo generation has been reworked for web and mobile to improve performance of the UI
* **Reworked SMS notifications** to allow for a better focus on alert summary content
* Alerts in state ACCEPTED may now be accepted by responders that are not yet added to the responder list of the alert

### New and updated integrations

* Auvik alert creation has been improved (new fields)
* The Grafana inbound integration now supports custom priority mapping based on label values

### ChatOps

* The Microsoft Teams bot now supports a new who is on call command (**@iLert oncall**) that can be customized for teams and channels using a Microsoft Teams alert source
* The Microsoft Teams Activity Feed display information for the bot's cards has been improved

### Terraform

* New alert action filter types have been added
* Alert source templates (text form) are now available in Terraform
* delayMin field for escalation policies
* New alert source time based grouping options are now available in Terraform

## September 2023

### New features and improvements

* The schedule detail view calendar mode now creates shareable URLs that include your calender configuration
* Static schedules received multiple improvements for QoL and a new default shift start setting that is remembered for your user profile
* Call routing speech detection has been improved for certain scenarios where the input was not properly detected
* The alert comment (messages) UI has been reworked
* Alerts can now be manually linked to incidents (and also unlinked from them)
* Last activity in (admin's) user list is updated more frequently for web UI activity
* Status page enduser facing email communication now resolves the status page name as friendly email from address
* We have relaxed the view permission checks for Maintenance Windows a little (Note: edit permissions stay the same) it is no longer required to have a permission to access every single related alert source and service, but now sufficient to have access to a single one of those related entities
* You can now provide custom time ranges for overrides in my-oncalls, giving you more flexibility if you want to override partial shifts
* The subscription button on private status pages now adjusts its state asynchronously depending on the current viewer
* We have added an additional step to prevent accidental deletion of resource like alert sources
*   Alerts with linked incidents are now marked with a :fire: icon

    <figure><img src=".gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

#### Manual alert escalation

You no longer need to lookup who's next in the escalation chain. You can now manually escalate alerts to an escalation level of your choice. The escalation process will resume from the selected level.

<figure><img src=".gitbook/assets/manual-escalation.gif" alt=""><figcaption></figcaption></figure>

#### Support for partial overrides on the My on-call shifts page

Ever wanted to take someone else's on-call, but not their entire week long shift, but only for a day? Now you can do this from the **My on-call shifts** (both in the web and mobile app) page when taking someone else's on-call and overriding your shifts. Until now, this was possible only on the on-call schedule itself.&#x20;

<figure><img src=".gitbook/assets/partial-overrides.gif" alt=""><figcaption></figcaption></figure>



### Alert actions first party BETA

This has been in the making for a while: we have completely overhauled our alert actions and connector UIs and APIs, giving tons of new QoL features like multi alert source assignments or team management to alert actions. We have launched the closed **BETA** and would love to hear your feeback on it - so if you are interested in trying it out just **reach out via email or live chat**.

<figure><img src=".gitbook/assets/image (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### New and updated integrations

* A new inbound integration has been added for Particle
* The Grafana inbound integration now supports the cluster alert label to build alert summaries by default

### Chatops

* The ilert Slack bot now supports a new [**who is on call**](chatops/slack/lookup-who-is-on-call.md) command ( /ilert oncall )
* Create dedicated channels in Microsoft Teams to communicate alert updates
* New /il-alert command to create alerts from within Slack - you can customize this feature for your team and Slack channels using a Slack alert source
* The Slack bot now supports further alert based interactions such as raise, reroute, escalate etc.

## August 2023

### New features

* You may now choose your primary phone number, if you are using multiple contacts. The primary phone number will be preferred when making call routing agent calls or showing your number to other users in on-call requests
* You can now choose a specific timed window to group your alerts in your alert source e.g. group all incoming events for 5 minutes, until creating the next alert
* The alert source creation process has ben overhauled, there is a now a wizard that guides through the most important steps of the setup

### New and updates integrations

* New inbound integration Twilio Errors
* New inbound integration Uptime Kuma
* We have overhauled and enhanced our Github inbound integration, you may now choose specific alert action types and event types for which to create or resolve alerts, we also do support **Github Advanced Security** type webhook events now
* Grafana v9 Links have been optimized, instead of showing general instance links we prefer to show specific dashboard links now
* It is now possible to turn an alert source bidirectional even though it was already created
* You can now choosen to enhance Autotask inbound alerts with company details, by enabling the specific setting for your Autotask alert source in ilert
* You may now choose if you want to receive full text alert details or short forms in Microsoft Team channel notifications, by adjusting the **longDetails** field in your MS Teams connector

### Chatops

* Create dedicated channels in Microsoft Teams to communicate alert updates
* Added new create alert feature to Microsoft Teams bot (note: you may optionally customize the behaviour using ilert [Microsoft Team alert sources](chatops/slack/create-alerts-in-slack.md#overview))
* It is now possible to re-authorize your Microsoft Teams bot without removing your existing alert actions

## July 2023

### New features

* Added a new text mode for alert source templates, you can use the top right icon in the input area to switch between text and block mode when creating alert templates
* API key analytics are now available showing live API key resource usage for every user (Navi -> Profile -> Manage API keys) this feature also ships with an API resource for ADMINs to fetch account wide API usage information see [https://api.ilert.com/api-docs/#tag/Reports/paths/\~1reports\~1api-keys\~1usage/get](https://api.ilert.com/api-docs/#tag/Reports/paths/~1reports~1api-keys~1usage/get)

### Mobile app

*   [Maintenance windows](alerting/maintenance-windows.md) are now also available in the mobile app\


    <figure><img src=".gitbook/assets/pika-1691784090207-1x.png" alt="" width="188"><figcaption></figcaption></figure>
* The alert creation view has been reworked to match the features of the web UI

## June 2023

### New features

* Migrated the platform to a new infrastructure, improving performance, scalability and availability
* New session management, allowing for more secure and longer running sessions
* Added remember me option for even longer running web sessions
* 2-FA codes are now supported by the mobile app's login
* We launched [ilert AI](broken-reference), which adds advanced generative artificial intelligence features for responders along the incident management lifecycle

### New and updated integrations

* Updated Slack bot
* Added new create alert feature to Slack bot (note: you may optionally customize the behaviour using ilert [Slack alert sources](chatops/slack/create-alerts-in-slack.md))

## May 2023

### New features

* New navbar widget for user onboarding and product updates
* Improved performance of schedule UIs

### New and updated integrations

* Google Cloud Security Command Center inbound integration

## April 2023

### New features

* Brand new alert source list and edit UI
* Brand new call routing number list UI
* Brand new maintenance window list UI
* User list CSV export

### New and updated integrations

* Improved the Sentry inbound integration
* New status field for Autotask outbound integration
* Improved Autotask outbound company search, now dynamically fetching based on search input
* Upgraded Jira outbound integration to dynamically detect Jira Cloud, Jira Server and other Jira versions and switch the API automatically so that old and new installations are seemlessly supported

## March 2023

### New features

* We have launched a new feature for notification preferences: **live test notification** status
* We have added additional states to our alert notification timeline events, that now allow you to (live) **track the status of outbound alert notifications** and see if they have been delivered to or (e.g. Whatsapp) read be the responder, they work seemlessly for all notification channels
* We have launched an overhowl of our escalation policy list and detail views
* We added additional details to delete dialogs across the platform
* We have introduced the new ilert Free billing plan
* The user list search has been improved
* Alert email notifications links now come with an additional confirmation step

### New and updated integrations

* New Checkly inbound integration
* Optimized Appdynamics inbound integration

## February 2023

### New features

* Generic alert summary, details and routingKey templating with our **new template editor for alert sources**.
* **We have launched a complete re-work of our Notification Preferences feature**
* shiftColor is now supported in API
* Public status pages may now receive unlimited subscriber imports in state INACTIVE, during activation a license with a fitting range of subscriptions is needed however.
* We have enhanced the information in our /api/integrations resource

### New and updated integrations

* Cisco Meraki has been added as new inbound integration
* We have optimized our PRTG inbound integration

## January 2023

#### New features

* You may now backfill incidents via the API
* New on-call widget in mobile apps for iOS and Android
* Improved maintenance window creation
* Improved 2FA login experience

#### New and updated integrations

* Further improvements to the ServiceNOW bidirectional integration
* Status page service groups structure and metrics for [Terraform](https://registry.terraform.io/providers/iLert/ilert/latest)
* Improved version of the [ilert browser extension](https://github.com/iLert/ilert-chrome)

## December 2022

#### New features

* Metric data source credentials are now validated during creation
* Status pages now support service groups
* Dozens of new schedule override features that make it easier and faster to add overrides on the fly
* Reworked My-on-calls features to take and pass on-call shifts
* New end-of-escalation reached events for alert actions
* Status page SMS and Webhook subscriptions

#### New and updated integration

* checkmk alert detail parsing has been improved
* checkmk now supports custom detail labels

## November 2022

#### New features

* We have updated our platform to our new logo and CI
* automation rules (alert -> incident) have been integrated into alert actions and may now be manually triggered or configured with conditional execution
* Status pages will now automatically collapse large amounts of services, SLA data and uptime graph are fetched on demand by opening collapsed services

#### New and updated integrations

* Prometheus metrics data source
* new relic now supports the new [workflow](integrations/inbound-integrations/new-relic/new-relic-workflow.md) events
* Prometheus inbound integration now supports the custom url and urlLabel labels (added as links to alert)
* Microsoft SCOM inbound [integration](integrations/inbound-integrations/ms-scom.md)
* Twilio Alarms inbound [integration](integrations/inbound-integrations/twilio-alarms.md)

## October 2022

#### New features

* New major milestone: **metrics** for status pages

#### New and updated integrations

* PandoraFMS [inbound](integrations/inbound-integrations/pandorafms.md) integration
* HashiCorp Cloud (HCP) Consul support
* Terraform client now supports mulitple responders in escalation policies
* Datadog metrics data source

#### Other

* ilert **Backstage** plugin has been updated to support mulitple responders, services and status pages

## September 2022

#### New Features

* An initial delay can be configured for escalation policies
* Private status pages now support IP whitelists
* Service uptime history can now be managed and overwritten

#### Improvements

* Alert submit UI supports additional fields to overwrite: priority, policy or responders
* Added MFA reset for Admin users

#### New and updated integrations

* Jira alert sources now support Service Desk Events
* Grafana alert sources now support Grafana V9 events

## August 2022

**New features**

* This feature has been long-awaited by many customers: we have added support for **Multiple Responders**
* \=> Escalation policy rules now support multiple users and schedules
* \=> During the escalation of an alert all responders will be added to the alert
* \=> A user may request additional help of another responder on any open alert
* We have added a new messenger for alert notifications: **Telegram**, users may connect their ilert account to their Telegram app and respond to alerts on their favorite messenger
* We have added live updates to our alert list view
* Status pages of a team can now be managed in the team admin view

**Improvements**

* We have completely reworked the alert list view, users will now see additional information and improvements such as responders and their individual alert status, escalation policy filter, **aggregation status of events for a specific alert**, bulk resolve comments, highly reduced load and response times, deep links for filter configurations
* We have completely reworked the user list view, admins have now access to new tools and filters that should help them with their day to day tasks: filter for roles, mfa status and team membership, pagination, highly reduced load and response times, deep links for filter configurations
* Increased status page service limit from 30 to 100
* Doubled the API rate limits for Terraform clients
* Improved response time of team edit view

**New and updated integrations**

* Increased amount of fetched companies for Autotask connectors to 1000 and added a search view to the selection

**Other**

* Alert reports are now available in the professional plan, on-call reports stay a premium only feature

## July 2022

### New features

* Maintenance windows now support services and appear on related status pages
* Maintenance window now offer different types of notifications along their lifecycle when affecting services or status pages with private or public subscribers
* ilert will now inform the owner of incidents (via email) that are publicly visible on status pages in case they have been pinned there for longer than 4 hours
* Alert actions may now be cloned to other alert sources
* We now support conditional execution for alert actions making it possible to filter and tune alert streams to webhooks or tools like Microsoft Teams and Slack

### Mobile apps

* Now support incident list and detail views
* Now support status pages and services
* We have reworked the navigation as well as the stakeholder user experience
* We have improved the performance for customers with a large amount of teams and users

### Improvements

* we have introduced a new region field for users and adjusted all calendar and date/time relevant components to deliver a seemless localized experience

### New and updated integrations

* Our Zabbix native integration now supports [severity mapping](integrations/inbound-integrations/zabbix/native.md#faq) and [bidirectional problem/alert acknowledgement](integrations/inbound-integrations/zabbix/native.md#faq-1)

## June 2022

### New features

* The s[ervice outage edit API ](https://api.ilert.com/api-docs/#tag/Service-Outages)is now available
* All public facing incident communications emails now support beautifully crafted html email versions
* We have introduced a new feature for private status pages to make them available to any user within an organization even if the entity itself is owned by a private team or hidden from stakeholders "Account Wide View"
* we have launched a [public roadmap](https://roadmap.ilert.com/roadmap)
* we have launched a completely new onboarding experience for new accounts
* added a new subscription API endpoint for status pages to add or remove a single subscriber

### Improvements

* the MFA status is now visible in the user list
* browser caching of certain script and style resources has been optimized for faster page load

### New and updated integrations

* [Samsara Inbound integration](integrations/inbound-integrations/samsara.md) has been added

## May 2022

### New features

* Conditional alert actions; you may now add additional filters to alert actions
* Alert action duplication, you may now easily copy and paste an alert action to other alert sources
* Call routing numbers may now use uploaded audio files to playback greeting, waiting and mailbox messages
* New endpoints have been added to the API to support add and remove operations for single user/team private subscribers

### Improvements

* Overall page load times have been reduced for the web-ui, especially for accounts with large user and team bases

### New and updated integrations

* Sentry inbound integration has been improved to support alert metric events
* Autotask inbound integration has been improved to support new webUrl attribute for ticket link generation
* SignalFX inbound integration has been improved to support better alert detail extraction

## April 2022

### New features

* [Status pages](incident-comms-and-status-pages/status-pages/) and[ Incident comms 2.0](broken-reference) are now in GA
* New [alert creation API](https://api.ilert.com/api-docs/#tag/Alerts/paths/~1alerts/post) e.g. possible to target specific user
* [2FA and MFA ](user-administration/two-factor-authentication-mfa.md)are now available for every ilert user
* Call routing is now available in Italian

### New and updated integrations

* Hyperping Integration
* Paoloalto Networks Prisma Cloud Integration

## March 2022

### New features

* We have launched private and public status pages in closed BETA.
* We have launched [dynamic alert actions](broken-reference) (application hooks) in closed BETA.

### Improvements

* User shift color (profile settings) is now used in all schedule visualisations
* Status page editors now receive update notifications when the domain status of their page changes

### New and updated integrations

* IXON alert source now supports dynamic routing

## February 2022

### New features

* We have launched the [ilert developer platform](rest-api/developing-ilert-apps/), which enables you to create your own applications on top of ilert's uptime platform and share them with other ilert users.
* [Incident Communications 2.0](broken-reference) is now in public BETA for all Premium users.
* Support for WhatsApp as a notification channel

### Improvements

* Event API: routingKey may now be used to re-assign alerts during ALERT events
* Alerts API: escalationPolicy attribute is now included in the response payload
* Services of teams can now be managed in the teams admin UI

### New and updated integrations

* Our ServiceNow bidirectional integration now supports dynamic mapping of assignmentGroups and escalation policies (as well as re-assignment)

## January 2022

### New features

* we have launched our Incident Communications 2.0 BETA, [reach out to us](contact.md) to join during the testing phase
* On-call schedules: we now allow you to create more complex recurring schedules with [schedule layers](on-call-management-and-escalations/on-call-schedules/recurring-schedules.md#schedule-layers).
* New alert view: as part of our new Incident Comms 2.0 feature, a brand new revamp of our Alert Detail View has been launched, including live updates for Alerts and Alert related information.
* as part of our Incident Com 2 Feature, Stakeholder users may now use the web login (they were previously limitted to the Mobile App only)

### Improvements

* the `GET /api/log-entries` [resource](ilert-release-notes.md#undefined) now supports `?include=vars` and `?filter-types=ALERT_UPDATES` parameters, as well as pagination for more advanced and detailed alert timeline access
* Microsoft Teams Alert Actions have been rebuild to support a direct Teams query for enterprise customers with > 10k Teams.
* the (Support) Live Chat has been made available to EU customers (see Account Settings

## December 2021

### New and updated integrations

* Oh Dear [Inbound](integrations/inbound-integrations/ohdear.md)
* Gitlab Inbound [Integration](integrations/inbound-integrations/gitlab.md)

## November 2021

### New features

* users may now choose their personal shift color that is rendered in schedules

### New and updated integrations

* Humio Inbound
* Apifortress Inbound
* Freshdesk Inbound
* AppSignal Inbound
* Lightstep Inbound
* IBM Cloud Functions Inbound
* Crowdstrike Inbound

### Improvements

* critical alert push notifications are no longer triggered for update notification types
* update type notifications are now fanned out to all registered push token devices
* call routing numbers now support blacklists for incoming callers
* assign to policy action no longer sends two notifications but one
* added re-authorize option for Slack bot
* updated all alert source and connector icons to newest version with increased resolution
* the resolving user will no longer receive a resolve notification

## October 2021

### New features

* we have released a new version of our API check [here for more info](rest-api/api-version-history/)
* we have added a new API resource [incident reports](https://api.ilert.com/api-docs/#tag/Reports)

### New and updated integrations

* new inbound integration IXON
* new inbound integration Salesforce
* new inbound integration Jumpcloud
* new inbound integration StatusHub
* new inbound integration AWS GuardDuty

### Improvements

* rendering performance of timelines of schedules has been improved

## September 2021

### New features

* added policy routingKeys to the [event API](https://api.ilert.com/api-docs/#tag/Events/paths/~1events/post)
* added a new uptime monitor type: SSL

### New and updated integrations

* added dynamic user-, priority- and policy mapping to our [ServiceNow integration](broken-reference)
* updated [Jira inbound integration](broken-reference) to support alert creation on update events
* added new fields for [ServiceNow outbound](integrations/outbound-integrations/servicenow.md) alert creation

### Improvements

* added response keywords check for HTTP uptime monitors
* added option to delete user avatar
* increased displayed team name sizes in action dropdowns and list views

## August 2021

### New features

* [My on-call shifts](on-call-management-and-escalations/on-call-schedules/my-on-call-shifts.md) page
* Avatar upload (in user contact details)

### New and updated integrations

* Microsoft Teams Chat (new bot)
* Microsoft Teams Meeting (new bot)

### Improvements

* updates for on-calls API
* updates for schedule shifts API

## July 2021

### New and updated integrations

* Zendesk inbound integration now supports attaching comments to alerts
* Zammad inbound integration now supports attaching comments to alerts

## June 2021

### New and updated integrations

* Zendesk inbound integration
* Additional DingTalk Action that does not require a connector setup

### New features

* Added `team-context` HTTP header to control team context on a per request basis when using api keys
* Escalation policy detail view has been added
* Attaching comments to alerts is now additionally possible through the events [API](https://api.ilert.com/api-docs/#tag/Events/paths/~1events/post)

### Improvements

* Improved team details in settings view
* Preventing ongoing call routing sessions from intervention through accept and resolve actions through mobile
* Email bounces are now made visible in the user contact information
* Updated algorithm to improve search results in list views

## May 2021

### New and updated integrations

* The alert priority of Zammad, ServiceNOW and SearchGuard Inbound Integrations is now fully managed in the alert source
* DingTalk Outbound Integration

### New features

* Added option for account owners to disable report sharing
* Added API keys, which may now be created by each user and provided during API calls instead of basic auth
* Added option to logout of all mobile devices using the web UI

## April 2021

### New and updated integrations

* New: [Zoom Chat](broken-reference) Integration
* New: [Zoom Meeting](broken-reference) Integration
* New: [Microsoft Teams Chat](chatops/microsoft-teams/chat/) Integration
* New: [Microsoft Teams Meeting](chatops/microsoft-teams/meeting.md) Integration
* New: [MXToolBox](integrations/inbound-integrations/mxtoolbox.md) Integration
* New: [Azure Alert Sentinel](integrations/inbound-integrations/azure-alerts/sentinel.md) Integration

### New features

* On-calls REST API [resource](https://api.ilert.com/api-docs/#tag/On-Calls)

## March 2021

### New and updated integrations

* New: Azure Alerts Integration for [Azure Activity Logs](integrations/inbound-integrations/azure-alerts/activity-logs.md)
* New: Azure Alerts Integration for [Budget Alert](integrations/inbound-integrations/azure-alerts/budget.md)
* New: Azure Alerts Integration for [Azure Logs](integrations/inbound-integrations/azure-alerts/logs.md)
* New: Azure Alerts Integration for [Azure Metric](integrations/inbound-integrations/azure-alerts/metric.md)
* New: Azure Alerts Integration for [Azure Sentinel](integrations/inbound-integrations/azure-alerts/sentinel.md)
* New: Azure Alerts Integration for [Service Health](integrations/inbound-integrations/azure-alerts/service-health.md)
* New: [SignalFx Inbound](integrations/inbound-integrations/signalfx.md) Integration
* New: [Terraform Cloud / Terraform Enterprise Inbound](integrations/inbound-integrations/terraform-cloud-terraform-enterprise.md) Integration
* New: [Sentry Inbound](integrations/inbound-integrations/sentry.md) Integration
* New: [Kubernetes Inbound](integrations/inbound-integrations/kubernetes.md) Integration

### Improvements <a href="#improvements" id="improvements"></a>

* [Nagios](integrations/inbound-integrations/nagios.md) / [CheckMK](integrations/inbound-integrations/checkmk/check-mk.md) Plugin: Use proxy for the outbound traffic via `--proxy` flag
* [Nagios](integrations/inbound-integrations/nagios.md) / [CheckMK](integrations/inbound-integrations/checkmk/check-mk.md) Plugin: Disable SSL certification validation (e.g. to use self-signed certificates) via `--insecure` flag

## February 2021

### New features

* [Advanced support hours routing](call-routing/call-routing-legacy/routing-calls-based-on-support-hours.md) for call routing numbers
* Auto provision [teams and mobile](user-administration/single-sign-on/auto-provisioning-users-and-teams.md) numbers with SSO

### New and updated integrations

* New: [Zammad Inbound](broken-reference) and [Outbound](integrations/outbound-integrations/zammad.md) Integration
* New: [Mattermost Outbound](integrations/outbound-integrations/mattermost.md) Integration
* New: [Splunk Inbound](integrations/inbound-integrations/splunk.md) Integration
* New: [Elastic Search Guard Inbound](integrations/inbound-integrations/search-guard.md) Integration
* New: [ServiceNow Inbound](broken-reference) Integration
* Updated PRTG integration: custom alert summary and details based on PRTG placeholders.

### Improvements

* Call Routing Number User Interface rework

## January 2021

### New features

* [Team based organisation](user-administration/teams.md)

### Improvements

* New on-call schedule styles for all schedule views
* SAML2 SSO auto-provision now supports [custom provision attributes](https://docs.ilert.com/single-sign-on/setting-up-sso-with-azure-active-directory#passing-additional-attributes-during-auto-provisioning)

## December 2020

### New features

* Irregular Schedules new calendar UI
* Call Routing: You may now choose if an alert is resolved on agent/caller hang-up

### New and updated integrations

* New: [Autotask Outbound Integration](integrations/outbound-integrations/autotask.md)

### Improvements

* Links and Images for Alerts with automatic connections
* Adedd [international caller IDs for voice alerts](alerting/phone-numbers/#voice-alerts) for USA and Canada, UK, Australia, Belgium and Netherlands

## November 2020

### New features

* New Notification Reports
* Connectors and Connections are now available [via API](https://api.ilert.com/api-docs/#tag/Connections)
* New [Go Client](https://github.com/iLert/ilert-go) with full API support
* New [Terraform Provider](https://registry.terraform.io/providers/iLert/ilert/latest/docs) with full API support

### New and updated integrations

* New: Zapier [Inbound](broken-reference) and [Outbound](integrations/outbound-integrations/zapier.md) Integration
* New: Jira [Inbound](broken-reference) Integration
* New: Server Density [Inbound](integrations/inbound-integrations/serverdensity.md) Integration
* New: [Consul](integrations/inbound-integrations/consul.md) integration
* Updated [Email integration](integrations/inbound-integrations/email/): email deduplication now also works for email threads
* Updated [Pingdom integration](integrations/inbound-integrations/pingdom.md): alerts created by Pingdom now include a backlink to Pingdom

## October 2020

### New features

* Added new [Responder role](user-administration/user-roles-and-permissions.md#responder)
* On-call duty notifications

### New and updated integrations

* [Sysdig Inbound and Outbound Integration](integrations/inbound-integrations/sysdig.md)

### Improvements

* Call routing: added mailbox transcription to alert details and made voicemail links easier accessible in the alert links section

## September 2020

### New features

* Alert Actions
* Support for outbound connections in Call Routing Numbers
* Support Hours for Call Routing Numbers

### New and updated integrations

* [Email Outbound Integration](integrations/outbound-integrations/email.md)
* [Kentix AlarmManager](integrations/inbound-integrations/kentix-am.md)
* Datadog Outbound Integration now supports regions
* Prometheus alert detail formatting has been updated
* Slack channels (connections) can now be managed in ilert directly

### Improvements

* Ability to select alert events in outbound integrations. Example: trigger webhooks for alert creation and resolution events, but ignore remaining alert event types.
* Every call routing number is now referenced to an alert source, helping you connect incoming calls to e.g. Slack. You can now also manage support hours for your call routing number.
* Optimized bulk alert actions like accept and resolve
* Uptime monitor TCP and UDP modes now support first packet and expected packet
* Further improvements on our API to optimize response time and delivery for our mobile app
* New API endpoint /numbers

## August 2020

### New features

* Ability to re-route alerts to escalation policies and on-call schedules
* Suggested responders: when re-routing an alert, ilert now suggests you the best responder based on historic data

### New and updated integrations

* [Autotask](integrations/inbound-integrations/autotask.md)
* [Zabbix](integrations/inbound-integrations/zabbix/native.md) (updated): Starting Zabbix 4.4, ilert can be integrated as a media type into Zabbix. Zabbix 5.0.4+ includes ilert as a media type by default. See also Zabbix blog post: [Working with multiple on-call teams using Zabbix and ilert](https://blog.zabbix.com/working-with-multiple-on-call-teams-using-zabbix-and-ilert/11847/)
* [Prometheus](integrations/inbound-integrations/prometheus.md) (updated): improved readabiltiy of prometheus alerts

### Improvements

* Alert source overview page now includes outbound connections
* User profile: low priority notifications rules are entirely optional, i.e. a user can now chose to not receive any notification for low priority alerts

## July 2020

### New Features

* [Heartbeat Monitoring](alerting/heartbeat-monitoring/)

## June 2020

### Updated integrations

* [Email](integrations/inbound-integrations/email/): added ability to resolve alerts via email

### Improvements

* [Stakeholder engagement](user-administration/user-roles-and-permissions.md): stakeholders can now unsubscribe from alert update notifications
* Email login: Users can now login via email (in addition to username) . Usernames in ilert are deprecated and will be removed in the future.

## May 2020

### New features

* [Stakeholder engagement](user-administration/user-roles-and-permissions.md): keep stakeholders in the loop during critical alerts.

### New and updated integrations

* [AWS Personal Health Dashboard](integrations/inbound-integrations/aws-phd.md)
* [StatusCake](integrations/inbound-integrations/statuscake.md)
* Serverless outbound integrations:
  * [AWS Lambda](broken-reference)
  * [Google Cloud Functions](broken-reference)
  * [Microsoft Azure Functions](broken-reference)
* [Icinga v2.x](integrations/inbound-integrations/icinga.md) (updated): there is a dedicated plugin for Icinga now on our [GitHub repo](https://github.com/iLert/ilert-icinga). You can now override the alert priority from within Icinga and we include the comments that you enter in Icinga when ack’ing a problem in the event log of the alert.
* [JIRA](integrations/inbound-integrations/jira.md) (updated): When you setup a connection from your alert source in ilert to your JIRA instance, projects and issue types are now dynamically fetched from your JIRA instance, so you can select the issue types when ilert syncs an alert to JIRA. You can even include custom fields.
* [Webhook](integrations/outbound-integrations/webhook.md) (updated): you can now fully customize the payload for outbound webhooks.

### Improvements

* [API end point](https://api.ilert.com/api-docs/#tag/Uptime-Monitors) for uptime monitors
* Uptime monitors: support for milliseconds in check timeout
* Flexible periods in repeating on-call schedules: set an arbitrary period length and chose between days and weeks as the period unit ([blog post](https://www.ilert.com/blog/2020-05-27-stakeholder-engagement-release-notes/#flexible-periods))

## April 2020

### New features

* [Single Sign On](broken-reference): Single sign on makes it easy to manage access to your ilert account using an identity provider of your choice.
* **Alert Reporting** includes key metrics such MTTA and MTTR.

### New integrations

* [AppDynamics](integrations/inbound-integrations/appdynamics.md)
* [TopDesk](integrations/inbound-integrations/topdesk.md)
* [Discord](integrations/outbound-integrations/discord.md)
* [GitHub](integrations/inbound-integrations/github/)
* [Dynatrace](integrations/inbound-integrations/dynatrace.md)

### Improvements

* **Auto raise alert priority** lets you delay notifications and escalations until support hours start ([blog post](https://www.ilert.com/blog/release-notes-incident-reports-sso-auto-raise-priority-new-integrations))
