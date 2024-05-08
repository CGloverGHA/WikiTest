---
title: azure-devops-deployment-repository
description: 
published: true
date: 2024-01-19T15:06:30.758Z
tags: 
editor: markdown
dateCreated: 2023-05-22T13:28:28.821Z
---

# Deployment Repository

This repository contains `docker-compose.yml` files used for deploying containers

The following `docker-compose.yml` files are included in this repository

| File Name                        | Environment                                |
| -------------------------------- | ------------------------------------------ |
| `docker-compose-development.yml` | [Development](./environments-and-servers.md#development-environment) |
| `docker-compose-testing.yml`     | [Testing](./environments-and-servers.md#testing-environment)         |
| `docker-compose-staging.yml`     | [Staging](./environments-and-servers.md#staging-environment)         |
| `docker-compose-release.yml`     | [Live](./environments-and-servers.md#live-environment)               |

This repository is typically cloned in CD pipelines for container deployment
