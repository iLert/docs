---
description: >-
  With the iLert Kubernetes integration, you can create incidents in iLert based
  on Kubernetes events and metrics.
---

# Kubernetes Integration

## In iLert <a id="in-ilert"></a>

### Create a Kubenetes alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Kubernetes" as the **Integration Type** and click on **Save**.

![](../.gitbook/assets/ilert%20%2833%29.png)

3. On the next page, a API Key is generated. You will need it below when setting up the **ilert-kube-agent** deployment.

![](../.gitbook/assets/ilert%20%2830%29.png)

## In Kubernetes <a id="in-splunk"></a>

### a. Deploy ilert-kube-agent with helm <a id="create-action-sequences"></a>

1. Add helm charts repo and update it

```text
helm repo add ilert https://ilert.github.io/charts/
helm repo update
```

2. Deploy ilert-kube-agent with the API Key  that you generated in iLert 

```text
helm upgrade --install --namespace kube-systems \
    ilert-kube-agent ilert/ilert-kube-agent \
    --set config.settings.apiKey="<YOUR KEY HERE>"
```

### b. Deploy ilert-kube-agent with manifest <a id="create-action-sequences"></a>

1. Clone the ilert-kube-agent repository

```text
git clone https://github.com/iLert/ilert-kube-agent.git
```

2. Paste the API Key that you generated in iLert into _./example/standard/30-deployment.yaml_

```text
...
          env:
            ...
            - name: ILERT_API_KEY
              value: "<YOUR KEY HERE>"
...
```

3. Apply the deployment manifest to your kubernetes cluster

```text
kubectl apply -f example/standard/
```

4. Verify that the ilert-kube-agent pods are running and ready

```text
kubectl --namespace kube-system get pod -l app=ilert-kube-agent

NAME                               READY   STATUS    RESTARTS   AGE
ilert-kube-agent-64f7dfd4d-nsnzp   1/1     Running   0          37h
ilert-kube-agent-64f7dfd4d-zx7fb   1/1     Running   0          37h
```

### c. Deploy ilert-kube-agent with terraform <a id="create-action-sequences"></a>

1. Define module and paste the API Key that you generated in iLert 

```text
module "ilert-kube-agent" {
  source  = "iLert/ilert-kube-agent/kubernetes"
  version = "0.3.4"
  replicas = 2
  api_key = "<YOUR KEY HERE>"
}
```

2. Apply changes

```text
terraform init
terraform apply
```

###  <a id="create-action-sequences"></a>

Finished! Your Kubernetes alerts will now create incidents in iLert.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an alert has been resolved in ilert-kube-agent, the associated incident in iLert will be resolved automatically.

**Can I connect multiple Kuberenetes namespaces with multiple alert sources from iLert?**

Yes, simply create multiple deployments per namespace in Kubernetes.

