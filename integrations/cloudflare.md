---
description: >-
  The iLert Cloudflare Integration helps you to easily connect iLert with
  Cloudflare.
---

# Cloudflare Integration

Cloudflare allows you to set alert notifications to track DDoS attacks, billing usage and many more.

With iLert Cloudflare Integration, you can receive Cloudflare alert through iLert and easily extend Cloudflare functionality with SMS, push, voice, and iLert on-call schedules.

## In iLert <a href="#create-alarm-source" id="create-alarm-source"></a>

### Create an email alert source

1. Go to **Alert sources** and click on **Add a new alert source**
2. Enter a name and select an escalation policy
3. Chose **Email** as integation type
4. Enter an email address for the alert source, you will need this email below when setting up the notification in Cloudflare
5. Save the email alert source

![](../.gitbook/assets/screenshot-2020-06-18-at-16.21.49.png)

## In Cloudflare

### Create a notification

1. Go to Cloudflare and then to **Account Home**

![](<../.gitbook/assets/account\_\_\_cloudflare\_-\_web\_performance\_\_\_security (1).png>)

1. On the next page,  click on the **Notifications** tab and then on the **Create** button

![](../.gitbook/assets/account\_\_\_cloudflare\_-\_web\_performance\_\_\_security\_and\_slack\_\_\_chris\_\_\_ilert.png)

1. On the next page,  choose an **Event Type** and then on the **Next** button

![](../.gitbook/assets/account\_\_\_cloudflare\_-\_web\_performance\_\_\_security.png)

1. On the next page,  name the notification e.g. iLert, paste the **email** paste that you created in iLert and click on the **Create** button

![](<../.gitbook/assets/account\_\_\_cloudflare\_-\_web\_performance\_\_\_security (2).png>)

Finished! Your Cloudflare notifications will now create alerts in iLert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

No, unfortunately Cloudflare is not sent resolution notifications.

**Can I connect Cloudflare with multiple alert sources from iLert?**

Yes, simply add more notification settings in Cloudflare.
