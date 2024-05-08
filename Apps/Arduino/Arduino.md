---
title: Untitled Page
description: 
published: true
date: 2024-01-19T14:58:48.905Z
tags: 
editor: markdown
dateCreated: 2023-04-27T13:20:03.020Z
---

## What To Do In Epicor
1. Count Parts going through 
	1. Add Quantity to material on Job?
	2. Issue Quantity of part to material on Job?
2. Receive to stock? 
	3. Of different colours
3. Automatic Non-conformance based on colours
4. Goods In?
	1. Add lines to PO Receipt?
		1. Initially arrived then received? (Needs two sensors)
5. Order Picking?
	1. Add lines to Customer Shipment?

sorting out different colours

## `UD19` Data Types
|     | Key1       | Character01        | Character 02   | Number01   | Date01        |
| --- | ---------- | ------------------ | -------------- | ---------- | ------------- |
|     | `{Random}` | AddQuantityToJob   | `{ballColour}` | `{amount}` | `{timestamp}` |
|     | `{Random}` | IssueQuantityToJob | `{ballColour}` | `{amount}` | `{timestamp}` |
|     | `{Random}` | ReceiveToStock     | `{ballColour}` | `{amount}` | `{timestamp}` | 
> A table of the data that is sent per each "action" to the `UD19` table







# Document
# Physical layout
![arduino.png](/arduino.png)

![image_2023-10-31_132424075.png](/image_2023-10-31_132424075.png)
# What It Does
A x sensor

# Limitations
1. The Arduino does not support multithreading so REST calls to Epicor can take a few seconds halting further sensing of balls
	- There are proposed workarounds but none are implemented as of yet


# Epicor

> [!NOTE] Environment
> The following setup is available in **10.2.600, EPIC06, MfgSys**

## Initial Setup
The following has been created
- A **Warehouse** with the code `BallWhse` containing
	- A **Bin** with the number `BallInput`
	- A **Bin** with the number `BallOutput`

- A **Part** with the number `RedBall`
- A **Part** with the number `BlueBall`
- A **Part** with the number `GreenBall`
> Both `BallInput` and `BallOutput` have had `BallWhse` added as a warehouse under `Sites > Warehouses` in **part maintenance**

- A **Job** with the number `2476` containing
	- A **Material** with sequence `10` for `RedBall`
	- A **Material** with sequence `20` for `BlueBall`

## Method Directives





# Software
## Code Repository

## Code Structure
- 📁`ESP8266` - The program that runs on the `ESP8266` module
- 📁`UNO` - The program that runs on the `UNO` module


## Sensors
[Laser Trip Wire](/Apps/Arduino/Arduino/LaserSensor)
[Tap Sensor](/Apps/Arduino/Arduino/TapSensor)
[Metal Detector](/Apps/Arduino/Arduino/MetalTouch)
[Light Cup](/Apps/Arduino/Arduino/LightCup)
[Avoidance](/Apps/Arduino/Arduino/Avoidance)
[MagneticSpring](/Apps/Arduino/Arduino/MagneticSpring)