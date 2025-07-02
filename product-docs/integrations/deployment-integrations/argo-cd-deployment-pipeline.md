# Argo CD deployment pipeline

With ilert Deployment integration for [Argo CD](https://argoproj.github.io/), you can display your deployment pipelines in ilert and enrich alerts’ context. Real-time visibility helps you quickly assess whether a recent deployment triggered an incident. This instant insight is essential for identifying issues as they occur, allowing for a faster response and minimizing downtime.

## Setting up

### Creating your deployment pipeline in ilert

In any way, a pipeline is required, which will also generate a new `integrationKey` required to route deployment events when they occur. Head to your ilert account and navigate to **Alert sources -> Deployment events.**

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Head over to the deployment pipelines tab and click on **Create new pipeline.**

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Provide a name for your pipeline.

<figure><img src="../../.gitbook/assets/1 (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

By clicking on Create, you should end up on the detail view of your Argo CD deployment pipeline.

<figure><img src="../../.gitbook/assets/2 (2).png" alt=""><figcaption></figcaption></figure>

Providing you with a freshly generated `integrationKey` and copy & pastable **URL** ready for your webhook setup.

### Configure the notification controllers configmap in Argo CD

Locate the notification controllers configmap in your setup.

Add following under `data` in the configmap and enter your :

```yaml
service.webhook.ilert: |
    url: <YOUR-ARGO-CD-PIPELINE-URL>
    headers:
      - name: "Content-Type"
        value: "application/json"

  template.ilert-app-sync-template: |
    webhook:
      ilert:
        method: POST
        body: |
          { 
            "app": {{ toJson .app }},
            "commit": {{ if .app.status.sync.revision }}{{ call .repo.GetCommitMetadata .app.status.sync.revision | toJson }}{{ else }}null{{ end }},
            "repositoryName": "{{ call .repo.FullNameByRepoURL .app.spec.source.repoURL }}"
          }

  template.ilert-app-deleted-template: |
    webhook:
      ilert:
        method: POST
        body: |
          { 
            "app": {{ toJson .app }},
            "repositoryName": "{{ call .repo.FullNameByRepoURL .app.spec.source.repoURL }}"
          }

  trigger.on-deployed: |
    - when: app.status.operationState.phase in ['Error', 'Failed', 'Succeeded']
      send: [ilert-app-sync-template]

  trigger.on-app-deleted: |
    - when: app.metadata.deletionTimestamp != nil
      send: [ilert-app-deleted-template]
```



An example for the full file could be:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: argocd-notifications-cm
  namespace: argocd
data:
  service.webhook.ilert: |
    url: <YOUR-ARGO-CD-PIPELINE-URL>
    headers:
      - name: "Content-Type"
        value: "application/json"

  template.ilert-app-sync-template: |
    webhook:
      ilert:
        method: POST
        body: |
          { 
            "app": {{ toJson .app }},
            "commit": {{ if .app.status.sync.revision }}{{ call .repo.GetCommitMetadata .app.status.sync.revision | toJson }}{{ else }}null{{ end }},
            "repositoryName": "{{ call .repo.FullNameByRepoURL .app.spec.source.repoURL }}"
          }

  template.ilert-app-deleted-template: |
    webhook:
      ilert:
        method: POST
        body: |
          { 
            "app": {{ toJson .app }},
            "repositoryName": "{{ call .repo.FullNameByRepoURL .app.spec.source.repoURL }}"
          }

  trigger.on-deployed: |
    - when: app.status.operationState.phase in ['Error', 'Failed', 'Succeeded']
      send: [ilert-app-sync-template]

  trigger.on-app-deleted: |
    - when: app.metadata.deletionTimestamp != nil
      send: [ilert-app-deleted-template]
```

Now add an annotation to your apps you want to receive a notification from by creating a subscription in your app.

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  annotations:
    notifications.argoproj.io/subscribe.on-deployed.ilert: ""
    notifications.argoproj.io/subscribe.on-app-deleted.ilert: ""
```

Test the integration by syncing your app.\
