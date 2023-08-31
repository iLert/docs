---
description: >-
  The ilert Cloudflare Integration helps you to easily connect ilert with
  Cloudflare.
---

# Cloudflare Integration

Cloudflare allows you to set alert notifications to track DDoS attacks, billing usage and many more.

With ilert Cloudflare Integration, you can receive Cloudflare alert through ilert and easily extend Cloudflare functionality with SMS, push, voice, and ilert on-call schedules.

## In ilert <a href="#create-alarm-source" id="create-alarm-source"></a>

### Create an email alert source

1. Go to **Alert sources** and click on **Add a new alert source**
2. Enter a name and select an escalation policy
3. Chose **Email** as integation type
4. Enter an email address for the alert source, you will need this email below when setting up the notification in Cloudflare
5. Save the email alert source

![](<../.gitbook/assets/Screenshot 2020-06-18 at 16.21.49.png>)

## In Cloudflare

### Create a notification

1. Go to Cloudflare and then to **Account Home**

![](../.gitbook/assets/Account\_\_\_Cloudflare\_-\_Web\_Performance\_\_\_Security.png)

2. On the next page, click on the **Notifications** tab and then on the **Create** button

![](../.gitbook/assets/Account\_\_\_Cloudflare\_-\_Web\_Performance\_\_\_Security\_and\_Slack\_\_\_Chris\_\_\_iLert.png)

3. On the next page, choose an **Event Type** and then on the **Next** button

![](<../.gitbook/assets/Account\_\_\_Cloudflare\_-\_Web\_Performance\_\_\_Security (1).png>)

4. On the next page, name the notification e.g. ilert, paste the **email** paste that you created in ilert and click on the **Create** button

![](<../.gitbook/assets/Account\_\_\_Cloudflare\_-\_Web\_Performance\_\_\_Security (2).png>)

Finished! Your Cloudflare notifications will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately Cloudflare is not sent resolution notifications.

**Can I connect Cloudflare with multiple alert sources from ilert?**

Yes, simply add more notification settings in Cloudflare.
