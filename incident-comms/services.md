# Services

Services model business capabilities to which users rely on and can subscribe to receive incidents.

A service has any of the following states:

| Status            | Description                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------- |
| Operational       | All aspects of the service are working as expected.                                               |
| Under maintenance | The service is under maintenance.                                                                 |
| Degraded          | The service is working but is impacted in a minor way, e.g. its performance is slower than usual. |
| Partial outage    | The service is not working for a subset of customers, e.g. a certain region.                      |
| Major outage      | The service is not available.                                                                     |

The status of a service can be updated during the creation of an incident or independently without an incident.

{% hint style="info" %}
Service status changes on the service itself (i.e. without an incident) will not notify subscribers about the change. Subscribers will be notified only if an incident is created with affected services to which the subscriber is notified.
{% endhint %}

## Create a service

To create a new service, navigate to the Services page, click on the **Create new service** button.

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.00.00 (2).png>)

Give the service a name that is descriptive to the users of the service and click on **Create service**.&#x20;

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.07.12.png>)

The service is now ready to be used in incidents or included in status pages.

## Automation with alert sources

You can automatically set the status of a service and create incidents using automation rules that are triggered by your alert sources.&#x20;

To configure an automation

* navigate to the **Automation** tab **** of a service
* click on **Add alert source** and select the alert source that should trigger the automation
* click on **Configure automation**

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.11.23.png>)

Once you configure an alert source's automation settings, any alert that will be created will automatically set the status of your service:

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.12.32.png>)

## Service uptime

### How to hide service uptime

By default, a service's historical uptime is shown. You can chose to hide the historical uptime of a service in the service settings:

1. Go the services page and click on the service for which you wan to hide the uptime
2. In the **Settings** tab, uncheck the Option **Show historical uptime** ![](<../.gitbook/assets/image (52) (1).png>)****
3. Click on save

### How is the uptime of a service calculated?

The uptime percentage of a service is calculated based on the status of the service over a given period. iLert displays the uptime over a period of up to 90 days. We consider the states **Operational**, **Degraded** and **Under maintenance** as uptim. The states **Major outage** and **Partial outage** are counted as downtime, where partial outage minutes only count 30% as much as major outages.

Over a period _t_, the uptime percentage is calculated according the the following formula:

$$
u=1-{m+(p*0.3) \above{1pt} t}
$$

where

* _u_ is the uptime percentage
* _m_ is the major outage in minutes
* _p_ is the partial outage in minutes
* _t_ is the period in minutes

**Example**: During a period of 24 hours, a service was 5 minutes in the status **Major outage** and 30 minutes in the status **Partial outage**. The uptime of the service for that 24 hours period is calculated as follows:

$$
u=1-{5+(30*0.3) \above{1pt} 1440}=99.03 \%
$$

{% hint style="info" %}
Outages that last less than a minute will be ignored and won't show up as downtime in the uptime graph.&#x20;
{% endhint %}

## Add / remove subscribers to a service

Subscribers will automatically receive incident updates when the **Send notifications** option is selected during incident updates. There are two ways to subscribe users to a service

1. Users can add / remove themselves as subscribers
2. A user with Responder privileges can manually subscribe users or entire teams to a service

To self-subscribe to a service, go the Services page and click on **Subscribe.** To unsubscribe, click on the **Unsubscribe** button.

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.14.58.png>)

{% hint style="info" %}
**Team subscriptions**

Note that an unsubscription takes precedence over a team subscription. That is, if you are subscribed to a service, because you are a member of a team that is subscribed to the service, and if you unsubscribe yourself from that service, you won't receive any further updates from that service.
{% endhint %}

To add or remove users and teams as subscribers from a service, go to the **Subscribers** tab from the service.

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.18.44.png>)
