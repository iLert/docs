---
description: >-
  GitHub is a leading CI/CD tool primarily due to its integrated feature, GitHub
  Actions, which allows developers to automate build, test, and deployment
  workflows directly within their repositories.
icon: github
---

# Github deployment pipeline

## Installation types

The ilert Github deployment pipeline offers 2 different modes of installation:

### Through webhooks

The webhook setup can be done without checking in code into repositories. It simply requires a webhook setup either on the repository itself or globally on the Github account level.  The following webhook types are supported to create deployment events in ilert.

* (Commit) Push
* (Branch) Merge (closed + merge)
* Release (published)

### Through Github actions

Using the ilert Github deployment events action: [https://github.com/marketplace/actions/ilert-deployment-events](https://github.com/marketplace/actions/ilert-deployment-events) more advanced users can setup fine tuned use cases e.g. to create the deployment event only on successful rollouts by embedding the action as part of their Github action workflows.

## Setting up

### Creating your deployment pipeline in ilert

In any way a pipeline is required, which will also generate a new `integrationKey` required to route deployment events when they occur. Head to your ilert account and navigate to **Alert sources -> Deployment events**

<figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

Head over to the deployment pipelines tab and click on **Create new pipeline**

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

Provide a name for your pipeline

<figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

**Optional**: And if you are going to manage branch specific deployments, choose the branches in the branch filter section for which you would like to create deployment events in ilert.

<figure><img src="../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

**Optional**: If you would like to use a global webhook flow, where you coordinate specific deployment events for different repositories across multiple pipelines, you can use the event filters to fine tune, which specific event types should create deployment events in ilert and drop other ones. (_This is mainly usefull when using multiple Github account wide webhooks_)

<figure><img src="../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
We generally recommend Release based deployment events, as these are the easiest to setup while providing the most foundated correlations. Note that Push based deployment events can become very spammy, especially when used with Github account wide webhooks.
{% endhint %}

In any way, by clicking on Create you should end up on the detail view of your Github deployment pipeline.

<figure><img src="../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

Providing you with a freshly generated `integrationKey` and the copy & pastable **URL** ready for your webhook setup.

### Creating an account wide Github webhook for your pipeline

Head to your (or your organizations) Github accounts settings page **Home -> Organization/Account -> Settings (top tab) -> Webhooks (left side menu) -> Add webhook**

<figure><img src="../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

Create a new webhook by **pasting the URL** from your freshly created ilert deployment pipeline into the Payload URL field

<figure><img src="../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

Make sure to switch the content type to application/json and choose "Let me select individual events". Scroll down the list and choose whichever suits to your setup of `Pull requests, Pushes and Releases` (_you can also mark all and use the ilert event filter in your pipeline to switch faster in the future_)

<figure><img src="../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

When you are done click on "**Add webhook**" for your webhook to be created. You are now all set and should see deployment events coming into your ilert account.

### Creating a repository based Github webhook for your pipeline

Head to your Github repository and navigate to **Settings (top tab) -> Webhooks (left sidebar) -> Add webhook**

<figure><img src="../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

**Follow the account wide webhook setup above ^**, to configure the webhook.

### Adapting a fine-tuned workflow via Github action

If you wish for more fine-tuned controll on when to trigger deployment events e.g. after successfully finishing your Kubernetes rollout, you can use the official ilert deployment events github action [https://github.com/iLert/ilert-deployment-events-action](https://github.com/iLert/ilert-deployment-events-action) to embed deployment events into your Github action workflows.

#### While automatically mapping to your repo events is an option:

```yaml
on:
  push:
    branches:
      - master
      - main
  pull_request:
    branches:
      - master
      - main
    types:
      - closed

jobs:
  send-ilert-deployment-event:
    runs-on: ubuntu-latest
    name: Sending ilert deployment event
    steps:
      - name: Create a deployment event
        uses: iLert/ilert-deployment-events-action@master
        with:
          integration-key: ${{ secrets.ILERT_DEPLOYMENT_PIPELINE_INTEGRATION_KEY }}
```

#### It also provides an option to create custom deployment events, based on your very own triggered workflow:

```yaml
on:
  push:
    branches:
      - master
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    name: Deploying the application (dummy)
    steps:
      - name: Dummy step
        run: echo "Dummy deployment"

  notification:
    runs-on: ubuntu-latest
    name: Notify ilert
    needs: [deploy]
    if: always()
    steps:
      # make deploy job status available
      # see https://github.com/marketplace/actions/workflow-status-action
      - uses: martialonline/workflow-status@v3
        id: check
      - name: Create a deployment event
        uses: iLert/ilert-deployment-events-action@master
        with:
          integration-key: ${{ secrets.ILERT_DEPLOYMENT_PIPELINE_INTEGRATION_KEY }}
          custom-event: Deployment ${{ steps.check.outputs.status }}
```

Shown in the samples above is how your deployment pipeline's `integrationKey` is provided to the action via Github secrets variable. Which is the recommended way of embedding it into your flow.

