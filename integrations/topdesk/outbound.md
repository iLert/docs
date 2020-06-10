---
title: TOPdesk Outbound Integration
seoTitle: 'iLert: TOPdesk Outbound Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert TOPdesk Outbound Integration helps you to easily connect TOPdesk
  with iLert.
date: '2020-04-29T05:02:05.000Z'
weight: 1
---

# TOPdesk Outbound Integration

## In TOPdesk <a id="in-topdesk"></a>

### Create an API user <a id="create-api-user"></a>

1. Optional: create a dedicated iLert user in TOPdesk. This has the advantage that you can distinguish the TOPdesk tickets created by iLert.
2. Go to **Modules**, then to **Supporting Files**, and click on **Operator**
3. In the **Surname** section, enter a name eg. iLert
4. In the **Site** section,  choose **\[System\]**
5. In the **Email** section, enter a email eg. support@ilert.com
6. In the **Login name** section, click on **Edit login data** button
7. On the modal window, enter **Login Name**, **New Password**, **Repeat password** and click **OK**. Write down your username. You will need it later in iLert.
8. Click on **Save**
9. Go to **AUTHORIZATION** tab and click on **Links Wizard**
10. On the modal window, choose **\_API** permission and click on **Link**
11. On the modal window, ensure that permisson group is linked and click on **OK**
12. Logout and login with the new `iLert` account
13. Go to **My Settings** and click on **Add** in the **Application passwords** section
14. Enter an **Application name** e.g. `iLert` and ensure that the **Expires on** date is far in the future and click on **Create** 
15. Write down your password. You will need it later in iLert.

## In iLert <a id="in-ilert"></a>

### Create a TOPdesk Connector and Link to alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button
2. Click on **Add Connector**
3. Select **TOPdesk** as **type** and fill in all fields. Enter a name, the URL of your TOPdesk server, username and password of the API user that you created [in the last step]().
4. Go to the alert sources tab and open the alert source whose incidents you want to publish in TOPdesk. Click on **Connections** and then on **Add New Connection**.
5. Select **TOPdesk** as the **type**, select the connector created in step 3, fill in all fields. In the **Name** field, specify the connector name.
6. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test ticket will be published in TOPdesk.

## FAQ <a id="faq"></a>

**Are updates to an incident published in the TOPdesk Ticket?**

Yes, the state of the iLert Incident is reflected in the brief description of the TOPdesk ticket, eg \[RESOLVED\] Host compute.infra is DOWN.

**Can I choose which updates to publish to an incident in TOPdesk?**

Currently not. If you wish, we look forward to your feedback via chat or e-mail.

