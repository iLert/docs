---
description: >-
  The ilert Sensu Integration helps you to publish alerts into your channels or
  resolve alerts.
---

# Sensu Integration

[Sensu](https://sensu.io/) is a tool that functions as an observability pipeline which delivers monitoring as code on any cloud.

## In ilert: Create a Sensu alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Sensu** in the search field, click on the Sensu tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Sensu

1. Add Sensu ilert Handler

```
sensuctl asset add iLert/sensu-ilert
```

2. Make sure that the asset was added to your Sensu backend. Run:

```
sensuctl asset info iLert/sensu-ilert
```

3. In the following command, replace **\<ilert\_key>** with your ilert API key.

Then run the updated command:

```
sensuctl handler create ilert \
--type pipe \
--runtime-assets iLert/sensu-ilert \
--command "sensu-ilert -t <ilert_key>"
```

4. Make sure that your handler was added by retrieving the complete handler definition in YAML or JSON format:

```
sensuctl handler info ilert --format yaml
```

5. Trigger an event. You can try it with the **file\_exists** check and an ilert handler workflow in place - remove a file to cause Sensu to send a non-OK event.

You can refer to the next section for more instructions.

## Triggering an event

### Add system subscription to entity

1. Find your entity name:

```
sensuctl entity list
```

2. The `ID` in the response is the name of your entity and replace `<entity_name>` with the name of your entity in the `sensuctl` command below. Then run the command to add the `system` subscription to your entity:

```
sensuctl entity update <entity_name>
```

3. For `Entity Class`, press enter.
4. For `Subscriptions`, type `system` and press enter.
5. Confirm both `sensu-backend` and `sensu-agent` are running. You can use `docker ps` if you are running both from docker.

### Add the `file_exists` check <a href="#add-the-file_exists-check" id="add-the-file_exists-check"></a>

1. Before you can add the check, you need to add the Nagios Foundation asset to your Sensu configuration:

```
sensuctl asset add ncr-devops-platform/nagiosfoundationCopy
```

2. To confirm that the asset was added to your Sensu backend, run:

```
sensuctl asset info ncr-devops-platform/nagiosfoundationCopy
```

3. The check command includes the path for the file that the check will look for on your system, `/tmp/my-file.txt`. For this guide, you’ll add `/tmp/my-file.txt` as a temporary file:

```
touch /tmp/my-file.txt
```

4. You should see `=== ncr-devops-platform/nagiosfoundation` followed by a list of available builds for the asset. Now that you’ve added the Nagios Foundation dynamic runtime asset, you can add its `file_exists` check to your Sensu backend. Use sensuctl to add the check:

```
sensuctl check create file_exists \
--command "check_file_exists --pattern /tmp/my-file.txt" \
--subscriptions system \
--handlers ilert \
--interval 10 \
--runtime-assets ncr-devops-platform/nagiosfoundationCopy
```

5. To confirm that the check was added to your Sensu backend and view the check definition in YAML or JSON format,

```
sensuctl check info file_exists --format yaml
```

### Trigger a `file_exists` check <a href="#trigger-an-event" id="trigger-an-event"></a>

1. Remove the file `/tmp/my-file.txt`:

```
rm /tmp/my-file.txtCopy
```

2. This will make sure the file is **not** there for Sensu to find the next time the `file_exists` check runs. After about 10 seconds, Sensu will detect that `my-file.txt` is missing and reflect that in an event. To view the event with `sensuctl`, run:

```
sensuctl event listCopy
```

3. The response should show that the file removal resulted in a _CRITICAL (2)_ event:

```
     Entity         Check                                      Output                                   Status   Silenced             Timestamp                             UUID                  
 ────────────── ───────────── ──────────────────────────────────────────────────────────────────────── ──────── ────────── ─────────────────────────────── ────────────────────────────────────── 
  host01         file_exists   CheckFileExists CRITICAL - 0 files matched pattern /tmp/my-file.txt           2   false      2021-03-15 19:28:21 +0000 UTC   1b4266ae-7200-4728-a0n4-2f50f7a56613Copy
```

4. Open the Sensu web UI to see the events the `file_exists` check is generating. Visit [http://127.0.0.1:3000](http://127.0.0.1:3000), and log in as the admin user (created during initialization when you installed the Sensu backend). The failing check’s events will be listed on the **Events** page.
5. The Alert should be created on the Sensu Alert Source on ilert's side as well
6. To complete your workflow, restore the file that you removed so Sensu sends a resolution to ilert:

```
touch /tmp/my-file.txt
```
