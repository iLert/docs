---
description: Create events in Datadog from ilert alerts.
---

# Datadog Outbound Integration

## In Datadog <a href="#in-topdesk" id="in-topdesk"></a>

### Create an API key <a href="#create-api-user" id="create-api-user"></a>

1. Go to **Integrations**, then click on **APIs**

![](../../.gitbook/assets/datadog\_1.png)

1. In the **New API key** section, enter a name eg. ilert and click on **Create API Key** button

![](../../.gitbook/assets/datadog\_2.png)

1. Write down your API key. You will need it later in ilert.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Datadog Connector and Link to alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](<../../.gitbook/assets/go\_to\_connectors (1).png>)

1. Click on **Add Connector**

![](<../../.gitbook/assets/create\_connector\_button (7) (4).png>)

1. Select **Datadog** as **type** and fill in all fields. Enter a name and the API key that you created [in the last step](outbound.md).

![](../../.gitbook/assets/datadog\_il1.png)

1. Go to the alert sources tab and open the alert source whose alerts you want to publish in Datadog. Click on **Alert actions** and then on **Create alert action**.

![](<../../.gitbook/assets/new\_incident\_action (6).png>)

1. Select **Datadog** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the alert action name.

![](<../../.gitbook/assets/iLert (80).png>)

1. Finished! You can now test the alert action by clicking on the button **Test this alert action**. Then a test ticket will be published in Datadog.

![](<../../.gitbook/assets/iLert (81).png>)

## FAQ <a href="#faq" id="faq"></a>

**Are updates to an alert published in the Datadog?**

Yes, the state of the ilert Alert is reflected in the Datadog events.

**Can I choose which updates to publish to an alert in Datadog?**

Currently not. If you wish, we look forward to your feedback via chat or e-mail.
