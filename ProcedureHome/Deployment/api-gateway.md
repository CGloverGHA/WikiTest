---
title: api-gateway
description: 
published: true
date: 2024-01-19T15:06:11.680Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:09.206Z
---

# API Gateway

The API Gateway is used to route traffic after `https://{GHAAPI}.com/mobileportal/` to individual containers

- The source code for the API gateway is stored on `BitBucket` in the `GHASolutions` organization in a repository named `API Gateway`
- The CI pipeline is stored on `Azure DevOps` in the `GHASolutions` organization in a project name `API Gateway`

The API Gateway is built using [Ocelot](https://github.com/ThreeMammals/Ocelot)

The API Gateway is typically deployed after deploying another API to prevent `502 bad gateway` errors

## `master`

Changes to this branch will automatically build a new docker image
