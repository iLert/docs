---
description: Create alerts in ilert based on code scanning alerts from GitHub.
---

# GitHub Advanced Security Integration

With the ilert GitHub Advanced Security integration, you can create alerts in ilert based on code scans, secret scans and Dependabot scans from GitHub.

## In ilert: Create GitHub alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "**Alert sources**" tab and click "**Create new alert source**"
2. Type "GitHub" into the search field and select the "GitHub" tile.

<figure><img src="../../.gitbook/assets/github-1.png" alt=""><figcaption></figcaption></figure>

3. Enter a name and click on **Next**

<figure><img src="../../.gitbook/assets/github-2.png" alt=""><figcaption></figcaption></figure>

4. Select your desired escalation policy.

<figure><img src="../../.gitbook/assets/github-3.png" alt=""><figcaption></figcaption></figure>

5. Now choose an Event Type and an Action Type.

<figure><img src="../../.gitbook/assets/github-4.png" alt=""><figcaption></figcaption></figure>

6. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Github.

<figure><img src="../../.gitbook/assets/github-5.png" alt=""><figcaption></figcaption></figure>

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

4. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Github alert get resolved or closed, the alert in ilert will be resolved automatically.

**Can I connect Github with multiple alert sources from ilert?**

Yes, simply create more webhooks in Github.
