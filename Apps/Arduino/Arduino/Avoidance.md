---
title: Avoidance
description: 
published: true
date: 2024-01-19T15:08:06.839Z
tags: 
editor: markdown
dateCreated: 2023-05-18T08:47:20.031Z
---

# Avoidance
## Explanation
This sensor uses IR recievers and emitters to be able to detect if an object is in it's path. It might be reliable after a lot of configuring but at this moment it just works slightly.

Could be useful as a back up to another sensor that detects the amount of balls going through a point
## Components Needed
- Uno
- Wires
- Avoidance Sensor
## Images
![image_2023-05-18_094624942.png](/image_2023-05-18_094624942.png)
![image_2023-05-18_094651971.png](/image_2023-05-18_094651971.png)
## Code
``` C++
/*
 * Created by ArduinoGetStarted.com
 *
 * This example code is in the public domain
 *
 * Tutorial page: https://arduinogetstarted.com/tutorials/arduino-infrared-obstacle-avoidance-sensor
 */

// Arduino's pin connected to OUT pin of IR obstacle avoidance sensor
const int SENSOR_PIN = 8;

void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  // initialize the Arduino's pin as aninput
  pinMode(SENSOR_PIN, INPUT);
}

void loop() {
  // read the state of the the input pin:
  int state = digitalRead(SENSOR_PIN);

  if (state == LOW)
    Serial.println("The obstacle is present");
  else
    Serial.println("The obstacle is NOT present");

  delay(100);
}

```