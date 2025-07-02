---
description: >-
  Deployment events bring your CI & CD pipelines to ilert and enrich your alert
  contexts, reducing MTTR.
---

# Deployment events

You may choose one of your native integrations like GitHub or GitLab or use the generic [API deployment pipeline](../integrations/deployment-integrations/api.md) to generate an `integrationKey` and process your own events.

{% hint style="info" %}
Just like alerts use alert sources to maintain their event configuration, deployment events use deployment pipelines to do the same.
{% endhint %}

While being built for CD, deployment events are not only bound to modern cloud-based software deployments; instead, other sectors and tools might fire relevant deployment events as well, such as:

* Digital Marketing Campaigns (launching campaigns)
* Product Launches in Retail
* Supply Chain Management (transitioning goods)
* Education and E-Learning (courses)
* Regulatory Compliance Releases (financial services or healthcare)
* Content Publishing
* Healthcare Systems (health data)

## In theory

The deployment events view gives you a live overview of all deployments related to your account.

<figure><img src="../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

If a deployment event can be correlated to an alert, ilert will enrich your alert's context with the most relevant deployment information. Allowing you to save precious time when trying to resolve the alert's origin and in the end reducing MTTR.

<figure><img src="../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

## How correlation grows in larger accounts

### Getting started fast: account-wide and time-based

To get you started fast, deployment events support a global account-wide alert mapping, which purely runs on a time-based correlation. If the alert is in a specific window of a deployment it will be mapped in its context.

{% hint style="info" %}
Let's take [GitHub](../integrations/deployment-integrations/github.md) as an example. The fastest way to kick off your integration would be to set up a global GitHub organization webhook sending Releases or Merge events of all repositories to a single GitHub deployment pipeline in ilert. This will immediately start collecting and mapping deployment relations.
{% endhint %}

For ilert customers that are compact enough not to use the [Teams feature](../user-administration/teams.md), this might already do the trick, and no further fine-grained configuration might be needed.

### Scaling in larger organizations: team-based relation claiming

However, for larger or enterprise customers, the global approach might help adopt the feature quickly, but a time-based correlation at a large scale will no longer provide relevant mappings. **Here is where teams can start taking the matter into their own hands** if they wish to receive more relevant deployment mappings for their own resources.

All they need to do is set up their own deployment pipeline that hooks into their own repository events. While making sure that their deployment pipeline is assigned to their team, just like their alert sources and (even more important) escalation policies.

{% hint style="info" %}
If ilert finds a related alert resource, such as an escalation policy or alert source, with a team assignment while also finding at least one deployment pipeline with the same team assignment, it will only correlate deployment events from the specific team-owned deployment pipeline to the alert.
{% endhint %}

By assigning their team to policies and pipelines, a team can individually claim their specific deployment events for their alerts while seamlessly moving away from account-wide deployment events. This allows admins to introduce the feature quickly while still providing teams with the option to migrate to fine-grained correlations on their own—empowering admins and teams and finally reducing MTTR.

## Integrations

Jump into available native integrations or build your own using the generic API:

{% content-ref url="../integrations/deployment-integrations/" %}
[deployment-integrations](../integrations/deployment-integrations/)
{% endcontent-ref %}



