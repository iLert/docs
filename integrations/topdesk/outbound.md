---
description: Create tickets in TOPdesk based on alert events from iLert
---

# TOPdesk Outbound Integration

## In TOPdesk <a href="#in-topdesk" id="in-topdesk"></a>

### Create an API user <a href="#create-api-user" id="create-api-user"></a>

1. Optional: create a dedicated iLert user in TOPdesk. This has the advantage that you can distinguish the TOPdesk tickets created by iLert.
2. Go to **Modules**, then to **Supporting Files**, and click on **Operator**

![](../../.gitbook/assets/tpdko1.png)

1. In the **Surname** section, enter a name eg. iLert
2. In the **Site** section, choose **\[System]**
3. In the **Email** section, enter a email eg. support@ilert.com
4. In the **Login name** section, click on **Edit login data** button

![](../../.gitbook/assets/tpdko2.png)

1. On the modal window, enter **Login Name**, **New Password**, **Repeat password** and click **OK**. Write down your username. You will need it later in iLert.

![](../../.gitbook/assets/tpdko3.png)

1. Click on **Save**
2. Go to **AUTHORIZATION** tab and click on **Links Wizard**

![](../../.gitbook/assets/tpdko4.png)

1. On the modal window, choose **\_API** permission and click on **Link**

![](../../.gitbook/assets/tpdko5.png)

1. On the modal window, ensure that permisson group is linked and click on **OK**

![](../../.gitbook/assets/tpdko6.png)

1. Logout and login with the new `iLert` account
2. Go to **My Settings** and click on **Add** in the **Application passwords** section

![](../../.gitbook/assets/tpdko6.1.png)

1. Enter an **Application name** e.g. `iLert` and ensure that the **Expires on** date is far in the future and click on **Create**&#x20;

![](../../.gitbook/assets/tpdko6.2.png)

1. Write down your password. You will need it later in iLert.

![](../../.gitbook/assets/tpdko6.3.png)

## In iLert <a href="#in-ilert" id="in-ilert"></a>

### Create a TOPdesk Connector and Link to alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](<../../.gitbook/assets/go\_to\_connectors (2).png>)

1. Click on **Add Connector**

![](<../../.gitbook/assets/create\_connector\_button (4).png>)

1. Select **TOPdesk** as **type** and fill in all fields. Enter a name, the URL of your TOPdesk server, username and password of the API user that you created [in the last step](outbound.md).

![](<../../.gitbook/assets/iLert (69).png>)

1. Go to the alert sources tab and open the alert source whose alerts you want to publish in TOPdesk. Click on **Alert actions** and then on **Create alert action**.

![](<../../.gitbook/assets/new\_incident\_action (9).png>)

1. Select **TOPdesk** as the **type**, select the connector created in step 3, fill in all fields. In the **Name** field, specify the alert action name.

![](<../../.gitbook/assets/iLert (70).png>)

1. Finished! You can now test the alert action by clicking on the button **Test this connection**. Then a test ticket will be published in TOPdesk.

![](<../../.gitbook/assets/iLert (71).png>)

## FAQ <a href="#faq" id="faq"></a>

**Are updates to an alert published in the TOPdesk Ticket?**

Yes, the state of the iLert Alert is reflected in the brief description of the TOPdesk ticket, eg \[RESOLVED] Host compute.infra is DOWN.

**Can I choose which updates to publish to an alert in TOPdesk?**

Currently not. If you wish, we look forward to your feedback via chat or e-mail.
