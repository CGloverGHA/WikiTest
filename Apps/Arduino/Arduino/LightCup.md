---
title: Light Cup
description: 
published: true
date: 2024-01-19T15:08:14.307Z
tags: 
editor: markdown
dateCreated: 2023-05-18T08:25:18.646Z
---

# Light Cup
## Explanation

A Light Cup needs to sensors. They operate using mercury switches. When connected together the light can appear to be flowing from one cup to another. This could be used in the seasaw for ascetics however the code would need to be reviewed as at this moment in time it can be slow.

## Components Needed
- Uno
- 2 x Light Cup Sensors
- Wires
## Images
![image_2023-05-18_092435922.png](/image_2023-05-18_092435922.png)
## Code

```C++
int ledPinA = 9;
int switchPinA = 8;
int switchStateA = 0;
int ledPinB = 6;
int switchPinB = 7;
int switchStateB = 0;
int brightness   = 0;
void setup() 
{
  pinMode(ledPinA, OUTPUT); 
  pinMode(ledPinB, OUTPUT);  
  pinMode(switchPinA, INPUT); 
  pinMode(switchPinB, INPUT);
}
void loop() 
{
  switchStateA = digitalRead(switchPinA);
  if (switchStateA == HIGH && brightness != 255)
  { 
   brightness ++;
  } 
  switchStateB = digitalRead(switchPinB);
  if (switchStateB == HIGH && brightness != 0)
  { 
   brightness --;
  } 
  analogWrite(ledPinA, brightness);  //  A slow fade out
  analogWrite(ledPinB, 255 - brightness);  // B slow bright up
  delay(20);
}
```