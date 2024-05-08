---
title: Magnetic Spring
description: 
published: true
date: 2024-01-19T15:08:17.932Z
tags: 
editor: markdown
dateCreated: 2023-05-18T09:20:25.594Z
---

# Magnetic Spring
## Explanation
Can detect magnetic fields in the area with good accuracy. Only issue with this sensor is that magnetic balls would need to be sourced and they would have to be checked to see that they don't get stuck. It is also pretty fast, would easily be able to detect a moving ball.
## Components
- Magnetic Spring
- Wires
- Uno
## Images
![image_2023-05-18_101937657.png](/image_2023-05-18_101937657.png)
## Code
```C++
int led = 13; // define the LED pin
int digitalPin = 3; // KY-025 digital interface
int analogPin = A0; // KY-025 analog interface
int digitalVal; // digital readings
int analogVal; //analog readings
void setup()
{
  pinMode(led, OUTPUT);
  pinMode(digitalPin, INPUT);
  //pinMode(analogPin, OUTPUT);
  Serial.begin(9600);
}
void loop()
{
  // Read the digital interface
  digitalVal = digitalRead(digitalPin); 
  if(digitalVal == HIGH) // if magnetic field is detected
  {
    digitalWrite(led, HIGH); // turn ON Arduino's LED
  }
  else
  {
    digitalWrite(led, LOW); // turn OFF Arduino's LED
  }
  // Read the analog interface
  analogVal = analogRead(analogPin); 
  Serial.println(analogVal); // print analog value to serial
  delay(10);
}
```