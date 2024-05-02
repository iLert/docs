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
**Service status changes and notifications**

Service status changes on the service itself (i.e. without an incident) will not notify subscribers about the change. Subscribers will be notified only if an incident is created with affected services to which the subscriber is notified.
{% endhint %}

## Create a service

To create a new service, navigate to the Services page, click on the **Create new service** button.

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.00.00 (2).png>)

Give the service a name that is descriptive to the users of the service and click on **Create service**.

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.07.12.png>)

The service is now ready to be used in incidents or included in status pages.

## Automation with alert sources

You can automatically set the status of a service and create incidents using alert actions that are triggered by your alert sources.

To configure an automation

* click on **Alert sources** -> **Alert sources** in the navigation bar
* choose an alert source and navigate to the tab **Alert actions**
* click on **Create new alert action**
* select type ilert -> **Create incident or update status page or service**

![](<../.gitbook/assets/Alert sources (1).png>)

Once you have configured an automation's settings, any alert that will be created on the chosen alert source will automatically set the status of your service. Make sure that the trigger mode is set to **Automatic** for the alert action to trigger automatically for every alert:

![](<../.gitbook/assets/Screenshot 2023-01-10 at 13.34.17.png>)

## Service uptime

### How to hide historical service uptime

By default, a service's historical uptime is shown and you can choose to hide service uptime on the status page. If you'd like to globally disable historical uptime, thus preventing any status page from displaying the historical uptime, you can do so in the service settings:

1. Go the services page and click on the service for which you wan to hide the uptime
2. In the **Settings** tab, check the option **Never show historical uptime** ![](<../.gitbook/assets/Screenshot 2023-12-01 at 12.56.38.png>)
3. Click on **Save**

### How is the uptime of a service calculated?

The uptime percentage of a service is calculated based on the status of the service over a given period. ilert displays the uptime over a period of up to 90 days. We consider the states **Operational**, **Degraded** and **Under maintenance** as uptime. The states **Major outage** and **Partial outage** are counted as downtime, where partial outage minutes only count 30% as much as major outages.

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
Outages that last less than a minute will be ignored and won't show up as downtime in the uptime graph.
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
