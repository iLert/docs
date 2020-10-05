---
description: >-
  The iLert Sysdig Outbound Integration helps you to easily connect Sysdig with
  iLert.
---

# Sysdig Outbound Integration

## In Sysdig <a id="in-topdesk"></a>

### Copy API token <a id="create-api-user"></a>

2. Go to **Settings**, then to **User Profile.** Write down your API Token. You will need it later in iLert.

![](../../.gitbook/assets/profile_-_settings_-_sysdig.png)

## In iLert <a id="in-ilert"></a>

### Create a Sysdig Connector and Link to alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](../../.gitbook/assets/tpdko7.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/tpdko8.png)

3. Select **Sysdig** as **type** and fill in all fields. Enter a name, the API Token that you copied [in the last step]().

![](../../.gitbook/assets/ilert%20%283%29.png)

4. Go to the alert sources tab and open the alert source whose incidents you want to publish in Sysdig. Click on **Connections** and then on **Add New Connection**.

![](../../.gitbook/assets/tpdko10.png)

5. Select **Sysdig** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the connector name.

![](../../.gitbook/assets/ilert%20%284%29.png)

6. Optional: You can define tags and event filter. More information aber it you can find here: [https://docs.sysdig.com/en/events.html](https://docs.sysdig.com/en/events.html)

7. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test ticket will be published in Sysdig.

![](../../.gitbook/assets/ilert%20%286%29.png)

## FAQ <a id="faq"></a>

**Are updates to an incident published in the Sysdig Ticket?**

Yes, the state of the iLert Incident is reflected in the brief description of the Sysdig event, eg \[RESOLVED\] Host compute.infra is DOWN.

