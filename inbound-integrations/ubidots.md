---
description: >-
  Send alerts from Ubidots Industrial IoT platform to ilert and ensure your
  machines' uptime
---

# Ubidots Integration

[Ubidots](https://ubidots.com/) is an Industrial Internet of Things (IIoT) platform designed for developers and businesses to easily connect, collect, and visualize sensor data. It offers tools for data analysis, real-time monitoring, and automated actions, making it ideal for applications in industries such as manufacturing, healthcare, and environmental monitoring. This article provides step-by-step instructions on sending alerts from the Ubidots platform to ilert to ensure critical issues are escalated to responsible specialists as quickly as possible.&#x20;

## In ilert: Create a Ubidots alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Ubidots** in the search field, click the Ubidots tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated. You will need it later.

    <figure><img src="../.gitbook/assets/1-1 (1).png" alt=""><figcaption></figcaption></figure>



## In Ubidots: Create a Trigger Event

1. On the top bar, click on **Data** **->** **Events**.

<figure><img src="../.gitbook/assets/1 (9).png" alt="" width="563"><figcaption></figcaption></figure>

2. Now click on the "+" to create a new Trigger Event.

<figure><img src="../.gitbook/assets/2 (8).png" alt="" width="563"><figcaption></figcaption></figure>

3. Select a **Variable** and configure a trigger as you like. Click on **Next** to proceed to the next step.

<figure><img src="../.gitbook/assets/3 (7).png" alt="" width="563"><figcaption></figcaption></figure>

4. Now click on **ADD ACTION**.

<figure><img src="../.gitbook/assets/4 (6).png" alt="" width="563"><figcaption></figcaption></figure>

5. Select **Trigger webhook** from the list.

<figure><img src="../.gitbook/assets/5 (6).png" alt="" width="563"><figcaption></figcaption></figure>

6. Enter the previously in ilert created integration URL into the URL field.

<figure><img src="../.gitbook/assets/6 (7).png" alt="" width="563"><figcaption></figcaption></figure>

7. Copy and paste the following payload:

```json
{
	"eventType" : "alert",
	"deviceId" : "",
	"deviceName" : "",
	"lastValue": "",
	"lastValueTimestamp" : "",
	"triggerValue" : "",
	"triggerTimestamp" : "",
	"variableId" : "",
	"variableName": ""
}
```

8. Now fill the payload with the help of the tag button.

<figure><img src="../.gitbook/assets/10 (3).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/7 (6).png" alt="" width="563"><figcaption></figcaption></figure>

9. To send resolve events, click on **Back to Normal**.

<figure><img src="../.gitbook/assets/8 (5).png" alt="" width="563"><figcaption></figcaption></figure>

10. Enable **Back to normal action** and copy following payload:

<pre class="language-json"><code class="lang-json">{
	"eventType" : "resolved",
	"deviceId" : "",
	"deviceName" : "",
	"lastValue": "",
	"lastValueTimestamp" : "",
	"triggerValue" : "",
	"triggerTimestamp" : "",
	"variableId" : "",
<strong>	"variableName": ""
</strong>}
</code></pre>

11. Fill out the payload with the tag button.

<figure><img src="../.gitbook/assets/11 (3).png" alt="" width="563"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/9 (4).png" alt="" width="563"><figcaption></figcaption></figure>

12. Save the Trigger action to finish the setup.

## FAQ

**Will alerts in ilert be resolved automatically?**

Yes, as soon as "Back to normal action" is configured and a variable in Ubidots is back to a normal state, the associated alert is automatically resolved in ilert.&#x20;
