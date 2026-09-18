---
title: Lesson 11 - Internet of Things & Embedded Systems
subject: AL ICT
unit: 11
competency: Explores IoT and identify the building blocks of embedded systems to develop simple applications
tags:
  - AL-ICT
  - Lesson-11
  - IoT
  - EmbeddedSystems
  - Microcontrollers
  - Sensors
  - Flashcards
---
# :LiBook: Lesson 11: Internet of Things & Embedded Systems

> [!ABSTRACT] Syllabus Scope (NIE Teacher's Guide)
> - Embedded Systems concept & Microprocessor vs Microcontroller
> - Sensors (Inputs) vs Actuators (Outputs)
> - Arduino / Microcontroller hardware components & I/O pins
> - IoT Architecture Layers (Sensing, Network, Cloud, Application)
> - Real-world IoT Applications (Smart Home, Agriculture, Industry)

---
## 1. Embedded Systems & Microcontrollers

An **Embedded System** is a specialized computer system designed to perform dedicated functions within a larger mechanical or electrical system.

| Parameter        | Microprocessor (e.g., Intel i7)                                  | Microcontroller (e.g., ATmega328P / Arduino)                                            |
| :--------------- | :--------------------------------------------------------------- | :-------------------------------------------------------------------------------------- |
| **Components**   | Contains CPU only; RAM, ROM, I/O ports are connected externally. | Contains CPU, RAM, ROM/Flash, Timers, and I/O ports integrated on a **single IC chip**. |
| **Cost & Power** | Expensive, high power consumption.                               | Inexpensive, ultra-low power consumption.                                               |
| **Application**  | General-purpose computing (PCs, Laptops).                        | Dedicated embedded tasks (Washing machines, IoT nodes).                                 |

---
## 2. Sensors and Actuators

- **Sensors (Input Devices)**: Convert physical signals (temperature, light, distance) into electrical signals.
  - **Analog Sensors**: Output continuous voltage (e.g., LDR light sensor, LM35 temperature sensor).
  - **Digital Sensors**: Output discrete high/low signals or digital pulses (e.g., PIR motion sensor, Ultrasonic HC-SR04).
- **Actuators (Output Devices)**: Convert electrical control signals into physical actions (e.g., Relay module, Servo motor, DC motor, LED, Buzzer).

> [!INFO] Deep Dive Note
> For Arduino code syntax (`pinMode`, `digitalRead`, `digitalWrite`, `analogRead`), pin layouts, and sensor circuit wiring diagrams, read: [[Subtopics/IoT Microcontrollers & Sensor Interfacing|IoT Microcontrollers & Sensor Interfacing Guide]].

---
## 3. IoT Architecture 4-Layer Model

1. **Sensing / Perception Layer**: Sensors, actuators, microcontrollers collecting environment data.
2. **Network / Gateway Layer**: Transmits data wirelessly or via wire (Wi-Fi, Bluetooth, Zigbee, LoRa, 4G/5G).
3. **Service / Cloud Layer**: Data storage, MQTT brokers, analytics processing on cloud servers.
4. **Application Layer**: User interface apps (Smart Home mobile apps, Smart Farming dashboards).

---
## :LiRocket: Flashcards (Spaced Repetition)

#flashcards

What is an Embedded System? :: A specialized computer system designed to perform dedicated control functions within a larger mechanical or electrical system.

What is the main structural difference between a Microprocessor and a Microcontroller? :: A Microprocessor contains only the CPU; a Microcontroller integrates the CPU, RAM, ROM/Flash, Timers, and I/O ports on a single silicon chip.

What is the difference between a Sensor and an Actuator? :: A Sensor converts physical parameters into electrical signals (input); an Actuator converts electrical signals into physical actions (output).

Name 2 Analog Sensors and 2 Digital Sensors used in IoT. :: Analog: LDR (Light Dependent Resistor), LM35 (Temperature); Digital: PIR (Motion Sensor), Ultrasonic (HC-SR04).
<!--SR:!2026-09-28,11,270-->

List the 4 layers of the IoT Architecture Model. :: 1. Sensing/Perception Layer, 2. Network/Gateway Layer, 3. Service/Cloud Layer, 4. Application Layer.
<!--SR:!2026-08-07,2,230-->