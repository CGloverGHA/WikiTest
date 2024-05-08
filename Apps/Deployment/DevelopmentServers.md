---
title: Deployment of Development Servers
description: 
published: true
date: 2024-01-19T15:00:28.162Z
tags: 
editor: markdown
dateCreated: 2023-04-26T07:56:20.323Z
---

When the development servers are restarted, the containers do not start automatically and so need redeploying.

There appears to be issues with the network in docker containers on Windows 2019 server, therefore the following commands 

```
docker rm -f (docker ps -aq)
docker image rm -f (docker image ls -q)
docker network rm (docker network ls -q)
docker system prune
```

### Development Server GHAUKDV02

<br/>

|Server|GHAUKDV01|GHAUKDVCH01|GHAUKDVCH02|
|:---|:---:|:---:|:---:|
|**Container**|**Dev 02**|**Staging**|**Testing**|
|API Gateway|&#x2713;|&#x2713;|&#x2713;|
|License API|&#x2713;|&#x2713;|&#x2713;|
|Field Service App API|&#x2713;|&#x2713;|&#x2713;|
|Field Service Web API|&#x2713;|&#x2713;|&#x2713;|
|Epicor Incoming Service API|&#x2713;|&#x2713;|&#x2713;|
|Alberta Quoting System API|&#x2713;| | |
|PO Approval API|&#x2713;| | |
|Mobile Field Service Web Front End|&#x2713;| | |
|Alberta Quoting System Front End|&#x2713;| | |
|Field Service Sync Service|&#x2713;|&#x2713;|&#x2713;|
|Field Service Data Sync Service|&#x2713;|&#x2713;|&#x2713;|
|Admin Service|&#x2713;|
|AP Automation Service|&#x2713;| | |
|Health Check Service|&#x2713;| | |
|MQ Check Service|&#x2713;| | | |
|Trim Logs Service|&#x2713;| | | |
|Wiki Outgoing Service|&#x2713;| | |


