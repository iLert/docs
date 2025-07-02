---
description: >-
  Hyperping is a monitoring tool that helps users track the uptime and
  performance of their websites and web applications
---

# Hyperping Integration

[Hyperping](https://hyperping.com/) is a monitoring tool that helps users track the uptime and performance of their websites and web applications by providing uptime checks, performance metrics, and incident alerts. Integrating Hyperping with ilert allows for centralized incident management, automated alerting, and improved response times, ensuring that teams can quickly address performance issues and maintain high service reliability.

## In ilert: Create a Hyperping alert source

1.  Go to **Alert sources** -> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Hyperping** in the search field, click on the Hyperping tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Hyperping: Configuring your project settings

![](<../../.gitbook/assets/image (60) (2).png>)

Login to your Hyperping account and navigate to **Project Settings**. Paste your alert source's **url** that we just copied in the step before into the webhook field. You may try and test your configuration using the provided **Down test** and **Up test** buttons.

\
Dont forget to click on **Save** to save your project setup.
