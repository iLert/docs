# Post alerts to a Slack channel

{% hint style="info" %}
**Connect your Slack workspace with ilert first**

Before you proceed, please make sure that a global admin has connected your Slack workspace with your ilert account (as described in our [integration for Slack guide](./))
{% endhint %}

## In Slack: Add alert sources to Slack channels <a href="#in_slack" id="in_slack"></a>

1.  Open Slack and go to a channel to publish ilert alerts. Enter`/ilert` and press Enter:

    ![](../../.gitbook/assets/sl5.png)
2.  A configuration menu appears in which you can add alert sources to the channel.

    ![](../../.gitbook/assets/sl6.png)
3.  Select one or more alert sources from this list

    ![](../../.gitbook/assets/sl7.png)
4. You have now linked an alert source to a Slack Channel.
5. Create a test alert in the alert source in ilert. To do this, click on the link of the alert source in Slack _(New Relic in the example above)_.
6.  A notice appears on the overview page of the alert source actions that alerts from this alert source will be published in Slack.

    ![](<../../.gitbook/assets/iLert (104).png>)
7. Click on **Create Alert** (...) and create a test alert.
8.  A message is now published in the configured channel with the alert information. You can accept the alert within Slack or resolve it.

    ![](../../.gitbook/assets/sl9.png)

## **FAQ**

#### **Are updates to an alert published in Slack?**

Yes, the following updates for an alert are currently being published:

* **Escalations** : An alert is automatically assigned to another user.
* **Manual assignments** : An alert is assigned to someone manually.
* **Actions** : An alert is accepted or corrected.

#### **Can I choose which updates to an alert are published in Slack?**

Yes, you can configure this in the altert source's Alert action settings.

**Can I manage alert sources from private teams using the `/ilert` slash command?**

No, alert sources of private teams can only be added via ilert's web interface, in the alert source's **Alert actions** configuration tab.

#### **Why am I not seeing all of my Slack channels in the Connections UI?**

This could be due to missing permission for private channels. Please try to invite the ilert bot for Slack into the desired (missing) channels and refresh the page.

## &#x20;<a href="#faq" id="faq"></a>
