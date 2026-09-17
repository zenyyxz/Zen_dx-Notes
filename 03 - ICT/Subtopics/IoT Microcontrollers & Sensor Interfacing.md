---
title: IoT Microcontrollers & Sensor Interfacing
subject: AL ICT
subtopic: IoT & Embedded Systems
tags:
  - AL-ICT
  - Subtopic
  - Arduino
  - IoT
  - Sensors
  - Microcontrollers
---
# Subtopic: IoT Microcontrollers & Sensor Interfacing Guide

> [!ABSTRACT] Core Focus
> Arduino hardware architecture, digital vs analog pin functions, C/C++ code structure (`setup()` and `loop()`), and wiring logic for sensors and actuators.

---
## 1. Arduino Board Hardware Overview

- **Microcontroller Chip**: ATmega328P (8-bit AVR RISC microcontroller).
- **Digital Pins (Pins 0 - 13)**: Can be configured as `INPUT` or `OUTPUT`. Pins marked with `~` support Pulse Width Modulation (PWM - simulated analog output).
- **Analog Input Pins (Pins A0 - A5)**: Reads analog voltage ($0 - 5V$) using built-in 10-bit Analog-to-Digital Converter (ADC), returning values from $0$ to $1023$.
- **Power Pins**: `5V`, `3.3V`, `GND` (Ground), `VIN`.

---
## 2. Standard Arduino C/C++ Program Structure

```cpp
// 1. Pin Definitions & Constants
const int LED_PIN = 13;
const int LDR_PIN = A0;

void setup() {
    // Runs once when board powers up
    pinMode(LED_PIN, OUTPUT);
    Serial.begin(9600); // Initialize serial communication at 9600 baud
}

void loop() {
    // Runs continuously in an infinite loop
    int sensorValue = analogRead(LDR_PIN); // Read light level (0-1023)
    Serial.print("LDR Value: ");
    Serial.println(sensorValue);

    if (sensorValue < 300) {
        // Dark environment -> Turn ON Light
        digitalWrite(LED_PIN, HIGH);
    } else {
        // Bright environment -> Turn OFF Light
        digitalWrite(LED_PIN, LOW);
    }

    delay(1000); // Delay 1 second (1000 ms)
}
```

---
## 3. Key Interfacing Functions Summary

- `pinMode(pin, MODE)`: Sets pin mode to `INPUT` or `OUTPUT`.
- `digitalWrite(pin, VALUE)`: Outputs `HIGH` (5V) or `LOW` (0V) to digital pin.
- `digitalRead(pin)`: Reads digital value (`HIGH` or `LOW`) from digital input pin.
- `analogRead(pin)`: Reads analog voltage on pins A0-A5 (returns integer $0 - 1023$).
- `analogWrite(pin, value)`: Generates PWM signal on `~` pins (accepts integer $0 - 255$).