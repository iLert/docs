---
description: Create alerts in ilert from Checkly checks
---

# Checkly Integration

## In ilert: Create Checkly alert source

1. Go to **Alert sources** and click on the **Create new alert source** button
2. Set a name for your Checkly alert source and select an escalation policy
3.  In the field Integration type select **Checkly** and click **Create**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-06-01 at 19.01.15.png" alt=""><figcaption></figcaption></figure>
4. Skip any advanced settings for now and click **Save** on the next page.
5.  Copy the **Checkly URL**. You will need in the Checkly configuration below.\


    <figure><img src="../.gitbook/assets/Screenshot 2023-06-01 at 17.33.27 (1).png" alt=""><figcaption></figcaption></figure>

## In Checkly: Add ilert alerting channel

1.  Go to **Alerts** and click on **Add more channels**.\


    <figure><img src="../.gitbook/assets/Screenshot 2023-06-01 at 17.59.20.png" alt=""><figcaption></figcaption></figure>
2.  Browse to ilert in the list of channels and click on **Add channel**\


    <figure><img src="../.gitbook/assets/Screenshot 2023-06-01 at 18.00.43.png" alt=""><figcaption></figcaption></figure>
3.  Give the alert channel a name (e.g. ilert) and paste the **Checkly URL** from above in the URL field. Optionally change the notification events. Recovery notifications will resolve existing alerts in ilert that were created from checkly. **Do not edit the payload**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-06-01 at 18.05.49.png" alt=""><figcaption></figcaption></figure>
4. Click **Save ilert webhook**.

## FAQ <a href="#faq" id="faq"></a>

#### **Will alerts in ilert be resolved automatically?**

Yes, as soon as a check in checkly recovers, the associated alert in ilert will be resolved automatically. Make sure that the option **Send alert notifications when a check recovers** is enabled in the alert channel settings in Checkly.&#x20;

#### **Can I link Checkly to multiple alert sources in ilert?**

Yes, create an **alert channel** per alert source in Checkly.

#### **Can I also receive SSL certificate expiration alerts in ilert**

Yes. Simply enable the **Send alert notifications when an SSL certificate is due to expire in x days** in the alert channel settings in Checkly.

