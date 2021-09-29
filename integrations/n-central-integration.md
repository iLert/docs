---
description: >-
  Use N-ABLE N-central notification channels and service groups to create
  alerts in iLert.
---

# N-central Integration

## Setup in iLert

Login to your iLert account and navigate to the alert sources list.  
Click on the **Create a new alert source** button

![](../.gitbook/assets/image%20%2843%29.png)

Enter a name for your new alert source and choose an escalation policy.  
In the dropdown for integration type tool search for N-central and select it.

![](../.gitbook/assets/image%20%2841%29.png)

Click on **Save** to create your alert source.

Your newly created N-central alert source will be opened, **copy** the N-central HTTP notification **URL** or click on the small copy icon right next to it.

![](../.gitbook/assets/image%20%2846%29.png)

We will need this URL to setup our N-central notification in the steps below.

## Configure notifications in N-central

Login to N-ABLE N-central and navigate to the users menu.

![](../.gitbook/assets/image%20%2844%29.png)

Go ahead and click on the **email address** of the user for whose notifications you want to create alerts in iLert for. \(We recommend creating a user just for this purpose, however that is not necessary\).

In the user's edit view, click on the _**User Details**_ tab and then on the **Notification Method** sub-tab.

![](../.gitbook/assets/image%20%2847%29.png)

Choose **Add** and create a new Third Party I**ntegration - HTTP** notification method.

![](../.gitbook/assets/image%20%2842%29.png)

Give it a proper name and paste the URL that you have copied _**from the new alert source**_ that you have created in iLert from the steps above as **Target URL**.

![](../.gitbook/assets/image%20%2845%29.png)

Click on **Save** to create the new notification method.

Congratulations you have successfully connected N-central with iLert.

## Ensuring that notifications from N-central reach iLert

To make sure that N-central events will reach your iLert alert sources it is important to verify all required assignments of users in N-central.

* is your user part of an **Access Group** that is linked to the **Device**
* is your user assigned as **Primary Notification** of the **Notification Profile** \(_Configuration -&gt; Monitoring -&gt; Notifications -&gt; Choose Notification Profile of your choice e.g. Connectivity Failed -&gt; Primary Notification -&gt; Selected Recipients_\)

## FAQ

### I am having issues creating an N-central user

You can find the official documentation [here](https://documentation.n-able.com/N-central/userguide/Content/User_Management/Role%20Based%20Permissions/role_based_permissions_create_user.htm)

### I am having issues creating an HTTP notification method for an N-central user

You can find the official documentation [here](https://documentation.n-able.com/N-central/userguide/Content/Further_Reading/API_Level_Integration/API_Integration_NotifReg.html)

### How can I test alerts?

If you navigate on to the **devices** overview of your assigned access groups or that are using your notification profile, you may click on one of the devices to edit them and select the specific device's _**service**_ that relates to your Notification Profile, you can edit the check in the **Monitoring tab** and **reverse the check** - this will usually trigger a notification.

