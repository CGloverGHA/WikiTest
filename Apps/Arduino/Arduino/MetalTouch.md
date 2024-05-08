---
title: Metal Touch
description: 
published: true
date: 2024-01-19T15:08:21.504Z
tags: 
editor: markdown
dateCreated: 2023-04-27T15:00:29.658Z
---

# Metal Touch

## Explanation
Metal touch is able to detect if an object can conduct electricity however, after testing it has shown to not be the most reliable source of information and when it was the object has to sit on the sensor for a while and therefore it is not the best option for us to use.

## Components
- Arduino
- Metal Touch Sensor

## Images
![image_2023-04-27_154744380.png](/image_2023-04-27_154744380.png)
## Code

```C++
int digitalPin = 7;   // KY-036 digital interface
int analogPin = A0;   // KY-036 analog interface
int ledPin = 13;      // Arduino LED pin
int digitalVal;       // digital readings
int analogVal;        // analog readings
void setup()
{
  pinMode(digitalPin,INPUT); 
  pinMode(analogPin, INPUT);
  pinMode(ledPin,OUTPUT);      
  Serial.begin(9600);
}
void loop()
{
  // Read the digital inteface
  digitalVal = digitalRead(digitalPin); 
  
  if(digitalVal == HIGH) 
  {
    digitalWrite(ledPin, HIGH); // Turn ON Arduino's LED
  }
  else
  {
    digitalWrite(ledPin, LOW);  // Turn OFF Arduino's LED
  }
  // Read analog interface
  analogVal = analogRead(analogPin);
  Serial.println(analogVal);  // Print analog value to serial
  delay(100);
}
```

## Website
[Website](https://arduinomodules.info/ky-036-metal-touch-sensor-module/)