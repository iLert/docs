---
description: >-
  Our email outbound integration allows you to send emails for incidents and
  incident updates to any emails address (e.g. to group addresses or people
  outside of iLert).
---

# Email Outbound Integration

We will create an outbound email connection for an alert source.

Navigate to your **Alert sources** and click on the desired alert source where the connection \(outbound integration\) should be created.

![](../.gitbook/assets/screenshot-2020-09-03-at-17.01.54.png)

In the **Incident actions** view, click on **Create incident action** to get to the creation form.

![](../.gitbook/assets/new_incident_action%20%2811%29.png)

In the incident action creation view, choose **Email** as connection type.  
You may now decide if this connection should be triggered **automatically** and select the incident events for which you would like to send emails or select **manually** and turn it into an incident action \(as seen at the end of this document\).

![](../.gitbook/assets/ilert%20%2880%29.png)

Don't forget to give your incident action a **label** and enter a comma separated list of emails _\(one is fine\),_ that should receive the incident actions emails on incident events, in the **send to** field.

The form already prompts you with a **default template** for each email **subject** and email **body**. You may adjust it to your liking and add or exchange additional template variables from iLert listed below.

![](../.gitbook/assets/screenshot-2020-09-03-at-17.06.57.png)

If you chose an automatic incident action, there are no more actions needed, as the next incident event on the specific alert source should trigger your incident action and send emails.

In case you chose manual \(so called incident actions\) you should now see an **action** in the incident context menu for your email incident action on each incident detail view of the selected alert source.

![](../.gitbook/assets/screenshot-2020-09-03-at-17.08.53.png)

