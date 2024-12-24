---
description: >-
  Connecting ServerGuard24 with ilert enables real-time alerts and streamlined
  incident management, allowing teams to respond swiftly to server issues and
  minimize downtime
---

# ServerGuard24 Integration

[ServerGuard24](https://www.serverguard24.com/index.html) is a comprehensive server monitoring service that ensures the availability and performance of your IT systems. It offers a range of monitoring solutions, including website monitoring, mail server monitoring, database server monitoring, and security monitoring. This guide helps to connect ServerGuard24 with ilert.

## In ilert: Create a ServerGuard24 alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **ServerGuard24** in the search field, click the ServerGuard24 tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/il-1 (2).png" alt="" width="563"><figcaption></figcaption></figure>

## In ServerGuard24: Create a Webhook

1. On the Dashboard, click on **Settings**.

<figure><img src="../.gitbook/assets/1 (16).png" alt=""><figcaption></figcaption></figure>

2. Now, on the sidebar, navigate to **Integrations** and click on the **+ New Integration** button.

<figure><img src="../.gitbook/assets/2 (14).png" alt=""><figcaption></figcaption></figure>

3. Change the **Type** to 'Custom'.
4. Change the **Request Type** to 'POST Data'
5. Now, enter a **Description** and the previously generated alert source URL in the **URL** field.

<figure><img src="../.gitbook/assets/3 (13).png" alt=""><figcaption></figcaption></figure>

6. Enter the following template into the **Data Template** field:

```json
{
  "id": "{ID}",
  "status": "{STATUS}",
  "status2": "{STATUS2}",
  "output": "{OUTPUT}",
  "remark": "{REMARK}",
  "shortlink": "{SHORTLINK}",
  "downmsg": "{DOWNMSG}",
  "timestamp": "{TIMESTAMP}",
  "datetime_gmt": "{DATETIME_GMT}",
  "datetime_loc": "{DATETIME_LOC}",
  "datetime_frm": "{DATETIME_FRM}",
  "datetime_iso": "{DATETIME_ISO}",
  "check": "{CHECK}",
  "server": "{SERVER}",
  "address": "{ADDRESS}",
  "debugoutput": "{DEBUGOUTPUT}"
}
```

<figure><img src="../.gitbook/assets/4 (12).png" alt=""><figcaption></figcaption></figure>

7. Click on **Save** to finish the setup.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the status of a ServerGuard24 check is 'OK' again, the corresponding alert in ilert will be resolved.
