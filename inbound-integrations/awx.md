# Ansible Automation Platform Integration

## In ilert: Create a Ansible Automation Platform alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Ansible Automation Platform** in the search field, click the Ansible Automation Platform tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated. You will need it later.

    <figure><img src="../.gitbook/assets/1-il (1).png" alt=""><figcaption></figcaption></figure>



## In Ansible Automation Platform: Create a Notification Template

1. On the sidebar, click on **Notifications**.

<figure><img src="../.gitbook/assets/1 (14).png" alt="" width="563"><figcaption></figcaption></figure>

2. On the next page, click on **Add**, to add a new notification template.

<figure><img src="../.gitbook/assets/2 (12).png" alt="" width="563"><figcaption></figcaption></figure>

3. Enter a **Name** and change the **Type** to 'Webhook'.

<figure><img src="../.gitbook/assets/3 (11).png" alt="" width="563"><figcaption></figcaption></figure>

4. Scroll down to the **Type Details** and enter the previously created alert source url into the **Target URL** field.
5. Change the **HTTP Method** to 'POST'.

<figure><img src="../.gitbook/assets/4 (10).png" alt="" width="563"><figcaption></figcaption></figure>

6. Optional: You can send a test notification by clicking on the **Test** button.

<figure><img src="../.gitbook/assets/5 (9).png" alt="" width="563"><figcaption></figcaption></figure>

7. Navigate back to your projects and click on on of the desired projects.

<figure><img src="../.gitbook/assets/6 (10).png" alt="" width="563"><figcaption></figcaption></figure>

8. On the navigation bar, click on **Notifications** and enable 'Failure' for the just created nofication template.

<figure><img src="../.gitbook/assets/7 (7).png" alt="" width="563"><figcaption></figcaption></figure>

## FAQ

**Will alerts in ilert be resolved automatically?**

No, unfortunately, Ansible Automation Platform notification template is not compatible with ilert's resolve event.
