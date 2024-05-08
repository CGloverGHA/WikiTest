---
title: deployment-strategies
description: 
published: true
date: 2024-01-19T15:07:03.834Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:29:04.744Z
---

# Deployment Strategies

A "Deployment Strategy" refers to the strategy used to deploy a piece of software.

## Docker Deployment Strategy

> This is the current deployment strategy used at GHA Solutions.

This deployment strategy follows these steps

- Build the docker image on [Development Server 2](./environments-and-servers.md#development-server-2)
  - Save the docker image to a TAR file
- Deploy the image to the relevant server
  - Download the TAR file
  - Load the docker image
    - Deploy the container using docker compose

Notes:

- Windows containers are used for this strategy
- GMSA accounts are used on the Staging & Live servers
