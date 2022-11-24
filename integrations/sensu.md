---
description: >-
  The ilert Sensu Integration helps you to publish alerts into your channels or
  resolve alerts.
---

# Sensu Integration

[Sensu](https://sensu.io/) is a tool that functions as an observability pipeline which delivers monitoring as code on any cloud.

## In ilert

* Go to the "**Alert sources**" tab and click "**Create new alert source**"

![](../.gitbook/assets/screenshot-cloudelca.ilert.com-2021.08.31-21\_08\_34.png)

* Enter a name and select your desired escalation policy.  &#x20;
* Select "Sensu" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/screenshot-cloudelca.ilert.com-2021.08.31-21\_04\_34.png)

* On the next page, an **API key** is generated. You will need the API Key when setting up the handler in Sensu.

![](../.gitbook/assets/screenshot-cloudelca.ilert.com-2021.08.31-21\_05\_48.png)

## In Sensu

* Add Sensu ilert Handler

```
sensuctl asset add iLert/sensu-ilert
```

* Make sure that the asset was added to your Sensu backend. Run:

```
sensuctl asset info iLert/sensu-ilert
```

* In the following command, replace **\<ilert\_key>** with your ilert API key.  &#x20;

Then run the updated command:

```
sensuctl handler create ilert \
--type pipe \
--runtime-assets iLert/sensu-ilert \
--command "sensu-ilert -t <ilert_key>"
```

* Make sure that your handler was added by retrieving the complete handler definition in YAML or JSON format:

```
sensuctl handler info ilert --format yaml
```

* Trigger an event. You can try it with the **file\_exists** check and an ilert handler workflow in place - remove a file to cause Sensu to send a non-OK event. &#x20;

You can refer to the next section for more instructions.

## Triggering an event

### Add system subscription to entity

* Find your entity name:

```
sensuctl entity list
```

* The `ID` in the response is the name of your entity and replace `<entity_name>` with the name of your entity in the `sensuctl` command below. Then run the command to add the `system` subscription to your entity:

```
sensuctl entity update <entity_name>
```

* For `Entity Class`, press enter.
* For `Subscriptions`, type `system` and press enter.
* Confirm both `sensu-backend` and `sensu-agent` are running. You can use `docker ps` if you are running both from docker.

### Add the `file_exists` check <a href="#add-the-file_exists-check" id="add-the-file_exists-check"></a>

* &#x20;Before you can add the check, you need to add the Nagios Foundation asset to your Sensu configuration:

```
sensuctl asset add ncr-devops-platform/nagiosfoundationCopy
```

* To confirm that the asset was added to your Sensu backend, run:

```
sensuctl asset info ncr-devops-platform/nagiosfoundationCopy
```

* The check command includes the path for the file that the check will look for on your system, `/tmp/my-file.txt`. For this guide, you’ll add `/tmp/my-file.txt` as a temporary file:

```
touch /tmp/my-file.txt
```

* You should see `=== ncr-devops-platform/nagiosfoundation` followed by a list of available builds for the asset. Now that you’ve added the Nagios Foundation dynamic runtime asset, you can add its `file_exists` check to your Sensu backend. Use sensuctl to add the check:

```
sensuctl check create file_exists \
--command "check_file_exists --pattern /tmp/my-file.txt" \
--subscriptions system \
--handlers ilert \
--interval 10 \
--runtime-assets ncr-devops-platform/nagiosfoundationCopy
```

* To confirm that the check was added to your Sensu backend and view the check definition in YAML or JSON format,

```
sensuctl check info file_exists --format yaml
```

### Trigger a `file_exists` check <a href="#trigger-an-event" id="trigger-an-event"></a>

* Remove the file `/tmp/my-file.txt`:

```
rm /tmp/my-file.txtCopy
```

* This will make sure the file is **not** there for Sensu to find the next time the `file_exists` check runs. After about 10 seconds, Sensu will detect that `my-file.txt` is missing and reflect that in an event. To view the event with `sensuctl`, run:

```
sensuctl event listCopy
```

* The response should show that the file removal resulted in a _CRITICAL (2)_ event:

```
     Entity         Check                                      Output                                   Status   Silenced             Timestamp                             UUID                  
 ────────────── ───────────── ──────────────────────────────────────────────────────────────────────── ──────── ────────── ─────────────────────────────── ────────────────────────────────────── 
  host01         file_exists   CheckFileExists CRITICAL - 0 files matched pattern /tmp/my-file.txt           2   false      2021-03-15 19:28:21 +0000 UTC   1b4266ae-7200-4728-a0n4-2f50f7a56613Copy
```

* Open the Sensu web UI to see the events the `file_exists` check is generating. Visit [http://127.0.0.1:3000](http://127.0.0.1:3000), and log in as the admin user (created during initialization when you installed the Sensu backend). The failing check’s events will be listed on the **Events** page.
* The Alert should be created on the Sensu Alert Source on ilert's side as well
* To complete your workflow, restore the file that you removed so Sensu sends a resolution to ilert:

```
touch /tmp/my-file.txt
```
