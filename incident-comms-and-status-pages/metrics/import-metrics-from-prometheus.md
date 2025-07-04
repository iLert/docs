# Import metrics from Prometheus

## Create a Prometheus metric data source

#### In ilert

1.  Go to **Incident comms** --> **Metric data sources** and click on **Create metric data source.**



    <figure><img src="../../.gitbook/assets/Screenshot 2022-12-19 at 16.14.41.png" alt=""><figcaption></figcaption></figure>
2. Give the metrics data source a name (e.g. Prometheus).
3. Select **Prometheus** in **Type** dropdown list.
4. Type in your Prometheus URL. For ex.: [https://prometheus.example.org](https://prometheus.example.org).
5. Choose your **Authentication** method.

{% hint style="info" %}
**Warning:** We recommend that you secure your Prometheus instance by using an authentication method.
{% endhint %}

**Basic auth:**

1. Enter your login credentials for Prometheus, e.g. username and password and click on **Create metric data source**.

**Custom header:**

1. Enter a custom header name, for ex. "Cookie", if you wish to authenticate via cookie header.
2. Paste your custom header value for the header name. In case of "Cookie" enter the cookie's value here and click on **Create metric data source**.

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-19 at 15.53.25.png" alt=""><figcaption></figcaption></figure>

## Create a metric

#### In Prometheus

1.  Go to **Graph** --> Type in a **query** --> Test your result with **Execute.**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-12-19 at 15.03.25.png" alt=""><figcaption></figcaption></figure>
2. Select a query from which you want to import the data into ilert. Copy the query, you will need it later.

**In ilert**

1.  Go to **Status pages** (or **Incident comms**) --> **Metrics** and click on **Create metric.**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-12-19 at 16.20.23.png" alt=""><figcaption></figcaption></figure>
2.  Select the Prometheus metrics data source that you have created above and click on **Next.**

    <figure><img src="../../.gitbook/assets/Screenshot 2022-12-19 at 16.08.40.png" alt=""><figcaption></figcaption></figure>


3.  On the next screen, enter a metric name, a display unit and paste the metric query from step 2 "In Prometheus" above. Click **Save** to preview your metric data.



    <figure><img src="../../.gitbook/assets/Screenshot 2022-12-20 at 14.07.43.png" alt=""><figcaption></figcaption></figure>


4. Preview your metric. You can make changes to your query and reload the data from Prometheus. Note that once you have created your metric, you will no longer be able to change the metric query.&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2022-12-20 at 13.51.06.png" alt=""><figcaption></figcaption></figure>
