---
description: >-
  The ilert SolarWinds Integration extends SolwarWinds Orion products with
  ilert's powerful alerting and on-call management capabilities.
---

# SolarWinds Integration

With the ilert SolarWinds Integration you can easily integrate SolarWinds Orion products (eg [NPM](https://www.solarwinds.com/network-performance-monitor) and [SAM](https://www.solarwinds.com/server-application-monitor)) into ilert. The integration extends SolarWinds with SMS, push and voice notification as well as on-call schedules from ilert. Alerts are created in ilert and automatically resolved. Furthermore, alerts in ilert that were created by SolarWinds contain links to the respective alerts in SolarWinds.

## In ilert: Create SolarWinds alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **SolarWinds** in the search field, click on the SolarWinds tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## &#x20;<a href="#create-topic" id="create-topic"></a>

## In SolarWinds: create alert definition <a href="#alert-definition" id="alert-definition"></a>

1. Go to the **Settings → All Settings** tab and click **Manage Alerts**

![](../.gitbook/assets/sw3.png)

2. Click on **ADD NEW ALERT**

![](../.gitbook/assets/sw4.png)

3. Fill out the **Alert Properties** according to your requirements and click on **NEXT**

![](../.gitbook/assets/sw5.png)

4. Define the **trigger condition** on the next page and click on **NEXT**. The **trigger condition** defines the conditions under which you want to be alerted via ilert. You can use the full flexibility of SolarWinds here. In this example we define the following condition: Immediate alarm for all **nodes** that are not in the status **up**.

![](../.gitbook/assets/sw6.png)

5. Define **reset condition** and click on **NEXT**. As soon as the **reset condition** occurs, the associated alert is resolved in ilert.

![](../.gitbook/assets/sw7.png)

6. Select **Time of Day** according to your requirements and click on **NEXT**.

![](../.gitbook/assets/sw8.png)

7. **TRIGGER ACTIONS**: Click **Add Action** and select **Send a GET or POST Request to a Web Server** to add **trigger action**.

![](../.gitbook/assets/sw9.png)

![](../.gitbook/assets/sw10.png)

8. Enter the `HTTP POST` Action URL generated in ilert in the **URL** field and select Use **HTTP / S POST** . Enter the following in the **Body to POST** field:

![](../.gitbook/assets/sw11.png)

```
iLertEventType=ALERT&
iLertIncidentKey=${N=Alerting;M=AlertObjectID}-${N=Alerting;M=AlertActiveID}&
iLertEventSummary=${N=SwisEntity;M=DisplayName} (${N=SwisEntity;M=IP_Address}): ${N=SwisEntity;M=StatusDescription}&
iLertUrl=${N=Alerting;M=AlertDetailsUrl}&
AcknowledgeUrl=${N=Alerting;M=AcknowledgeUrl}&
AlertName=${N=Alerting;M=AlertName}&
AlertActiveID=${N=Alerting;M=AlertActiveID}&
AlertObjectID=${N=Alerting;M=AlertObjectID}&
ObjectType=${N=Alerting;M=ObjectType}&
Severity=${N=Alerting;M=Severity}
```

9. **Optional**: Activate the **Repeat this action action every X minutes until the alert is acknowledged** option in the **execution settings**. This is for safety, if an alert could not be sent to ilert (e.g. due to a network problem).

![](../.gitbook/assets/sw12.png)

10. &#x20;On **ADD ACTION** and then click **NEXT**.
11. &#x20;**RESET ACTIONS**: Click **Add Action** and select **Send a GET or POST Request to a Web Server** to add **Reset Action**. Enter the `HTTP POST` Action URL generated in ilert in the **URL** field and select Use **HTTP / S POST** . Enter the following in the **Body to POST** field :

![](../.gitbook/assets/sw13.png)

```
iLertEventType=RESOLVE&
iLertIncidentKey=${N=Alerting;M=AlertObjectID}-${N=Alerting;M=AlertActiveID}&
iLertEventSummary=${N=SwisEntity;M=DisplayName} (${N=SwisEntity;M=IP_Address}): ${N=SwisEntity;M=StatusDescription}
```

12. &#x20;On **ADD ACTION** and then click **NEXT**.
13. &#x20;Click **SUBMIT** on the **SUMMARY** page.

## FAQ <a href="#faq" id="faq"></a>

**Are alerts automatically resolved in ilert?**

Yes, as soon as the **reset condition** for an alert has occurred in SolarWinds, the associated alert in ilert is resolved.

**What if an alert is acknowledged in SolarWinds, is the associated alert also acknowledged in ilert?**

No, in SolarWinds it is unfortunately not possible to perform an action after an **acknowledge**.

**Can I link SolarWinds to multiple alert sources in ilert?**

Yes, create several alert definitions in SolarWinds and store the corresponding URL of the alert source from ilert in the HTTP URL.

**What if my internet connection is lost? Are the alerts generated in SolarWinds lost?**

No, no alerts are lost if you have activated the option **Repeat this action action every X minutes until the alert is acknowledged** in SolarWinds (see above). We also recommend that you monitor your Internet connection with an external monitoring service, such as ilert's [Uptime monitoring](https://www.ilert.com/product/uptime-monitoring/).

**Can I change the content of the alert in ilert (e.g. the summary)?**

Yes, you can configure this in the definition of the trigger action. In the HTTP Post Body, several variables in the format `variable1=value1&variable2=value2&variable3=value3...` are sent to ilert. To change the summary text of the alert, change the definition of the variable `iLertEventSummary` . All other variables that you add below `iLertEventSummary` inserted in the description of the alert.

**The integration doesn't work. How do I find the issue?**

If you do not find the error, please contact our support at [support@ilert.com](mailto:support@ilert.com).
