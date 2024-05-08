---
title: Rancher Deployment Pg.5
description: 
published: true
date: 2024-04-11T11:34:37.898Z
tags: 
editor: markdown
dateCreated: 2024-04-11T10:53:07.971Z
---

# Rancher Deployment Pg.5

## Install Rancher
We will now install Rancher in HA mode onto our Rancher01 Kubernetes cluster. The following command will add rancher-latest as a helm repository.
```
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
```

Finally, we can install Rancher using our helm install command.
```
helm install rancher rancher-latest/rancher \
  --namespace cattle-system \
  --set hostname=rancher.54.154.30.147.sslip.io \
  --set replicas=1 \
  --version 2.7.4 \
  --create-namespace
```

---
[<- Previous Page](/Documentation/Rancher/Pg4)-----[Next Page ->](/Documentation/Rancher/Pg6)