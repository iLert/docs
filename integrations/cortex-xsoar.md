---
description: Create ilert alerts directly from Cortex XSOAR (formerly Demisto).
---

# Cortex XSOAR (formerly Demisto) Integration

[Cortex XSOAR](https://www.paloaltonetworks.com/cortex/xsoar) is the industry’s only extended security orchestration, automation and response platform that unifies case management, automation, real-time collaboration and threat intelligence management to transform every stage of the alert lifecycle. Teams can manage alerts across all sources, standardize processes with playbooks, take action on threat intelligence and automate response for any security use case, resulting in significantly faster responses that require less manual review.

## In ilert: Create a Cortex XSOAR alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Cortex XSOAR** in the search field, click on the Cortex XSOAR tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Cortex XSOAR Server: Add Integration <a href="#in-cortex-xsoar" id="in-cortex-xsoar"></a>

1. Go to Cortex XSOAR, then to **Settings -> Integrations**, search for **iLert** integration and click on the **Add instance** button

![](../.gitbook/assets/Settings.png)

2. On the modal window, name the instance, paste the ilert **API Key** that that you generated in ilert and click on the **Save & exit** button

![](<../.gitbook/assets/Settings (1).png>)

3. Type some available ilert command to test the integration, e.g.

```bash
!iLert-submit-event summary="Test alert"
```

![](<../.gitbook/assets/Settings (2).png>)

## FAQ <a href="#faq" id="faq"></a>

**Can I connect Cortex XSOAR with multiple alert sources from ilert?**

Yes, simply add more integration instances in Cortex XSOAR.
