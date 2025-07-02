# Using ilert AI for post-mortem creation

## Understanding the alert -> incident transition and what to do after the dust has settled

As a technical issue transitions from an alert into an incident because it has an effect on business services. Its disruption and impact might make it necessary to revisit what happened and which steps can be taken to prevent a similar issue from reoccurring in the future. Assume following sample incident that has reached its resolved state.

<figure><img src="../.gitbook/assets/image (215).png" alt="" width="375"><figcaption><p>A simple example incident that has reached the end of its lifecycle in the RESOLVED state</p></figcaption></figure>

## When the dust settles

As customers have been notified, the root cause identified and a potential fix in place, the dust and hectic has settled around the incident. Now it is time to sit back and think about what caused the issue in the first place and if/how such things can be prevented in the future.

Usually someone in the team responsible for the services that were impacted by the incident will now start working on gathering all information around the incident and set up a document with all details that is discussed afterwards. This can be quite cumbersome and ilert AI is here to help reduce the time it takes to get started with a proper doc significantly.

### Using ilert AI to generate a postmortem doc

<figure><img src="../.gitbook/assets/image (216).png" alt="" width="563"><figcaption></figcaption></figure>

If ilert AI is enabled, you will find the option to generate a postmortem in the detail view of the incident.

This will open a popup that offers multiple options to fine tune your postmortem document generation.

<figure><img src="../.gitbook/assets/image (217).png" alt="" width="375"><figcaption></figcaption></figure>

### By default (no selections)

By default the generation will take all available context of the incident into account, such as history updates, subscribers, services and involved users / responders.

### Include alerts

If an alert is linked to the incident, the alerts details will also be taken into account, as well as its timeline. This can help to significantly improve the generation of technical related action items in the final document. You can also link alerts afterwards, as long as they are not resolved yet.

### Including alert related Slack or MS Teams channels

When an alert is linked that has an attached **#warroom** Slack channel or MS Teams channel the channel will also appear in the selection options of the popup. Channels that are included will be scanned and parsed by the connected ilert Slack or MS Teams bot and relevant messages will be included automatically in content of the final document.

It is also possible to paste a chat transcript from any other source manually, this script may contain timestamps and usernames in any raw format, ilert AI will automatically parse and handle the content accordingly.

### Optional fine-tuning

You have three additional fields to provide optional content for fine-tuning of the postmortem document. The content here has a little higher weight in such that during the generation it can help shape action items or root cause. This is helpful if certain action items or root cause information are already known at the time of postmortem generation and you wish to include them.

## Postmortem creation

When you are satisfied with the postmortem input you can click on **Generate post mortem** to enqueue your postmortem creation. As certain sources are pulled, paginated, read and parsed during the creation process it has been decoupled and can take a little moment.

<figure><img src="../.gitbook/assets/image (218).png" alt="" width="275"><figcaption></figcaption></figure>

As soon as your document is ready, the status will transition to **created**.

You may now click on **View generated content** to see a simplified markdown rendered version of the generated content:

<figure><img src="../.gitbook/assets/image (219).png" alt="" width="265"><figcaption></figcaption></figure>

For our sample alert the generated markdown version looks like this:

<figure><img src="../.gitbook/assets/image (220).png" alt="" width="375"><figcaption></figcaption></figure>

At the bottom right you will find the **Open** option which will contain a link to the raw text file document of your generated postmortem. You will probably want to move this raw version of the document into a shared MS Word or Google Doc for further manual fine-tuning and adjustments before sharing it with colleagues.

## Publishing a postmortem

As soon as you are ready to share your document with internal or external stakeholders and subscribers you have the option to link your document to an incident.

<figure><img src="../.gitbook/assets/image (221).png" alt="" width="563"><figcaption></figcaption></figure>

{% hint style="success" %}
You may also choose to include your postmortem on all status pages that this incident appears on.
{% endhint %}

