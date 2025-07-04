---
description: >-
  Our email outbound integration allows you to send emails for alerts and alert
  updates to any emails address (e.g. to group addresses or people outside of
  ilert).
---

# Email Outbound Integration

We will create an outbound email connection for an alert source.

Navigate to your **Alert sources** and click on the desired alert source where the connection (outbound integration) should be created.

![](<../../.gitbook/assets/Screenshot 2020-09-03 at 17.01.54.png>)

In the **Alert actions** view, click on **Create alert action** to get to the creation form.

![](<../../.gitbook/assets/new_incident_action (11).png>)

In the alert action creation view, choose **Email** as connection type.\
You may now decide if this connection should be triggered **automatically** and select the alert events for which you would like to send emails or select **manually** and turn it into an alert action (as seen at the end of this document).

![](<../../.gitbook/assets/iLert (79).png>)

Don't forget to give your alert action a **label** and enter a comma separated list of emails _(one is fine),_ that should receive the alert actions emails on alert events, in the **send to** field.

The form already prompts you with a **default template** for each email **subject** and email **body**. You may adjust it to your liking and add or exchange additional template variables from ilert listed below.

![](<../../.gitbook/assets/Screenshot 2020-09-03 at 17.06.57.png>)

If you chose an automatic alert action, there are no more actions needed, as the next alert event on the specific alert source should trigger your alert action and send emails.

In case you chose manual (so called alert actions) you should now see an **action** in the alert context menu for your email alert action on each alert detail view of the selected alert source.

![](<../../.gitbook/assets/Screenshot 2020-09-03 at 17.08.53.png>)

## Related articles

{% content-ref url="../inbound-integrations/email/" %}
[email](../inbound-integrations/email/)
{% endcontent-ref %}
