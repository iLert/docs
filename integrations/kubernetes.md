---
description: >-
  With the ilert Kubernetes integration, you can create alerts in ilert based on
  Kubernetes events and metrics.
---

# Kubernetes Integration

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Kubenetes alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Kubernetes" as the **Integration Type** and click on **Save**.

![](<../.gitbook/assets/iLert (32).png>)

1. On the next page, a API Key is generated. You will need it below when setting up the **ilert-kube-agent** deployment.

![](<../.gitbook/assets/iLert (33).png>)

## In Kubernetes <a href="#in-kubernetes" id="in-kubernetes"></a>

### a. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with helm (recommended) <a href="#deploy-a" id="deploy-a"></a>

1. Add helm charts repo and update it

```
helm repo add ilert https://ilert.github.io/charts/
helm repo update
```

1. Deploy ilert-kube-agent with the API Key  that you generated in ilert&#x20;

```
helm upgrade --install --namespace kube-system \
    ilert-kube-agent ilert/ilert-kube-agent \
    --set config.settings.apiKey="<YOUR KEY HERE>"
```

### b. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with terraform (recommended) <a href="#deploy-b" id="deploy-b"></a>

1. Define module and paste the API Key that you generated in ilert&#x20;

```
module "ilert-kube-agent" {
  source  = "iLert/ilert-kube-agent/kubernetes"
  version = "0.3.9"
  replicas = 2
  api_key = "<YOUR KEY HERE>"
}
```

1. Apply changes

```
terraform init
terraform apply
```

### c. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with manifest <a href="#deploy-c" id="deploy-c"></a>

1. Clone the ilert-kube-agent repository

```
git clone https://github.com/iLert/ilert-kube-agent.git
```

1. Paste the API Key that you generated in ilert into _./example/standard/30-deployment.yaml_

```
...
          env:
            ...
            - name: ILERT_API_KEY
              value: "<YOUR KEY HERE>"
...
```

1. Apply the deployment manifest to your kubernetes cluster

```
kubectl apply -f deployment/standard/
```

1. Verify that the ilert-kube-agent pods are running and ready

```
kubectl --namespace kube-system get pod -l app=ilert-kube-agent

NAME                               READY   STATUS    RESTARTS   AGE
ilert-kube-agent-64f7dfd4d-nsnzp   1/1     Running   0          37h
ilert-kube-agent-64f7dfd4d-zx7fb   1/1     Running   0          37h
```

Finished! Your Kubernetes alerts will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an alert has been resolved in ilert-kube-agent, the associated alert in ilert will be resolved automatically.

**Can I connect multiple Kuberenetes namespaces with multiple alert sources from ilert?**

Yes, simply create multiple deployments per namespace in Kubernetes.
