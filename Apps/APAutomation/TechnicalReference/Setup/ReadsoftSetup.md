---
title: Readsoft Setup
description: 
published: true
date: 2024-02-09T15:40:52.832Z
tags: 
editor: markdown
dateCreated: 2023-02-06T15:16:19.073Z
---

# Readsoft Setup

This section describes the process of setting up a **Customer Account** on the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/")

# Creating the Customer Account

## 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

## 2. Navigate to **Customers**

![readsoft1.png](/readsoft1.png)

Please ensure the Auto-rotate images option is selected as shown below.
![ap_kofax.png](/apautomation/ap_kofax.png)

## 3. Click on **ADD**

![readsoft2.png](/readsoft2.png)

## 4. Enter the **Profile Details**

![readsoft4.png](/readsoft4.png)

## 5. Ensure that the following **Services** are enabled

![readsoft5.png](/readsoft5.png)

It is essential that **API** is the selected option for **Target System**

# Email Input Setup

In order for documents to be sent to the Readsoft system via email, a **email input** must be setup

## 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

## 2. Navigate to `Customers/{Customer}/Account/Services/Email input`

Where **{Customer}** is the name of the customer that is currently being set up

![readsoft6.png](/readsoft6.png)

## 3. Ensure that the Email input settings are correct

Readsoft will create a **default input email**, as such ensure that the settings of this email match the settings below

![readsoft7.png](/readsoft7.png)

# Extraction Setup

In order for the **GHA AP Automation Service** to track erroneous documents, a **customer Header Field** must be added

## 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

## 2. Navigate to `Customers/{Customer}/Account/Services/Extraction`

![readsoft8.png](/readsoft8.png)

Where **{Customer}** is the name of the customer that is currently being set up

## 3. Add the `ToLearn` **Header Field** to each **Document Type**

Repeat the following steps **for each Document Type**

### 3a. Click **Edit**

![readsoft9.png](/readsoft9.png)

### 3b. Click the **Hyperlink** of the current **Document Type**

![readsoft10.png](/readsoft10.png)

### 3c. Click **ADD HEADER FIELD**

![readsoft11.png](/readsoft11.png)

### 3d. Enter the following details and click **OK**

![readsoft12.png](/readsoft12.png)

### 3e. Click **OK**

![readsoft13.png](/readsoft13.png)

### 3f. Click **SAVE**

![readsoft14.png](/readsoft14.png)

# Master Data Setup

By default, Readsoft assigns **suppliers** at a **buyer** level which will cause errors when the **GHA AP Automation Service** attempts to synchronise the **Epicor vendors**

## 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

## 2. Navigate to `Customers/{Customer}/Account/Services/Master data`

Where **{Customer}** is the name of the customer that is currently being set up

![readsoft15.png](/readsoft15.png)

## 3. Click **EDIT**

![readsoft16.png](/readsoft16.png)

## 4. Set `MASTER DATA UPLOAD` to `Master data on customer account level` and click **SAVE**

![readsoft17.png](/readsoft17.png)

# Process Control Setup

To bypass the [Verification](https://docs.readsoftonline.com/help/eng/partner/office/verifying/c_verifying_invoices_overview.html#rso131220017_verifying_invoices__overview "https://docs.readsoftonline.com/help/eng/partner/office/verifying/c_verifying_invoices_overview.html#rso131220017_verifying_invoices__overview") process. the **Process Control** must be set to never verify documents

## 1. Login to the [Readsoft Portal](https://ghasolutions.readsoftonline.com/ "https://ghasolutions.readsoftonline.com/") using a **GHA Administrative Account**

## 2. Navigate to `Customers/{Customer}/Account/Services/Process control`

Where **{Customer}** is the name of the customer that is currently being set up

![readsoft18.png](/readsoft18.png)

## 3. Click **EDIT**

![readsoft19.png](/readsoft19.png)

## 4. Set `DATA VERIFICATION` to `Never` and click **SAVE**

![readsoft20.png](/readsoft20.png)