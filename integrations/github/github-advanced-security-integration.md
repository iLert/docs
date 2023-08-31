---
description: Create alerts in ilert based on code scanning alerts from GitHub.
---

# GitHub Advanced Security Integration

With the ilert GitHub Advanced Security integration, you can create alerts in ilert based on code scans, secret scans and Dependabot scans from GitHub.

## In ilert: Create GitHub alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **GitHub Advanced Security** in the search field, click on the GitHub Advanced Security tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In GitHub <a href="#in-github" id="in-github"></a>

### Create a Repository Webhook

1. Go to your GitHub repository and then to **Settings -> Webhooks** and click on **Add webhook** to add a new webhook (`https://github.com/<org>/<repo>/settings/hooks`)

<figure><img src="../../.gitbook/assets/git-4.png" alt=""><figcaption></figcaption></figure>

2. In the **Payload URL** section, set the **Webhook URL** that you generated in ilert
3. In the **Content type** section, select **application/json**

<figure><img src="../../.gitbook/assets/git-3.png" alt=""><figcaption></figcaption></figure>

4. In the **Which events would you like to trigger this webhook?** section, change it to **Let me select individual events** and select following events: **Check runs**, **Code scanning alerts**, **Dependabot alerts**, **Issues**, **Secret scanning alert locations**, **Secret scanning alerts**.

<figure><img src="../../.gitbook/assets/git-1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/git-2.png" alt=""><figcaption></figcaption></figure>

5. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Github alert get resolved or closed, the alert in ilert will be resolved automatically.

**Can I connect Github with multiple alert sources from ilert?**

Yes, simply create more webhooks in Github.
