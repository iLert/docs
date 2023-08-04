---
description: Create alerts in ilert from PRTG notifications.
---

# PRTG Network Monitor Integration

PRTG Network Monitor is a robust network monitoring software developed by the German company Paessler AG. It allows system administrators and other IT professionals to manage and monitor their entire IT infrastructure, including servers, routers, switches, bandwidth usage, and more. With PRTG integration, you can easily integrate PRTG with ilert and extend your existing PRTG monitoring with SMS, push and voice notifications as well as on-call schedules from ilert.

## In ilert: Create PRTG alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Add a new alert source**
2. Enter a name for your alert source (e.g. "PRTG") and select your desired escalation policy.
3. In the Integration Type field, select **PRTG Network Monitor** and click on Save.

<figure><img src="../.gitbook/assets/Screenshot 2023-03-28 at 18.59.49 (1).png" alt=""><figcaption></figcaption></figure>

4. Open the alert source details view by navigating to **Alert sources -->Alert sources** and clicking in the alert source that you have created. In the alert source details view, the fields **PRTG URL** and **PRTG Postdata** will be displayed. You will need those two fields in the PRTG setup below.

<figure><img src="../.gitbook/assets/Screenshot 2023-03-28 at 19.13.16.png" alt=""><figcaption></figcaption></figure>

## In PRTG: Create new notification <a href="#create-notification" id="create-notification"></a>

1.  Got to **Setup** --> **Account Settings** --> **Notification Templates**\


    <figure><img src="../.gitbook/assets/Screenshot 2023-03-29 at 17.43.55.png" alt=""><figcaption></figcaption></figure>
2. Click on **Add Notification Template**&#x20;
3. As notification method select **Execute HTTP ACTION**
4.  Copy the **URL** and **Postdata** fields from the ilert alert source above and paste them in **URL** and **Payload** fields of the HTTP Action.\
    \


    <figure><img src="../.gitbook/assets/Screenshot 2023-03-29 at 17.58.10.png" alt=""><figcaption></figcaption></figure>
5. Click on **Create**
6.  Next, we will use the ilert notification template in PRTG. To do this, switch to the **Root** group in the device overview and select the **Notification Triggers** tab.



    <figure><img src="../.gitbook/assets/Screenshot 2023-03-29 at 18.05.37.png" alt=""><figcaption></figcaption></figure>
7.  Create the following **Notification Triggers**. Note: We recommend to make use of the option **repeat every x minutes** in case your internet connection goes down.

    <figure><img src="../.gitbook/assets/Screenshot 2023-03-29 at 21.51.48.png" alt=""><figcaption></figcaption></figure>

    \
    You may adjust the trigger to fit your needs, e.g. adjust the time that PRTG waits before it sends a notification to ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the condition of a sensor in PRTG is OK again, the associated alert is resolved in ilert.

**What if an alert is acknowledged in PRTG, is the associated alert also acknowledged in ilert?**

No, in PRTG it is unfortunately not possible to send notifications for acknowledgements.

**What if my internet connection is interrupted? Are the events generated in PRTG lost?**

No, events will not be lost if you enable the "repeat every x minutes" option in PRTG (see above). In addition, we recommend that you monitor your Internet connection with ilert's [heartbeat monitoring](../alerting/heartbeat-monitoring/).

**Can I link PRTG to multiple alert sources in ilert?**

Yes, create multiple ilert notifications in PRTG. You can then associate them with objects in the PRTG object hierarchy.

**The integration does not work. How do I find the issue?**

If you can not find the error, please contact our support at [support@ilert.com](https://github.com/iLert/docs/tree/dfe03283a452516a115a55f8c20942698e279d7b/integrations/support@ilert.com).
