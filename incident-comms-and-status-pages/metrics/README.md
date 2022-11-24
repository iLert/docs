---
description: >-
  Provide basic information about the health of your services by including
  metrics in status pages
---

# Metrics

Metrics in ilert lets you provide additional information about the health of your services in status pages.

## What is a metric?

A metric is a numerical value that can track anything over time, such as API response time, API error rates, number of open tickets, etc. ilert stores metric data as pairs of floating point values and timestamps.

## Metric Display Options in ilert

ilert provides two ways to display a metric

1. Line graph (optionally with an aggreated value)
2. Single number

### Line Graph

Here's an example of a metric visualized as a line graph:

<figure><img src="../../.gitbook/assets/What is a metric.png" alt=""><figcaption></figcaption></figure>

* **Display name**: The name of the metric that will be displayed on the status page
* **Period:** A metric can be visualized over a period of 24 hours (day), 7 days (week) or 28 days (month).
* **Aggregated value:** An single value that combines all values over the selected period by applying an aggregration function. The aggregated value is shown in the top right corner of the graph and can be hidden. ilert provides four aggregations that you can choose from:
  * AVG: the arithmetic average of all values over the selected period
  * SUM: the arithmetic sum of all values over the selected period
  * MIN: the minimum value of all values over the selected period
  * MAX: the maximum value of all values over the selected period
* **Display unit:** this unit will be shown as a suffix. Note that this unit is just for display purposes and can be left empty.

{% hint style="info" %}
**Interval aggregration in graphs (aka rollup aggregration)**

ilert stores a large number of data points per metric (up to one datapoint every 30 seconds). In most cases, there are more data points than what can be visualized on a graph. Therefore, ilert aggregates the values by combining them in time intervals. For example, when selecting Month as period, data points are aggregated into 2 hour intervals. To aggreate the values, ilert uses the same aggregation function that you select for the summary display in the right corner of the graph.

**Periods and Aggreation Intervals**

* Month - 2 hours
* Week - 30 minutes
* Day - 5 minutes
{% endhint %}

#### Linear interpolation

With linear interpolation, missing data points will be shown by drawing a straight line between two known data points. If you disable linear interpolation, missing data points will be shown as gaps in the line graph.

**Example**

The following metric has missing data points. Below you can see the effect of interpolation.

|            Interpolation enabled           |           Interpolation disabled           |
| :----------------------------------------: | :----------------------------------------: |
| ![](<../../.gitbook/assets/image (1).png>) | ![](<../../.gitbook/assets/image (4).png>) |

### Single number metric

Here's an example of a metric that is displayed as a single number:

<figure><img src="../../.gitbook/assets/Single metric.png" alt=""><figcaption></figcaption></figure>

Metrics that are displayed as a single number provide the same aggregration functions from above. Additionally, you can chose to display the last reported value (i.e. the value with the latest timestamp).

## Create a metric

1. In the main navigation bar, click on **Status pages** (or **Incident comms**) --> **Metrics**
2. Click on the **Create metric** button
3. Chose your metric data source. You can either submit metric data using our [Series API](https://api.ilert.com/api-docs/#tag/Series/paths/\~1series\~1{key}/post) or import metrics from a 3rd party metrics provider such as Datadog or Prometheus.
4. Configure your metric and click **Save**

## Add a metric to status page

Once you have created a metric, you can add the metric to any of your status pages.

1. Navigate to the status page to which you want to include the metric
2.  Go to the the **Metrics** tab, click on the **Add metric** button and select the metrics that you would like to add to the status page.

    <figure><img src="../../.gitbook/assets/Screen Shot 2022-10-20 at 15.47.08.png" alt=""><figcaption></figcaption></figure>
3. The metric will now be displayed on your status page. You can change the order of metrics by reordering the metrics in the metrics tab of the status using drag and drop.

## Submit data points to a metric

Submitting data points to your metric is as easy making an HTTP POST request using the API key of your metric.

{% hint style="info" %}
**Metrics API Key**

Every metric has its own API key, just like alert sources have their own API keys. You cannot use your personal API key so submit metrics data at the moment.
{% endhint %}

You will find the API key of the metric in the metric's settings page:

<figure><img src="../../.gitbook/assets/Screen Shot 2022-10-21 at 08.41.23.png" alt=""><figcaption></figcaption></figure>

Here's an example curl command to update the above MTTA metric to 8.223 minutes:

```shell
curl -L -X POST 'https://api.ilert.com/api/series/ilm110229945419465b5494fxxxxxxxxxxxxxxxxf' \
-H 'Content-Type: application/json' \
--data-raw '{
    "value": 8.223
}'
```

Note that the timestamp value is omitted in the JSON payload. In this case, the current time stamp will be used.

Our API also support submitting multiple data points at once. Refer to our [API documentation](https://api.ilert.com/api-docs/#tag/Series/paths/\~1series\~1{key}/post) for more information.

{% hint style="info" %}
**iLert's Metric Data Storage**

* A metric can store maximum 1 data point every 30 seconds. Each submitted data point is truncated to its nearest 30s interval.
* Submitting data points with a higher resolution will result in the last data point being the only one stored.
* A metric can store data up to 28 days in the past. When creating a new metric, we recommend to backfill data for the past 28 days.
{% endhint %}

### Generate sample data

ilert lets you generate one time sample data for your metric

1. Open your metrics settings page
2. Click on the `...` button in the top right and select **Generate demo data**
3. Select the range for the random data and click on **Generate demo data**

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

### Clear metrics data

To clear metrics data

1. Open your metrics settings page
2. Click on the `...` button in the top right and select **Delete metric data**

This will delete all data points for that metrics.
