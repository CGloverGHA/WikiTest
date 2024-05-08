---
title: TapSensor
description: 
published: true
date: 2024-01-19T15:08:25.065Z
tags: 
editor: markdown
dateCreated: 2023-04-27T14:23:31.279Z
---

# TapSensor


## Explanation
Tap Sensor detects when it vibrates. This has been created however, it is very circumstantial when it decides to work. Most likely will not be useful unless the balls in the "Factory" fall a decent distance or are heavy each to trigger it.

## Components Needed
- Tap Sensor
- 1k ohm resistor
- Led
- Arduino

## Images
![image_2023-04-27_152223550.png](/image_2023-04-27_152223550.png)
![image_2023-04-27_152246513.png](/image_2023-04-27_152246513.png)


## Code

```C++
const int knockPin = 8;
const int ledPin = 7;

int knockVal = HIGH;
boolean knockAlarm = false;
unsigned long prevKnockTime;


int knockAlarmTime = 100;


void setup ()
{
  Serial.begin(9600);  
  pinMode (ledPin, OUTPUT) ;
  pinMode (knockPin, INPUT) ;
}
void loop ()
{
  knockVal = digitalRead (knockPin) ;
  
  if (knockVal == LOW)
  {
  
    prevKnockTime = millis();
    
    if (!knockAlarm)
    {
      Serial.println("KNOCK, KNOCK");
      digitalWrite(ledPin,HIGH);
      knockAlarm = true;
      delay(1000);
    }
  }
  else
  {
    if( (millis()-prevKnockTime) > knockAlarmTime &&  knockAlarm)
    {
      digitalWrite(ledPin,LOW);
      Serial.println("No Knocks");
      knockAlarm = false;
    }
  }
}
```
