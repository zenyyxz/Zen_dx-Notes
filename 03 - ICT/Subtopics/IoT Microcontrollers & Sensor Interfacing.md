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

---

## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

Which microcontroller is used on the classic Arduino Uno? :: The ATmega328P, an 8-bit AVR RISC microcontroller.

How many digital and analog pins does the classic Arduino Uno expose? :: 14 digital pins (0–13) and 6 analog input pins (A0–A5).

What is the difference between digital and analog pins on Arduino? :: Digital pins read/write HIGH or LOW; analog input pins read a variable voltage through the ADC.

Which digital pins support PWM? :: Pins marked with `~`; `analogWrite()` works only on those pins.

How does the Arduino ADC represent an analog voltage? :: As a 10-bit value from 0 to 1023.

What voltage range do Arduino analog inputs A0–A5 measure on a 5V board? :: 0V to 5V.

What is the purpose of `setup()`? :: It runs once at power-up or reset to initialise pins, Serial and other settings.

What is the purpose of `loop()`? :: It runs continuously after `setup()` and contains the main control logic.

What does `pinMode(pin, MODE)` do? :: Configures a digital pin as `INPUT` or `OUTPUT`.

What do `digitalWrite(pin, HIGH)` and `LOW` mean? :: HIGH outputs 5V (on); LOW outputs 0V (off).

What does `digitalRead(pin)` return? :: The digital state: `HIGH` or `LOW`.

What does `analogRead(pin)` return? :: An integer from 0 to 1023 representing the analog voltage.

What does `analogWrite(pin, value)` do, and what is its value range? :: It generates a PWM signal on a `~` pin; the value range is 0–255.

What is PWM used for? :: To simulate analog output by rapidly switching a digital pin on and off — for example, LED brightness or motor speed.

What does `Serial.begin(9600)` do? :: Starts serial communication at 9600 baud for debugging or sending data.

What does `delay(1000)` do? :: Pauses the program for 1000 milliseconds (1 second).

What is the role of a microcontroller in an IoT device? :: It reads sensors, processes data, controls actuators and communicates with other devices.

In the note's LDR example, why does a low sensor value turn on the LED? :: The circuit is wired so lower readings mean a darker environment; the code switches the LED on when the value is below 300.