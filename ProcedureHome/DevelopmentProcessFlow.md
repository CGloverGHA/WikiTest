---
title: Development Process Flow
description: 
published: true
date: 2024-01-19T15:08:24.951Z
tags: 
editor: markdown
dateCreated: 2023-02-02T13:53:06.819Z
---

# Development Process Flow


---

## Stage Gate Process

A point at which no further work should be carried out on a project unless all the preceeding work has been completed.

Each section heading represents a stage gate (to be reviewed)

---

## Formation

### Project Statement

A one sentence summary of the project

### Project Viability

ROI and Cost Analysis to check the project viability

### Project added to Jira

The project should be added to Jira with the statement against the description

### Project added to Confluence

Each project should have a Project Master Document

---

## Requirements and Planning

[https://doyouevenerp.com/business-vs-functional-vs-technical-requirements/](https://doyouevenerp.com/business-vs-functional-vs-technical-requirements/)

### Business Requirements

The business case for the change. This should be non technical and may take the form of a user story. What value is being added to both the GHA software and the customer experience.

**Why** are we making the change?

### Functional Requirements

This is filled in by the business analyst for the project and should discuss the following:

-   Process Flow and Details
    
-   Business Rules and Data Requirements
    
-   Interfaces to External Systems
    
-   Security
    
-   Audit Trail
    

**What** is the change?

### Technical Requirements

This is fllled by the developer and discusses the changes made, design patterns and decisions

There should be sections for each type of software affected:

-   Database
    
-   API
    
-   Front End
    
-   Web Pages
    
-   App Pages
    
-   Services
    
-   Epicor
    

**How** are the changes implemented?

### Requirements Review and Approval

All requirements should be peer reviewed before proceeding

---

## Development

### Coding

### Code Review

All code shoud be peer reviewed

---

## Test

### Unit Test

If applicable, each change should either have a Postman collection or be integrated into existing collections and perform part of the overall Unit Tests

### System Test

Before a change is released a full System Test should be performed to make sure nothing else has been affected.

---

## Product Release

### Change Advisory Board

The CAB comprising of Andy Wilson and Peter Roden should review every change before deployment to a production system.

### Change Request Document

For each release a change request document should be prepared which outlines the changes to be made (links to Confluence and/or Jira are acceptable)

The Change Request Document is reviewed by the Change Advisory Board

-   Impact Analysis
    
-   Approve or Deny
    
-   Implement Change
    

### Deployment Documents

Before release the following documents must be prepare in Confluence using the templates provided:

-   Internal Deployment
    
-   External (customer) Deployment
    
-   Change notes
    

### Jira Release

Post deployment a Jira release should be released with the Jira issues included

### Review and Reporting

The change should be reviewed a week after implementation to monitor successes or failures.

Failures should be documented in the Change Failure Document so lessons can be learnt and changes implemented

---

## Post Implementation

### Support Documents

Each change should be formally passed over to support by adding the appropriate documentation to the Project Master Document
