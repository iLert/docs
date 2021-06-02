---
description: Create incidents in iLert from tickets in Zendesk.
---

# Zendesk Inbound Integration

[Zendesk](https://www.zendesk.com/) is a cloud-based help desk management solution offering customizable tools to build customer service portal, knowledge base and online communities.

## In iLert <a id="create-alert-source"></a>

### Create a Zendesk alert source

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Zendesk" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2886%29.png)

3. On the next page, a **Webhook URL** is generated. You will need this URL below when setting up the Webhook in Zendesk.

![](../../.gitbook/assets/ilert%20%2885%29.png)

## In Zendesk <a id="in-topdesk"></a>

### Create Webhook

1. Go to Zendesk and then to **Settings -&gt; Extensions** and click on the **Add target** button

![](../../.gitbook/assets/a_-_agent.png)

2. On the next page click the **HTTP target** link

![](../../.gitbook/assets/a_-_agent%20%283%29.png)

3. On the next page:

* In the **Title** section, enter a name eg. iLert
* In the **URL** section, paste the **Webhook URL** that you generated in iLert
* In the **Method** section, choose **POST**
* In the **Content type** section, choose **JSON**
* In the bottom section choose **Create target**
* Click the **Submit** button

![](../../.gitbook/assets/a_-_agent%20%282%29.png)

### Create Trigger

1. Go to Zendesk and then to **Business Rules -&gt; Triggers** and click on the **Add trigger** button

![](../../.gitbook/assets/a_-_agent%20%281%29.png)

2. On the next page:

* In the **Trigger name** section, enter a name eg. iLert
* In the **Category** section, choose a category, e.g. Notifications
* In the **Meet ANY of following conditions** section, add **Ticket is created** and **Ticket is updated** rules

![](../../.gitbook/assets/a_-_agent%20%284%29.png)

* Scroll down to the **Actions** panel and choose the **iLert Notify target** that you created above
* In the **JSON body** sections, paste the following  object:

```javascript
{
  "id": "{{ticket.id}}",
  "title": "{{ticket.title}}",
  "description": "{{ticket.description}}",
  "via": "{{ticket.via}}",
  "status": "{{ticket.status}}",
  "priority": "{{ticket.priority}}",
  "requester_name": "{{ticket.requester.name}}",
  "group_name": "{{ticket.group.name}}",
  "assignee_name": "{{ticket.assignee.name}}",
  "account": "{{ticket.account}}",
  "link": "{{ticket.link}}",
  "latest_comment": "{{ticket.latest_comment}}"
}
```

* Click on the **Create** button

![](../../.gitbook/assets/notification_center%20%281%29.png)

## Zendesk Incident Lifecycle

<table>
  <thead>
    <tr>
      <th style="text-align:left">When I create an Zendesk ticket with status...</th>
      <th style="text-align:left">...then an iLert Incident...</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>New </b>or<b> Open</b>
      </td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Pending</b>
      </td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Solved</b> or <b>Closed</b>
      </td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
  </tbody>
</table>



<table>
  <thead>
    <tr>
      <th style="text-align:left">When I update an Zendesk ticket with status...</th>
      <th style="text-align:left">...and the<b> </b>iLert incident...</th>
      <th style="text-align:left">...then the/an iLert Incident...</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>New </b>or<b> Open</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Solved</b> or <b>Closed</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Pending</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>New </b>or<b> Open</b>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">doesn&apos;t change</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Solved</b> or <b>Closed</b>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">change status to <b>Resolved</b> if not already resolved</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Pending</b>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">change status to <b>Accepted</b> if not already accepted</td>
    </tr>
  </tbody>
</table>

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an Zendesk Ticket is completed, the incident in iLert will be resolved automatically.

**Can I connect Zendesk with multiple alert sources from iLert?**

Yes, simply create more Webhooks in Zendesk.

**Can I customize the incident messages?**

No.

