---
title: Laser Sensor
description: 
published: true
date: 2024-01-19T15:08:10.633Z
tags: 
editor: markdown
dateCreated: 2023-04-27T13:39:27.344Z
---

# Laser Sensor
## Explanation

Laser Emit allows for a trip wire to be created. The Laser must be faced towards the photoresitor. When the beam is broken then the buzzer will sound.

Could be useful for seeing how many balls pass a certain section. However, it cannot distinguish between different objects.

## Components needed

- Arduino
- Passive Buzzer
- 10K ohm resistor (Brown, Black, Black, Red, Brown)
- Photoresistor
- Laser Emit





## Images
![20230427_143307.jpg](/20230427_143307.jpg)
![20230427_143301.jpg](/20230427_143301.jpg)
![20230427_143304.jpg](/20230427_143304.jpg)

![image_2023-04-27_143615521.png](/image_2023-04-27_143615521.png)

## Code

```C++ 
int ldr = 0; //analog pin to which LDR is connected
int ldr_value = 0; //variable to store LDR values
const int buzzer = 9;

void setup() {
  Serial.begin(9600); //start the serial monitor
}

void loop() {
  ldr_value = analogRead(ldr); //reads the LDR values
  Serial.println(ldr_value); //prints the LDR values to serial monitor
  delay(100); //wait

  if (ldr_value > 100) {
    tone(buzzer, 1000);
    delay(1000); // 3 seconds of beeping to tell you the trip wire has been broken
  } else {
    noTone(buzzer);
  }

} 
```