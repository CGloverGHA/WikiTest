---
title: Documentation/Rancher/Pg8
description: 
published: true
date: 2024-04-11T11:33:40.898Z
tags: 
editor: markdown
dateCreated: 2024-04-11T11:00:06.653Z
---

# Documentation/Rancher/Pg8

## Creating a Kubernetes Lab Cluster within Rancher

In this step, we will be creating a Kubernetes Lab environment within Rancher. Normally, in a production case, you would create a Kubernetes Cluster with multiple nodes; however, with this lab environment, we will only be using one virtual machine for the cluster.
1. Go back to the Rancher Home Page
2. On top of the list of available clusters, click Create
• We will be using RKE2 cluster, so make sure to switch the toggle to RKE2/K3s
• Note the multiple types of Kubernetes cluster Rancher supports. We will be using Custom cluster on existing nodes for this lab, but there are a lot of possibilities with Rancher.
3. Click on the Custom Cluster box in the Use existing nodes and create a cluster using RKE2 section
4. Enter a name in the Cluster Name box
5. Set the Kubernetes Version to a v1.24.x version
6. All other settings can be kept as default
7. Click Create at the bottom.
8. Once the cluster is created, you can retrieve an installation command in the Registration tab that you can use to add new nodes to your Kubernetes cluster.
9. Make sure the boxes etcd, Control Plane, and Worker are all ticked.
10. Click Show Advanced to the bottom right of the checkboxes
11. Enter the Node Public IP (34.243.114.229) and Node Private IP (172.31.35.200)
• IMPORTANT: It is VERY important that you use the correct External and Internal addresses from the Cluster01 machine for this step, and run it on the correct machine. Failure to do this will cause the future steps to fail.
12. Check the checkbox to skip the TLS verification and accept insecure certificates below the registration command.
13. Double click the registration command to copy it to your clipboard.
14. Proceed to the next step of this scenario.

---
[<- Previous Page](/Documentation/Rancher/Pg7)-----[Next Page ->](/Documentation/Rancher/Pg9)