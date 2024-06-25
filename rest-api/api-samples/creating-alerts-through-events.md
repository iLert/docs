# Creating alerts through events

Besides offering the possibility to integrate custom tools via the API alert source, ilert also offers the option to directly create alerts via the events API. The API endpoint allows you to not only create, but also accept and resolve alerts.&#x20;

More information on this can be found in the [API reference](https://api.ilert.com/api-docs/#tag/events/post/events).

### Using the events API to create an alert:

Send a **POST** request to&#x20;

```
https://api.ilert.com/api/events
```

```json
{
  "apiKey": "il...", // api key of the alert source
  "eventType": "ALERT", // ALERT for create, ACCEPT or RESOLVE
  "summary": "",
  "details": "",
  "alertKey": "", // used to group events together
  "priority": "HIGH", // HIGH (with escalation), LOW (no escalation)
  "routingKey": "" // overwrite escalation policy for ALERT events
}
```

{% hint style="danger" %}
Note that the field `apiKey` does not refer to an authentication token for the ilert API itself but instead to the API key of the desired alert source. The API key can be found in the detail view of the alert source.
{% endhint %}

Visit the web UI or the mobile app (under Alerts) to confirm your event created a corresponding alert.

### FAQ

**Which priority will my alert be created with?**

By default, the priority set in the alert source will be considered as the default priority. \
However, the priority can be overridden by the event, if one of the following conditions are met:

* Integration type of the alert source is **Grafana** or **ServiceNow**
* Custom priority template is configured in alert source
* Default priority of alert source is set to **HIGH**
