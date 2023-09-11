---
description: >-
  The ilert Sysdig Outbound Integration helps you to easily connect Sysdig with
  ilert.
---

# Sysdig Outbound Integration

## In Sysdig <a href="#in-topdesk" id="in-topdesk"></a>

### Copy API token <a href="#create-api-user" id="create-api-user"></a>

1. Go to **Settings**, then to **User Profile.** Write down your API Token. You will need it later in ilert.

![](<../../.gitbook/assets/Profile\_-\_Settings\_-\_Sysdig (1).png>)

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Sysdig Connector and Link to alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](<../../.gitbook/assets/go\_to\_connectors (5).png>)

2. Click on **Add Connector**

![](<../../.gitbook/assets/create\_connector\_button (3).png>)

3. Select **Sysdig** as **type** and fill in all fields. Enter a name, the API Token that you copied in the last step.

![](<../../.gitbook/assets/iLert (5).png>)

4. Go to the alert sources tab and open the alert source whose alerts you want to publish in Sysdig. Click on **Alert actions** and then on **Create alert action**.

![](<../../.gitbook/assets/new\_incident\_action (8).png>)

5. Select **Sysdig** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the alert action name.

![](<../../.gitbook/assets/iLert (67).png>)

6. Optional: You can define tags and event filters. More information about it can be found here: [https://docs.sysdig.com/en/events.html](https://docs.sysdig.com/en/events.html)
7. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test event will be created in Sysdig.

![](<../../.gitbook/assets/iLert (68).png>)

## FAQ <a href="#faq" id="faq"></a>

**Are updates for an alert adapted in the corresponding Sysdig Event?**

Yes, the state of the ilert Alert is reflected in the brief description of the Sysdig event, eg \[RESOLVED] Host compute.infra is DOWN.
