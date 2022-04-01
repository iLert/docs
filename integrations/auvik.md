---
description: >-
  Auvik is an easy-to-use cloud-based networking management and monitoring
  software, the iLert integration offers two-way alert syncing.
---

# Auvik Integration

## In iLert: Create an Auvik alert source

1. Navigate to **Services** -> **Alert sources** and click on _Create new alert source_
2. Assign a name and select an escalation policy
3. From the tools dropdown choose **Auvik**

![](<../.gitbook/assets/image (54) (1).png>)

4\. If you wish to setup a bidirectional (two-way-sync) alert flow where Auvik alerts are resolved as soon as incidents in iLert are resolved, please check the **bidirectional checkbox** and fill in your Auvik API user credentials

![](<../.gitbook/assets/image (53) (1) (1) (1) (1) (1).png>)

If you need more guidance on how to retrieve an Auvik API key check out [this guide](https://support.auvik.com/hc/en-us/articles/204309114#topic\_regenerate)

5\. Click on **Save** to create your alert source, after you have been redirected you should see your alert source setup. Copy the **Auvik URL** as we will need it later in Auvik to setup the integration.

![](<../.gitbook/assets/image (48) (1) (1) (1).png>)

## In Auvik

### Configuring the integration

1. Navigate to **Integrations** and click on **Add integration**

![](<../.gitbook/assets/image (49) (1).png>)

&#x20;2\. From the dropdown choose **iLert**

3\. A popup will appear; enter a name and paste your **Auvik URL** that you have copied from your alert source in iLert

![](<../.gitbook/assets/image (47) (1) (1).png>)

4\. You may choose to click on Test Connection to see if it is setup correctly, afterwards click **Save** to create your integration in Auvik.

### Setting up a notification channel

1. Navigate to **Manage Alerts** -> **Notification Channels**

![](<../.gitbook/assets/image (52) (1) (1) (1) (1).png>)

2\. Click on **Add Notification Channel**; a popup will appear

3\. Choose a name and from the **Contact method** dropdown choose **iLert**

4\. Then select your freshly created iLert Integration and click on **Save**

### Syncing alerts

1. Navigate to **Manage Alert** -> **Alerts**

&#x20;

![](<../.gitbook/assets/image (50) (1) (1) (1).png>)

2\. Pick a desired alert that you want to sync to iLert, mark it and click on **Edit**

3\. In the Edit popup enable the **Notification channels** and choose your freshly created notification channel in the drop down, click on **Save** to assign it with your alert

![](<../.gitbook/assets/image (47) (1) (1) (1).png>)

4\. You are done, your alerts should sync from **Auvik** into iLert

## FAQ



### Will cleared Auvik alerts resolve iLert alerts?

Yes.

### Will resolved iLert alerts clear Auvik alerts?

Yes, if a bidirectional setup has been configured in iLert.

### Can there be multiple iLert Auvik alert sources?

Yes. You may create as many Auvik alert sources as you like and link them to different Auvik notification channels. This can be used to have different priorities as well as support hours and different escalation policies in iLert for specific alerts in Auvik.

