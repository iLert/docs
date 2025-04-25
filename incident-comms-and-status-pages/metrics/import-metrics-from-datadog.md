# Import metrics from Datadog

## Create a Datadog metric data source

#### In Datadog

1.  Go to **Organization Settings** --> **API Keys** and click on **New Key**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 21.18.37.png" alt=""><figcaption></figcaption></figure>
2. Give the Key a name (e.g. ilert metrics import) and click on **Copy Key** and paste it somewhere. You will need this key later in ilert.
3. Go to **Organization Settings** --> **Application Keys** and click on **New Key**&#x20;
4. Give the Key a name and copy and paste somewhere. You will need the application key later in ilert.

#### In ilert

1.  Go to **Status pages** (or **Incident comms**) --> **Metric data sources** and click on **Create metric data source**



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 21.39.53.png" alt=""><figcaption></figcaption></figure>
2. Give the metrics data source a name (e.g. Datadog).
3. Select **Datadog** in **Type** dropdown list.
4. Select your Datadog region. You can identify your region by matching your Datadog website URL to the URL from the list.
5.  Enter the API and Application keys from above and click on **Create metric data source**.



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 21.45.17 (1).png" alt=""><figcaption></figcaption></figure>

## Create a metric

#### In Datadog

1. Find the metric you want to import to ilert, e.g. by opening a dashboard.&#x20;
2.  Click on **Edit this widget**



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 23.44.29.png" alt=""><figcaption></figcaption></figure>
3.  In the **Edit** view, chose the graph you want to import and click on the `</>` icon to display the metric query



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 23.48.31.png" alt=""><figcaption></figcaption></figure>


4.  Copy the metric query. You will need the query below in ilert.



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-24 at 23.53.00.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Note that metrics in ilert are not dimensional. Therefore, only Datadog metrics without grouping can be imported. See the Datadog documentation on [Anatomy of a metric query](https://docs.datadoghq.com/metrics/#anatomy-of-a-metric-query).

<img src="../../.gitbook/assets/Screenshot 2022-11-24 at 23.59.35 (1).png" alt="" data-size="original">

For example the following query is not supported

&#x20; `max:system.disk.in_use{host:app_prod} by {device}`

while this query is supported

&#x20; `max:system.disk.in_use{host:app_prod}`
{% endhint %}

#### In ilert

1.  Go to **Status pages** (or **Incident comms**) --> **Metrics** and click on **Create metric**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-25 at 00.10.24.png" alt=""><figcaption></figcaption></figure>
2.  Select the Datadog metrics data source that you have created above and click on **Next**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-25 at 00.11.33.png" alt=""><figcaption></figcaption></figure>


3.  On the next screen, enter a metric name, a display unit and paste the metric query from step 4 above. Click **Save** to preview your metric data.



    <figure><img src="../../.gitbook/assets/Screenshot 2022-11-25 at 00.16.56.png" alt=""><figcaption></figcaption></figure>


4. Preview your metric. You can make changes to your query and reload the data from Datadog. Note that once you have created your metric, you will no longer be able to change the metric query.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2022-11-25 at 00.28.29.png" alt=""><figcaption></figcaption></figure>

## Further References <a href="#faq" id="faq"></a>

Here are the articles on how to connect Datadog and ilert: \
\
[Datadog Inbound Integration](https://docs.ilert.com/integrations/datadog/inbound) \
[Datadog Outbound Integration](https://docs.ilert.com/integrations/datadog/outbound)
