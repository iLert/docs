---
description: >-
  With the ilert Search Guard integration, you can create alerts in ilert based
  on Search Guard alerts.
---

# Search Guard Integration

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Search Guard alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the **Alert sources** tab and click on **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Search Guard" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_22\_47.png)

1. On the next page a **Search Guard URL** is generated. You will need this URL below when setting up the webhook action in Search Guard.

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_22\_48.png)

## In Search Guard <a href="#in-topdesk" id="in-topdesk"></a>

### Create watch <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Search Guard to open the main menu and choose **Search Guard -> Signals**

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_22\_49.png)

1. On the next page click on the **New** button to create a new watch

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_22\_53.png)

1. On the next view name the watch e.g. **My Watch** scroll down and configure the watch to your liking.

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_22\_56.png)

1. Scroll down to **Actions** and add the **Webhook** action

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_23\_00.png)

1. Name the action e.g. **iLert**, paste the **Webhook URL** that you generated in ilert, change headers as required and paste the following **json** as body template

```
{
  "incidentKey": "{{watch.id}}",
  "summary": "SearchGuard alert: {{watch.id}}",
  "details": "Problem occurred at {{execution_time}}",
  "serverUrl": "https://my-server.com"
}
```

![](../.gitbook/assets/Screenshot\_10\_02\_21\_\_23\_06.png)

1.  Click on **Create** to save the watch. &#x20;

    Finished! Your Elastic Search Guard alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Search Guard watch(es) will not fire resolve events for alerts.

**Can I connect Search Guard with multiple alert sources from ilert?**

Yes, simply create more watches in Search Guard.
