# Creating alerts through events

While there is the option to synchronously create alerts, we always recommend using the asynchronous events API to create and interact with alerts, especially in high volume or monitoring tool scenarios. The API endpoint allows you to not only create, but also accept, reroute and resolve alerts.&#x20;

More schema based information on this can be found in the [API reference](https://api.ilert.com/api-docs/#tag/events/post/events).

## Creating an alert:

Send a **POST** request to&#x20;

```
https://api.ilert.com/api/events
```

```json
{
  "apiKey": "il...", // api key of the alert source (required)
  "eventType": "ALERT", // ALERT for creation, ACCEPT or RESOLVE (required)
  "summary": "Your alert summary", // (required)
  "details": "", // (optional) larger content description of your alert (markdown supported)
  "alertKey": "abc123", // (optional) key used to group events together or ACCEPT and existing alert
  "priority": "HIGH", // (optional) HIGH (with escalation), LOW (no escalation)
  "images": [{"src": "https://...jpeg"}], // (optional) absolute image urls, will be rendered in web/app UI
  "links": [{"href": "https://...", "text": "A link"}], // (optional) deeplinks into tools etc., will be rendered in web/app UI
  "customDetails": { "some": { "more": "fields" }} // (optional) additional fields used for templating, sharing or storing information
  "routingKey": "abc123", // (optional) overwrite escalation policy of alert source for ALERT events
}
```

{% hint style="danger" %}
Note that the`apiKey`field does not refer to a Bearer authentication token for the ilert API itself but instead to the API key of the desired alert source. The API key can be found in the detail view of the alert source, there is no need to provide the Authorization header for the events API.
{% endhint %}

Visit the web UI or the mobile app (under Alerts) to confirm your event created a corresponding alert.

## More details on fields

### alertKey

Used to identify other open (unresolved, unaccepted) alerts and append additional events, or accept or resolve them. The platform will always search for the last open matching alert with alertKey when processing new incoming events. The behaviour here also depends on the chosen grouping options in your alert source, for more information see **Alert grouping** section in:

{% content-ref url="../../alerting/alert-sources.md" %}
[alert-sources.md](../../alerting/alert-sources.md)
{% endcontent-ref %}

### priority

By default, the priority set in the alert source will be considered as the default priority.\
However, the priority can be overridden by the event, if one of the following conditions are met:

* Integration type of the alert source is **Grafana** or **ServiceNow**
* Custom priority template is configured in alert source (however in this case the template extraction might overrule the API field, depending on the configuration in your alert source)
* Default priority of alert source is set to **HIGH** (_using support hours or setting the source to LOW will ignore your event priority field_**)**

**routingKey**

The routingKey field is used to dynamically assign an escalation policy in case the event will create an new alert. By default the policy assigned to the alert source is used, however if an escalation policy with the matching routing key is found it will be used instead. (You can assign routing keys to escalation policies in their edit view)
