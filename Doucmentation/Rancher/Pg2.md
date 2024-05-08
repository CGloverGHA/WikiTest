---
title: Rancher Deployment Pg.2
description: 
published: true
date: 2024-04-11T11:37:44.083Z
tags: 
editor: markdown
dateCreated: 2024-04-11T10:51:24.720Z
---

# Rancher Deployment Pg.2
## Testing your cluster

RKE2 now created a new Kubernetes cluster. In order to interact with its API, we can use the Kubernetes CLI kubectl.

To install kubectl run:
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```


We also have to ensure that kubectl can connect to our Kubernetes cluster. For this, kubectl uses standard Kubeconfig files which it looks for in a KUBECONFIG environment variable or in a ~/.kube/config file in the user's home directory.
RKE2 writes the Kubeconfig of a cluster to /etc/rancher/rke2/rke2.yaml.

We can soft symlink the /etc/rancher/rke2/rke2.yaml file to our ~/.kube/config file so that kubectl can interact with our cluster:
```
mkdir -p ~/.kube
ln -s /etc/rancher/rke2/rke2.yaml ~/.kube/config
```
 
In order to test that we can properly interact with our cluster, we can execute two commands.
To list all the nodes in the cluster and check their status:
```
kubectl get nodes
```
The cluster should have one node, and the status should be "Ready".
To list all the Pods in all Namespaces of the cluster:
```
kubectl get pods --all-namespaces
```
All Pods shoud have the status "Running".

---

[<- Previous Page](/Documentation/Rancher)-----[Next Page ->](/Documentation/Rancher/Pg3)