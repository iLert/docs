---
description: >-
  Use N-ABLE N-central notification channels and service groups to create alerts
  in ilert.
---

# N-central Integration



In ilert: Create a N-central alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **N-central** in the search field, click on the N-central tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## Configure notifications in N-central

Login to N-ABLE N-central and navigate to the users menu.

![](<../.gitbook/assets/image (43).png>)

Go ahead and click on the **email address** of the user for whose notifications you want to create alerts in ilert for. (We recommend creating a user just for this purpose, however that is not necessary).

In the user's edit view, click on the _**User Details**_ tab and then on the **Notification Method** sub-tab.

![](<../.gitbook/assets/image (44).png>)

Choose **Add** and create a new Third Party I**ntegration - HTTP** notification method.

![](<../.gitbook/assets/image (45).png>)

Give it a proper name and paste the URL that you have copied _**from the new alert source**_ that you have created in ilert from the steps above as **Target URL**.

![](<../.gitbook/assets/image (46) (1).png>)

Click on **Save** to create the new notification method.

Congratulations you have successfully connected N-central with ilert.

## Ensuring that notifications from N-central reach ilert

To make sure that N-central events will reach your ilert alert sources it is important to verify all required assignments of users in N-central.

* is your user part of an **Access Group** that is linked to the **Device**
* is your user assigned as **Primary Notification** of the **Notification Profile** (_Configuration -> Monitoring -> Notifications -> Choose Notification Profile of your choice e.g. Connectivity Failed -> Primary Notification -> Selected Recipients_)

## Acknowledgement and Resolving

To acknowledge and resolve N-central events in ilert you will need to add following notification templates.

1. On the sidebar navigate to **Administration -> Defaults -> Notification Templates**.

{% tabs %}
{% tab title="Acknowledgement" %}
1. Click on **Notification Acknowledgement**.
2. Scroll down to **HTTP MESSAGE TEMPLATE** and enter following template:

```
{{ActiveNotificationTriggerID}}
{{CustomerName}}
{{DeviceName}}
{{DeviceURI}}

{{ExternalCustomerID}}
{{AffectedService}}
{{TaskIdent}}
{{NcentralURI}}
{{QualitativeOldState}}
{{QualitativeNewState}}
{{TimeOfStateChange}}
{{ProbeURI}}
{{QuantitativeNewState()}}
{{ServiceOrganizationName}}
{{TimeOfNotification}}
{{AcknowledgementTime}}
{{AcknowledgementUser}}
{{AcknowledgementNote}}
```

<figure><img src="../.gitbook/assets/2 (3).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Resolving" %}
1. Click on **Return To Normal Notification**.
2. Scroll down to **HTTP MESSAGE TEMPLATE** and enter following template:

```
{{ActiveNotificationTriggerID}}
{{CustomerName}}
{{DeviceName}}
{{DeviceURI}}

{{ExternalCustomerID}}
{{AffectedService}}
{{TaskIdent}}
{{NcentralURI}}
{{QualitativeOldState}}
{{QualitativeNewState}}
{{TimeOfStateChange}}
{{ProbeURI}}
{{QuantitativeNewState()}}
{{ServiceOrganizationName}}
{{TimeOfNotification}}
{{AcknowledgementTime}}
{{AcknowledgementUser}}
{{AcknowledgementNote}}
```

<figure><img src="../.gitbook/assets/3 (3) (1).png" alt=""><figcaption></figcaption></figure>

3. To activate resolving: On the sidebar navigate to **Configuration -> Monitoring -> Notifications**.

<figure><img src="../.gitbook/assets/4 (3).png" alt="" width="281"><figcaption></figcaption></figure>

4. Now select a desired **Notification**.
5. Click on **Trigger Details** and either add or edit a trigger.

<figure><img src="../.gitbook/assets/5 (3).png" alt=""><figcaption></figcaption></figure>

6. Select the **Notify on return to Normal** checkbox and save the trigger.

<figure><img src="../.gitbook/assets/6 (4).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

## FAQ

### I am having issues creating an N-central user

You can find the official documentation [here](https://documentation.n-able.com/N-central/userguide/Content/User\_Management/Role%20Based%20Permissions/role\_based\_permissions\_create\_user.htm)

### I am having issues creating an HTTP notification method for an N-central user

You can find the official documentation [here](https://documentation.n-able.com/N-central/userguide/Content/Further\_Reading/API\_Level\_Integration/API\_Integration\_NotifReg.html)

### How can I test alerts?

If you navigate on to the **devices** overview of your assigned access groups or that are using your notification profile, you may click on one of the devices to edit them and select the specific device's _**service**_ that relates to your Notification Profile, you can edit the check in the **Monitoring tab** and **reverse the check** - this will usually trigger a notification.
