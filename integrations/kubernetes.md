---
description: >-
  With the ilert Kubernetes integration, you can create alerts in ilert based on
  Kubernetes events and metrics.
---

# Kubernetes Integration

## In ilert: Create a Kubernetes alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Kubernetes** in the search field, click on the Kubernetes tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Kubernetes <a href="#in-kubernetes" id="in-kubernetes"></a>

### a. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with helm (recommended) <a href="#deploy-a" id="deploy-a"></a>

1. Add helm charts repo and update it

```
helm repo add ilert https://ilert.github.io/charts/
helm repo update
```

2. Deploy ilert-kube-agent with the API Key that you generated in ilert

```
helm upgrade --install --namespace kube-system \
    ilert-kube-agent ilert/ilert-kube-agent \
    --set config.settings.apiKey="<YOUR KEY HERE>"
```

### b. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with terraform (recommended) <a href="#deploy-b" id="deploy-b"></a>

1. Define module and paste the API Key that you generated in ilert

```
module "ilert-kube-agent" {
  source  = "iLert/ilert-kube-agent/kubernetes"
  version = "0.3.9"
  replicas = 2
  api_key = "<YOUR KEY HERE>"
}
```

2. Apply changes

```
terraform init
terraform apply
```

### c. Deploy [ilert-kube-agent](https://github.com/iLert/ilert-kube-agent) with manifest <a href="#deploy-c" id="deploy-c"></a>

1. Clone the ilert-kube-agent repository

```
git clone https://github.com/iLert/ilert-kube-agent.git
```

2. Paste the API Key that you generated in ilert into _./example/standard/30-deployment.yaml_

```
...
          env:
            ...
            - name: ILERT_API_KEY
              value: "<YOUR KEY HERE>"
...
```

3. Apply the deployment manifest to your kubernetes cluster

```
kubectl apply -f deployment/standard/
```

4. Verify that the ilert-kube-agent pods are running and ready

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
