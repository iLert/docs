---
description: >-
  GitLab is a complete DevSecOps platform that streamlines collaboration and
  simplifies CI/CD, enabling teams to plan, develop, and deploy software in a
  single application
icon: gitlab
---

# GitLab deployment pipeline

GitLab is a complete DevSecOps platform that enables teams to collaborate on planning, development, CI/CD, and deployment in a single application. Display your GitLab deployment pipelines in the ilert and enrich alerts context. This integration helps you better understand the context of incidents and improves your MTTR.

## Setting up

### Creating your deployment pipeline in ilert

In any way, a pipeline is required, which will also generate a new `integrationKey` required to route deployment events when they occur. Head to your ilert account and navigate to **Alert sources -> Deployment events.**

<figure><img src="../.gitbook/assets/1 (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Head over to the deployment pipelines tab and click on **Create new pipeline.**

<figure><img src="../.gitbook/assets/2 (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Provide a name for your pipeline.

<figure><img src="../.gitbook/assets/3 (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Optional**: If you are going to manage branch-specific deployments, choose the branches in the branch filter section for which you would like to create deployment events in ilert.

<figure><img src="../.gitbook/assets/4 (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

**Optional**: If you would like to use a global webhook flow, where you coordinate specific deployment events for different repositories across multiple pipelines, you can use the event filters to fine-tune which specific event types should create deployment events in ilert and drop other ones. (_This is mainly useful when using multiple GitLab account-wide webhooks_).

<figure><img src="../.gitbook/assets/5 (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
We generally recommend Release-based deployment events, as these are the easiest to set up and provide the most foundated correlations. Note that Push-based deployment events can become very spammy, especially when used with Github account-wide webhooks.
{% endhint %}

In any way, by clicking on Create, you should end up on the detail view of your GitLab deployment pipeline.

<figure><img src="../.gitbook/assets/6 (1) (1).png" alt=""><figcaption></figcaption></figure>

Providing you with a freshly generated `integrationKey` and copy & pastable **URL** ready for your webhook setup.

### Creating an account-wide GitLab webhook for your pipeline

Head to your (or your organization's) GitLab groups settings page **Home -> Groups -> Settings (left sidebar) -> Webhooks -> Add webhook.**

<figure><img src="../.gitbook/assets/7 (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/8.png" alt=""><figcaption></figcaption></figure>

Create a new webhook by **pasting the URL** from your freshly created ilert deployment pipeline into the URL field.

<figure><img src="../.gitbook/assets/9 (1).png" alt=""><figcaption></figcaption></figure>

Scroll down the list and choose whichever suits your setup of `Push events, Merge request events and Releases events` (_you can also mark all and use the ilert event filter in your pipeline to switch faster in the future_).

<figure><img src="../.gitbook/assets/10-1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/10-2..png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/10-3.png" alt=""><figcaption></figcaption></figure>

When you are done, click "**Add webhook**" for your webhook to be created. You are now all set and should see deployment events coming into your ilert account.
