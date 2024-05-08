---
title: Documentation/Rancher/Pg6
description: 
published: true
date: 2024-04-11T11:34:20.478Z
tags: 
editor: markdown
dateCreated: 2024-04-11T10:59:29.325Z
---

# Documentation/Rancher/Pg6

## Verify Rancher is Ready to Access

Before we access Rancher, we need to make sure that cert-manager has signed a certificate using the dynamiclistener-ca in order to make sure our connection to Rancher does not get interrupted. The following bash script will check for the certificate we are looking for.
```
while true; do curl -kv https://rancher.54.154.30.147.sslip.io 2>&1 | grep -q "dynamiclistener-ca"; if [ $? != 0 ]; then echo "Rancher isn't ready yet"; sleep 5; continue; fi; break; done; echo "Rancher is Ready";
```

---
[<- Previous Page](/Documentation/Rancher/Pg5)-----[Next Page -> ](/Documentation/Rancher/Pg7)
