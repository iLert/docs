---
description: Create alerts in ilert from PandoraFMS alerts.
---

# PandoraFMS Integration

## In ilert: Create a PandoraFMS alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **PandoraFMS** in the search field, click on the PandoraFMS tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In PandoraFMS: Add ilert Webhook as Alert Command

1. Download our script pandorafms\_ilert.sh.\
   Download links:\
   [Pandora FMS modules library](https://pandorafms.com/library/)\
   [ilert Pandorafms](https://github.com/iLert/ilert-pandorafms)
2.  Save this script into the following path :

    ```
    [SERVER_INSTALLATION_PATH]/pandora_server/util/ilert/
    ```
3. In the sidebar, go to **Alerts** -> **Commands** and click on the **Create** button.
4. Enter a **Name** for the command.
5.  In the **Command** field enter: \\

    ```
    sh /usr/share/pandora_server/util/ilert/pandorafms_ilert.sh "_field1_" "_field2_" "_id_alert_" "_field3_" "_field4_" "_timestamp_" "_alert_text_severity_" "_agentname_" "_module_" "_data_"
    ```
6. In the **Description** field enter:\
   `_field1_ : ilert alert source API key.`\
   `_field2_ : Type of the created event. Can be "alert" or "resolved".`\
   `_field3_ : Title of the event.`\
   `_field4_ : Description of the event.`

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 15.40.45.png" alt=""><figcaption></figcaption></figure>

7. Enter following field descriptions:\
   **1 field description**: `ilert API Key (click on the hide checkbox, to keep the Key secure)`\
   \`\`**2 field description**: `Event Type`\
   **2 field values**: `alert,Alert;resolved,Resolved`\
   **3 field description**: `Title`\
   **4 field description**: `Description`

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 15.50.14.png" alt=""><figcaption></figcaption></figure>

8. Save the command by clicking on the **Create** button.
9. In the sidebar, go to **Alerts** -> **Actions** and click on the **Create** button.
10. Enter a **Name** for the action. Select a **Group** and select a the previous made **Command**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.14.04.png" alt=""><figcaption></figcaption></figure>

11. For **ilert API Key** enter the API Key created in ilert on [this step](pandorafms.md#in-ilert-create-pandorafms-alert-source).
12. Depending on the section **Triggering/Recovery** set the **Event Type** to Alert/Resolved
13. Enter a **Title** and a **Description**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.11.36.png" alt=""><figcaption></figcaption></figure>

14. Save the Action by clicking on the **Create** button.
15. In the sidebar, go to **Alerts** -> **Templates** and click on the **Create** button.
16. Enter a **Name** for the Template, assign a **Group** and set a **Priority**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.15.09.png" alt=""><figcaption></figcaption></figure>

17. On the next step, select our created action as **Default action**.
18. Set a **Condition type** and a **Value**(dependent on the type) for the event to get fired.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.15.51 (1).png" alt=""><figcaption></figcaption></figure>

19. &#x20;On the next step, enable **Alert recovery** to activate the automatical alert recovery in ilert.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-22 at 12.39.24.png" alt=""><figcaption></figcaption></figure>

20. &#x20;Create the template.
21. &#x20;In the sidebar, go to **Alerts** -> **List of Alerts** and click on the **Create** button.
22. &#x20;Enter a **Agent**, the **Module**, the previous created **Action**, and the **Template**.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.16.50.png" alt=""><figcaption></figcaption></figure>

23. &#x20;Click on **Add alert** to finish the integration.

<figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.17.15.png" alt=""><figcaption></figcaption></figure>

## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as a module has been recovered, the alert in ilert will be resolved automatically. Make sure to fill out the **Recovery** fields in **Alert Action** and enable **Alert recovery** in **Templates** in [PandoraFMS](pandorafms.md#in-pandorafms-add-ilert-webhook-as-alert-command).
