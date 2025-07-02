# Bulk resolving similar alerts

If you have not configured grouping for your alert sources you might end up with a view like this:

<figure><img src="../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>

Let's say you wish to clean / resolve a bulk of some specific alerts that might be duplicates in this list.

<figure><img src="../../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>

Open the search by clicking on its icon at the top bar or press CTRL/CMD + K. Then enter your desired search term aka alert summary you wish to filter for.

<figure><img src="../../.gitbook/assets/image (259).png" alt=""><figcaption></figcaption></figure>

**Click** on a matching alert in the search results.

{% hint style="info" %}
If your result hits an already resolved alert, try again, or widen your search in the category to find a PENDING alert. You may also of course just click on such an alert in the list view if you can identify it directly.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (260).png" alt=""><figcaption></figcaption></figure>

Click on **Resolve** to open the resolve context menu. Wait a second to let ilert AI fetch similar alerts, they will appear at the bottom of the menu.

<figure><img src="../../.gitbook/assets/image (261).png" alt=""><figcaption></figcaption></figure>

Use the **Select all** option to select all similar alerts (if necessary, use the individual checkbox to remove single alerts that might not exactly match your use-case). Click on **Resolve x alerts** to bulk resolve all selected alerts.

<figure><img src="../../.gitbook/assets/image (262).png" alt=""><figcaption></figcaption></figure>

Wait a short moment and you should see a confirmation message of your operation.

Looking at the alert list again, we can see that only the specific "blackbox probe failed" alerts have been resolved.

<figure><img src="../../.gitbook/assets/image (263).png" alt=""><figcaption></figcaption></figure>

Confirming our intended operation.



{% hint style="success" %}
Note that we recommend configuring alert grouping for your alert sources, especially for monitoring tools that tend to be more noisy or miss grouping operations themselves. You can find a guide here: [https://docs.ilert.com/alerting/alert-sources#alert-grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) and for more complex or custom use cases we highly recommend checking out ilert AI alert grouping: [https://docs.ilert.com/ilert-ai/using-ilert-ai-for-alert-grouping](https://docs.ilert.com/ilert-ai/using-ilert-ai-for-alert-grouping)
{% endhint %}
