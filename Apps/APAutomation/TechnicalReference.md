---
title: AP Automation Technical Reference
description: 
published: true
date: 2024-01-19T14:58:44.165Z
tags: 
editor: markdown
dateCreated: 2023-02-02T14:20:02.558Z
---

# AP Automation Technical Reference


# Description

The GHA AP Automation Service, is a service which interacts with Kofax Readsoft to retrieve invoice data to input into the Epicor ERP System. The service monitors each unprocessed document throughout the process on Readsoft until completion. Once the process is complete, the service will automatically read the invoice information and input it into the customer’s Epicor ERP System.

# Process Flow

Below is a diagram showing the process flow of the GHA AP Automation Service.

![screenshot_2023-02-02_140557.png](/Assets/screenshot_2023-02-02_140557.png)

## Invoice Correction

When a document contains validation errors, an email will be sent to the configured support email address

![0feccd15-a89d-4ed8-abbf-ab7da8b1b7ea.png](/Assets/0feccd15-a89d-4ed8-abbf-ab7da8b1b7ea.png)

A screenshot resembling an example of an email sent when a document is found to be erroneous

At this point, a member of GHA Support will need login to the [Readsoft Portal](https://spigraph.readsoftonline.com/), using an **Administrative Account** of the customer, and manually correct the error

### Locating the document

The link on the email should link to the erroneous document directly

> If the link is invalid, navigate to Explore > Documents on the left-hand navigation and identify the document by the Status
{.is-info}

# Setup

 Refer to the [Setup](/Apps/APAutomation/TechnicalReference/Setup) document




# Additional Details

## Mapping

Below are two tables showing how the GHA AP Automation Service maps the fields from Readsoft to the GHA AP Automation datasets.

### Header Fields

| **Readsoft Field Name** | **GHA AP Automation Dataset Field name**
|-|-|
|InvoiceNumber|Key1|
|Supplier (External Id)|VendorNum|
|OrderNumber|InvoiceNum|
|InvoiceDate|InvoiceDate|
|Currency|CurrencyCode|
|Debit/Credit|DebitMemo|
|GrossValue|DocInvoiceAmt|
|NetValue|DocNetAmt|
|VATValue|DocTaxAmt|
|OrderNumber|RefPONum|
|OrderNumber|PONum|

### Line Item Fields

|**Readsoft Field Name**|**GHA AP Automation Dataset Field name**|
|-|-|
|InvoiceNumber|Key1|
|LI_OrderLine|ChildKey1|
|Supplier (External Id)|VendorNum|
|InvoiceNumber|InvoiceNum|
|LI_OrderLine|InvoiceLine|
|LI_ProductCode|PartNum|
|LI_Description|Description|
|OrderNumber|PONum|
|LI_OrderLine|POLine|
|LI_OrderLine|PORelNum|
|OrderNumber|RefPONum|
|LI_OrderLine|RefPOLine|
|LI_OrderLine|RefPORelNum|
|LI_Quantity|DocUnitCost|
|LI_Quantity|VendorQty|
|LI_UnitofMeasure|PUM|
|LI_UnitofMeasure|IUM|
|LI_ProductCode|VenPartNum|
|LI_TotalValue|DocExtCost|

## Readsoft Field Type Table

The below links show all fields that are available from Readsoft.

> [https://ghasolutions.atlassian.net/wiki/spaces/~762347199/pages/361791492](https://ghasolutions.atlassian.net/wiki/spaces/~762347199/pages/361791492)
{.is-danger}


> [https://ghasolutions.atlassian.net/wiki/spaces/~762347199/pages/361791515](https://ghasolutions.atlassian.net/wiki/spaces/~762347199/pages/361791515)
{.is-danger}

