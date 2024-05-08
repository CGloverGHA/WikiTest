---
title: Rancher Deployment Pg.3
description: 
published: true
date: 2024-04-11T11:36:08.660Z
tags: 
editor: markdown
dateCreated: 2024-04-11T10:52:03.903Z
---

# Rancher Deployment Pg.3

## Install Helm

Installing Rancher into our new Kubernetes cluster is easily done with Helm. Helm is a very popular package manager for Kubernetes. It is used as the installation tool for Rancher when deploying Rancher onto a Kubernetes cluster. In order to use Helm, we have to download the Helm CLI.
```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 \
  | bash
```
After a successful installation of Helm, we should check our installation to ensure that we are ready to install Rancher.
```
helm version --client
```

Helm uses the same kubeconfig as kubectl in the previous step.
We can check that this works by listing the Helm charts that are already installed in our cluster:
```
helm ls --all-namespaces
```
 
---
[<- Previous Page](/Doucmentation/Rancher/Pg2)-----[Next Page ->](/Documentation/Rancher/Pg4)