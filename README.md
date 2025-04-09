# 🤖 Gesture-Controlled Wheelchair System

This project demonstrates a gesture-controlled robotic wheelchair using two Arduino Uno microcontrollers, an MPU6050 accelerometer and gyroscope module, Bluetooth communication, and safety features powered by ultrasonic and IR sensors. The system is designed for real-time control of a motorized platform using intuitive hand movements.

> 📘 This code is part of a Master’s thesis submitted to The University of Texas Permian Basin (UTPB) titled **"A Real-Time Embedded System for Gesture-Based Wheelchair Control with Integrated Safety Mechanisms."**

---

## 🚀 Features

- 🎮 **Gesture-based control** using MPU6050 (tilt forward/back/left/right to control wheelchair)
- 📡 **Bluetooth communication** between master (controller) and slave (wheelchair)
- ⚠️ **Obstacle detection** using ultrasonic sensor (auto-stop if obstacle ≤ 10 cm)
- 🕳️ **Drop-off detection** using downward-facing IR sensors (auto-stop if surface reading > 1000)
- 🔧 Modular and extensible Arduino code with clean separation of logic

---

## 🧱 Hardware Used

| Component                  | Qty |
|---------------------------|-----|
| Arduino Uno R3            | 1  |
| Arduino Nano              | 1  |
| MPU6050 (GY-521)          | 1   |
| HC-05 Bluetooth Module    | 2   |
| Ultrasonic Sensor (HC-SR04)| 1   |
| Analog IR Sensors         | 2   |
| L298N Motor Driver Shield | 1   |
| 12V Battery Pack          | 1   |
| DC Motors + Wheels        | 2   |
| Caster Wheel              | 1   |
| Chassis Frame             | 1   |

> All components were purchased from **Amazon**, chosen for their affordability and reliable community reviews.

---

## 🔌 Wiring Overview

### Master (Gesture Controller)
- MPU6050 → SDA to A4, SCL to A5, VCC to 3.3V, GND to GND
- HC-05 → TX to Pin 2, RX to Pin 3 (via voltage divider), VCC to 5V

### Slave (Wheelchair)
- HC-05 → TX to Pin 2, RX to Pin 3 (via voltage divider)
- Ultrasonic → Trigger & Echo connected to Pin 7 (single-pin mode)
- IR Front Left → A3, IR Front Right → A2
- Motor driver:
  - PWM_A → Pin 3
  - PWM_B → Pin 11
  - DIR_A → Pin 12
  - DIR_B → Pin 13

---

## 🧠 How It Works

1. The gesture controller reads tilt values using the MPU6050 and sends a direction command (`F`, `B`, `L`, `R`, `S`) via Bluetooth to the slave unit.
2. The wheelchair receives commands and executes motor movements accordingly.
3. If an object is detected ≤ 10 cm in front or if the IR sensor reads > 1000 (indicating a drop-off), the wheelchair immediately stops to ensure safety.

---

