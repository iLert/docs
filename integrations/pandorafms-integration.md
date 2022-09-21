---
description: Create alerts in iLert from Grafana alerts.
---

# PandoraFMS Integration

## In iLert: Create PandoraFMS alert source

1. Go to **Alert sources** and click on the **Create new alert source** button
2. Set a name for your PandoraFMS alert source and select an escalation policy
3. In the field Integration type select **PandoraFMS** and save.
4. On the next page, an API Key is generated. You will need this API Key below when setting up in PandoraFMS.

## In PandoraFMS: Add iLert Webhook as Alert Command

1. Download our script pandorafms\_ilert.sh from the [Pandora FMS modules library](https://pandorafms.com/library/).
2.  Save this script into the following path :

    ```
    [SERVER_INSTALLATION_PATH]/pandora_server/util/ilert/
    ```
3. In the sidebar, go to **Alerts** -> **Commands** and click on the **Create** button.
4. Enter a **Name** for the command.
5.  In the **Command** field enter: \


    ```
    sh /usr/share/pandora_server/util/ilert/pandorafms_ilert.sh "_field1_" "_field2_" "_id_alert_" "_field3_" "_field4_" "_timestamp_" "_alert_text_severity_" "_agentname_" "_module_" "_data_"
    ```


6. In the **Description** field enter: \
   `_field1_ : iLert alert source API key.`\
   `_field2_ : Type of the created event. Can be "alert" or "resolved".`\
   `_field3_ : Title of the event.`\
   `_field4_ : Description of the event.`
7.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 15.40.45.png" alt=""><figcaption></figcaption></figure>
8. Enter following field descriptions:\
   **1 field description**: `iLert API Key (click on the hide checkbox, to keep the Key secure)`\
   ``**2 field description**: `Event Type`\
   **2 field values**:          `alert,Alert;resolved,Resolved`\
   **3 field description**: `Title`\
   **4 field description**: `Description`
9.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 15.50.14.png" alt=""><figcaption></figcaption></figure>
10. Save the command by clicking on the **Create** button.
11. In the sidebar, go to **Alerts** -> **Actions** and click on the **Create** button.
12. Enter a **Name** for the action. Select a **Group** and select a the previous made **Command**.
13.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.14.04.png" alt=""><figcaption></figcaption></figure>
14. For **iLert API Key** enter the API Key created in iLert on [this step](pandorafms-integration.md#in-ilert-create-pandorafms-alert-source).
15. Depending on the section **Triggering/Recovery** set the **Event Type** to Alert/Resolved
16. Enter a **Title** and a **Description**.
17.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.11.36.png" alt=""><figcaption></figcaption></figure>
18. Save the Action by clicking on the **Create** button.
19. In the sidebar, go to **Alerts** -> **Templates** and click on the **Create** button.
20. Enter a **Name** for the Template, assign a **Group** and set a **Priority**.
21.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.15.09.png" alt=""><figcaption></figcaption></figure>
22. On the next step, select our created action as **Default action**.
23. Set a **Condition type** and a **Value**(dependent on the type) for the event to get fired.
24.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.15.51.png" alt=""><figcaption></figcaption></figure>
25. Create the template.
26. In the sidebar, go to **Alerts** -> **List of Alerts** and click on the **Create** button.
27. Enter a **Agent**, the **Module**, the previous created **Action**, and the **Template**.
28.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.16.50.png" alt=""><figcaption></figcaption></figure>
29. Click on **Add alert** to finish the integration.
30.

    <figure><img src="../.gitbook/assets/Screenshot 2022-09-19 at 16.17.15.png" alt=""><figcaption></figcaption></figure>
