---
description: >-
  HaloITSM is an IT service management solution designed to streamline IT
  support processes and operations through ticketing, asset management, and
  workflow automation.
---

# HaloITSM Integration

This integration enables you to connect ilert and HaloITSM easily and receive critical HaloITSM alerts via push, SMS, and voice notifications.&#x20;

## In ilert: Create a HaloITSM alert source&#x20;

1.  Go to **Alert sources** --> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **HaloITSM** in the search field, click the HaloITSM tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated. You will need it later.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In HaloITSM: Create a Custom Webhook integration

1. On the sidebar, click **Configuration**.

<figure><img src="../../.gitbook/assets/1 (18).png" alt="" width="342"><figcaption></figcaption></figure>

2. In the **search bar** enter "Custom integrations" and select **Custom integrations** from the results.

<figure><img src="../../.gitbook/assets/2 (18).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/3 (14).png" alt="" width="563"><figcaption></figcaption></figure>

3. Click **New**.

<figure><img src="../../.gitbook/assets/4 (12).png" alt="" width="563"><figcaption></figcaption></figure>

4. Enter a Name and the following Base URL `https://api.ilert.com/`.

<figure><img src="../../.gitbook/assets/5 (11).png" alt="" width="563"><figcaption></figcaption></figure>

5. Save the custom integration.
6. Now, click **Methods**.

<figure><img src="../../.gitbook/assets/6 (11).png" alt="" width="563"><figcaption></figcaption></figure>

7. Then, click **New**.

<figure><img src="../../.gitbook/assets/7 (8).png" alt="" width="563"><figcaption></figcaption></figure>

8. Enter a **Name**.
9. Change the **Method** to POST and enter the previously created URL path into the field.

<figure><img src="../../.gitbook/assets/8 (4).png" alt="" width="563"><figcaption></figcaption></figure>

10. Click **Body** and choose **JSON**.

<figure><img src="../../.gitbook/assets/9 (5).png" alt="" width="563"><figcaption></figcaption></figure>

11. Add the following payload to the body.

{% tabs %}
{% tab title="Recommended payload" %}
```
{
    "ticket" : {
        "status" : {
            "id" : <<ticket^status^id>>,
            "name" : <<ticket^status^name>>,
            "shortname" : <<ticket^status^shortname>>
        },
        "id" : <<ticket^id>>,
        "summary" : <<ticket^summary>>,
        "details" : <<ticket^details>>,
        "dateoccurred" : <<ticket^dateoccurred>>,
        "dateclosed" : <<ticket^dateclosed>>,
        "tickettype" : {
            "id" : <<ticket^tickettype^id>>,
            "name" :  <<ticket^tickettype^name>>
        },
        "priority" : {
            "id" : <<ticket^priority_id>>,
            "name" : <<ticket^priority^name>>
        },
        "client_id" : <<ticket^client_id>>,
        "client_name" : <<ticket^client_name>>,
        "site_id" : <<ticket^site_id>>,
        "site_name" : <<ticket^site_name>>,
        "team" : <<ticket^team>>,
        "agent" : {
            "id" : <<ticket^agent^id>>,
            "name" : <<ticket^agent^name>>
        },
        "organisation_id" : <<ticket^organisation_id>>,
        "department_id" : <<ticket^department_id>>,
        "workflow_name" : <<ticket^workflow_name>>,
        "oppcompanyname" : <<ticket^oppcompanyname>>
    }
}
```
{% endtab %}

{% tab title="Full payload" %}
```
{
    "ticket" : <<ticket>>
}
```
{% endtab %}
{% endtabs %}

12. In the next step add a new Runbook.

<figure><img src="../../.gitbook/assets/10 (2).png" alt="" width="563"><figcaption></figcaption></figure>

13. Enter a name for your newly created Runbook.

<figure><img src="../../.gitbook/assets/11 (1).png" alt="" width="563"><figcaption></figcaption></figure>

14. Add the following Events for the Runbook: "New Ticket Logged" and "Ticket Status Changed".

<div><figure><img src="../../.gitbook/assets/13 (1).png" alt="" width="375"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/14 (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

15. Now click **Flow Chart** and **Edit**.

<figure><img src="../../.gitbook/assets/15.png" alt="" width="563"><figcaption></figcaption></figure>

16. Enter a **Step Name**.
17. Change the Type to Action. Choose the **Action type** "Execute an Integration Method" and **Method** "ilert integration: send ticket to ilert" (previously created method).
18. Save the Step.

<figure><img src="../../.gitbook/assets/16.png" alt="" width="563"><figcaption></figcaption></figure>

19. Edit the other two steps.

<div><figure><img src="../../.gitbook/assets/17.png" alt="" width="375"><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/18.png" alt="" width="375"><figcaption></figcaption></figure></div>

20. &#x20;Save the Runbook.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, HaloITSM will resolve the ilert alert once the ticket is closed or resolved.
