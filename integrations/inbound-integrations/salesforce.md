---
description: >-
  Salesforce provides customer relationship management service and also provides
  a complementary suite of enterprise applications focused.
---

# Salesforce Integration

## In ilert: Create a Salesforce alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Salesforce** in the search field, click on the Salesforce tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Salesforce

_This Documentation is based on the new Salesforce Lightning, new UI from Salesforce_

Navigate to Developer Console by clicking the **Settings** icon and then click the **Developer Console**.

![](../../.gitbook/assets/salesforce-newmenu.png)

In Developer Console page select **File** -> **New** -> **Apex Class** and copy the following and save it as **`ilertClass.apxc`**, then click Save.

```java
global class ilertClass {

    @future(callout=true)
    WebService static void xRESTCall(String endpoint, String payload){
        HttpRequest req = new HttpRequest();
        req.setEndpoint(endpoint);
        req.setMethod('POST');
        req.setBody(payload);
        req.setHeader( 'Content-Type', 'application/json' );
        req.setHeader( 'Accept', 'application/json' );
        Http http = new Http();
        HTTPResponse res = http.send(req);
        System.debug(' Response: ' + res.getBody());
    }

    global static string getPayloadStringByHandlingNull(String value){
        return value==null?null:'"'+value.replaceAll('[^a-zA-Z0-9\\s]', '').replaceAll('\\s+', ' ')+'"';
    }

    global static string getPayloadStringByHandlingNull(DateTime value){
        return value==null?null:'"'+value+'"';
    }

    global static string getPayloadStringByHandlingNull(Decimal value){
        return value==null?null:'"'+value+'"';
    }

    global static string getPayloadStringByHandlingNull(Boolean value){
        return value==null?null:'"'+value+'"';
    }
  }
```

Create a trigger by clicking **File** -> **New** -> **Apex Trigger** and copy the following and save it as **`ilertTrigger.apxt`**. Please make sure that the `API_KEY` and the `URL` is replaced based on the relevant `API_KEY` and `URL` that were received from ilert side.

```java
trigger ilertCaseTrigger on Case (after insert, after update) {
    
    string endpoint = 'URL';
    string apiKey = 'API_KEY';
    Case obj = Trigger.new[0];
    
    System.debug('ilertCaseTrigger Fired');

    string caseNumber = obj.CaseNumber;
    string subject = obj.Subject;
    string description = obj.Description;
    
    string eventType = 'ALERT';

    if (obj.IsClosed) {
        eventType = 'RESOLVE';
    }

   string payload= '{'+       
        '\"eventType\" :' + ilertClass.getPayloadStringByHandlingNull(eventType)+ ',' +
        '\"apiKey\" :' + ilertClass.getPayloadStringByHandlingNull(apiKey)+ ',' +
        '\"incidentKey\" :' + ilertClass.getPayloadStringByHandlingNull(caseNumber)+ ',' +
        '\"summary\" :' + ilertClass.getPayloadStringByHandlingNull(subject)+ ',' +
        '\"details\" :' + ilertClass.getPayloadStringByHandlingNull(description) +
    '}';
    
    System.debug('Payload: ' + payload);

    ilertClass.xRESTCall(endpoint, payload);
}
```

In order to send to ilert, the domain needs to be allowlisted, back to the Salesforce page and select Setup from settings and go to **Setup** -> **Security** -> **Remote Site** Settings page.

![](../../.gitbook/assets/salesforce-remote.png)

Add a new remote site name it "iLert" and then paste the URL copied **`https://api.ilert.com`** to the "Remote Site URL" field and Save.

To test this, simply create a **Case** in Salesforce.

## FAQ

1.  How to Debug in case something is not working?\
    \
    In order to Debug this, you need to add `System.debug()` either on the trigger or the class. To view this just navigate to **Gear Icon -> Setup -> Environment -> Logs -> Debug Logs**\\

    ***
2. I don't see my logs, why?\
   \
   Make sure that the **Expiration Date** settings in the Debug Logs settings are set in the future, just edit it if it was done in the past, and create Case again.

![](../../.gitbook/assets/salesforce-debuglogs.png)
