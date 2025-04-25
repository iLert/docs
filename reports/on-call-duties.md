---
description: Check how on-call duties report works in ilert
hidden: true
---

# On-call duties

View time on-call, time spent on alert, and number of alerts. Narrow the metrics to only a part of the day by specifying start and end times of the day.

## Page layout

<figure><img src="../.gitbook/assets/On-call duties.png" alt=""><figcaption><p>Page layout of on-call duty reports</p></figcaption></figure>

1. Metric filter
2. Chart
3. Chart tooltip
4. Table
5. Report Parameters
6. Filters

### Metric filter

Select which metric to be displayed in the chart. The table always displays all metrics.

### Chart

The chart displays the report data in a bar chart.

{% hint style="info" %}
_The legend colours for responders are generated based on the hash derived from responder identifiers. Therefore, the colour stays the same even when the responder data is changed._
{% endhint %}

### Chart tooltip

The chart tooltip appears when hovering over the chart. The tooltip displays the names and values of a specific data point. It is vertically scrollable when the list is longer.

### Table

Each row represents a data point in the chart. Click the CSV button to download the table in a CSV file.

There is another table under the tab “Shifts by day.” This table further groups the metrics by day.

### Report parameters

#### Date range

The **Date range** parameter defines the period during which alerts are created. Select a date in the calendar view and select another day or the same day. Or fill in the **From** and **Until** fields.

<figure><img src="../.gitbook/assets/date-range-picker.gif" alt="" width="480"><figcaption><p>Date-range picker demo</p></figcaption></figure>



There are four predefined date ranges: the last 12 months, the last 6 months, the last 3 months, and the last month. These date ranges are calculated relative to the current date.

**Example date ranges**

| Today       | Preset        | Range              |
| ----------- | ------------- | ------------------ |
| 8 Jun 2025  | Last 3 months | 8 Mar–8 Jun 2025   |
| 1 Mar 2025  | Last 1 month  | 1 Feb–1 Mar 2025   |
| 31 Mar 2025 | Last 1 month  | 28 Feb–31 Mar 2025 |

{% hint style="info" %}
_The **From** date is translated to the beginning of that day, and the **Until** date is translated to the beginning of the following day. This ensures that all the alerts on the From date and the Until date, plus those between them, are included in the report._
{% endhint %}

#### **Time granularity**

This parameter specifies the granularity at which the data is aggregated. Each data point in the charts and each row in tables will display a total or average value in the selected granularity.

### Filters

The filters can be used to fine-tune which data is included in the report. When the **Apply** button is clicked, all parameters and filters are saved in the page URL, making it easier to bookmark your filters.

#### Teams

The team filter is available for users with access to [Teams feature](../user-administration/teams.md). This filter affects both the report data and the subsequent filters. When some teams are selected with **Includes**, the subsequent filters will show the resources and the responders that belong to any of the selected teams. If **Excludes** is used, the subsequent filters will hide any resources or responders that belong to any of the selected teams. The same logic applies to the report data.

{% hint style="warning" %}
_Team selection is limited to a maximum of 10 teams._
{% endhint %}

#### Schedules

The **Schedules** filter can be used to show or hide the alerts associated with the selected schedules.

#### Responders

The **Responders** filter can be used to show or hide the alerts that were accepted and/or resolved by the selected responders.

{% hint style="warning" %}
_When the two filters (**Schedules** and **Responders**) are in the **Includes** state, the report data includes any alerts that are either related to the selected schedules or accepted and/or resolved by the selected responders. In other words, an alert is included if it is matched by at least one of the filters. **In the previous version of reports, an alert was included only if it matched both filters.**_
{% endhint %}

{% hint style="info" %}
_When one or more filters are set to Excludes, these filters take precedence over the filters with the **Includes**. In other words, all alerts matched by the excluded filters are not included._
{% endhint %}

### Details

View the alerts, including their ID, summary, alert source, escalation policy, reported date, TTA, and TTR.

<figure><img src="../.gitbook/assets/On-call details.png" alt=""><figcaption><p>Page layout of alert details</p></figcaption></figure>

1. Table
2. Download CSV button

#### Table

The table displays the details of alerts.

{% hint style="info" %}
The date format of the **Reported On** column changes based on the selected **Time granularity**. For example, when **Day** is selected, only time is shown. If **Week** or **Month** is selected, both date and time are shown.
{% endhint %}

#### Download CSV button

Click the button to download the table in CSV format.
