---
description: Create iLert alerts directly from Cortex XSOAR (formerly Demisto).
---

# Cortex XSOAR (formerly Demisto) Integration

[Cortex XSOAR](https://www.paloaltonetworks.com/cortex/xsoar) is the industry’s only extended security orchestration, automation and response platform that unifies case management, automation, real-time collaboration and threat intelligence management to transform every stage of the alert lifecycle. Teams can manage alerts across all sources, standardize processes with playbooks, take action on threat intelligence and automate response for any security use case, resulting in significantly faster responses that require less manual review.

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create an alert source <a href="create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Cortex XSOAR" as the **Integration Type** and click on **Save**.

![](<../.gitbook/assets/iLert (54).png>)

1. On the next page, an **API Key** is generated. You will need this API Key below when setting up the Cortex XSOAR integration.

![](<../.gitbook/assets/iLert (55).png>)

## In Cortex XSOAR Server <a href="in-cortex-xsoar" id="in-cortex-xsoar"></a>

### Add Integration

1. Go to Cortex XSOAR, then to **Settings -> Integrations**, search for **iLert** integration and click on the **Add instance** button

![](../.gitbook/assets/Settings.png)

1. On the modal window, name the instance, paste the iLert **API Key** that that you generated in iLert and click on the **Save & exit** button

![](<../.gitbook/assets/Settings (1).png>)

1. Type some available iLert command to test the integration, e.g.

```bash
!iLert-submit-event summary="Test alert"
```

![](<../.gitbook/assets/Settings (2).png>)

## FAQ <a href="faq" id="faq"></a>

**Can I connect Cortex XSOAR with multiple alert sources from iLert?**

Yes, simply add more integration instances in Cortex XSOAR.
