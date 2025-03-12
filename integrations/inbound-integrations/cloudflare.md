---
description: >-
  The ilert Cloudflare Integration helps you to easily connect ilert with
  Cloudflare.
---

# Cloudflare Integration

Cloudflare allows you to set alert notifications to track DDoS attacks, billing usage and many more.

With ilert Cloudflare Integration, you can receive Cloudflare alert through ilert and easily extend Cloudflare functionality with SMS, push, voice, and ilert on-call schedules.

## In ilert: Create an email alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **email** in the search field, click on the email tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/1 (19).png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an **Integration email** will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/2 (17).png" alt=""><figcaption></figcaption></figure>

## In Cloudflare: Create a notification

1. Go to Cloudflare and then to **Account Home**

![](../../.gitbook/assets/Account___Cloudflare_-_Web_Performance___Security.png)

2. On the next page, click on the **Notifications** tab and then on the **Create** button

![](../../.gitbook/assets/Account___Cloudflare_-_Web_Performance___Security_and_Slack___Chris___iLert.png)

3. On the next page, choose an **Event Type** and then on the **Next** button

![](<../../.gitbook/assets/Account___Cloudflare_-_Web_Performance___Security (1).png>)

4. On the next page, name the notification e.g. ilert, paste the **email** paste that you created in ilert and click on the **Create** button

![](<../../.gitbook/assets/Account___Cloudflare_-_Web_Performance___Security (2).png>)

Finished! Your Cloudflare notifications will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Cloudflare is not sent resolution notifications.

**Can I connect Cloudflare with multiple alert sources from ilert?**

Yes, simply add more notification settings in Cloudflare.
