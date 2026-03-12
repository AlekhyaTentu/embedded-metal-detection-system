
# Integrated Embedded System for Autonomous Metal Detection

**R&D Project | Electronics Corporation of India Limited (ECIL)**

## 📌 Technical Overview

Engineered a sensor-integrated robotic vehicle designed for real-time metallic anomaly detection in high-risk environments. The system bridges raw analog inductive signals with digital control logic to automate landmine detection and geological surveying. Developed under the Computer Education Division of ECIL (Department of Atomic Energy), the project focuses on signal integrity, low-latency feedback, and remote telemetry.

## 📂 Repository Structure

```text
├── docs/
│   └── Technical_Report.pdf     # Full engineering documentation and R&D findings
├── firmware/
│   ├── main.c                   # System core logic and I/O initialization
│   ├── motor_control.c          # L293D driver logic and PWM signaling
│   └── sensor_input.h           # Inductive sensor threshold and interrupt definitions
├── simulation/
│   ├── schematics.pdsprj        # Proteus hardware simulation design file
│   └── hardware_layout.png      # Visual trace and bus configuration
└── README.md                    # Technical specifications and project summary

```

## 🛠️ Engineering Stack & Specifications

* **Microcontroller:** ARM LPC2148 (32-bit ARM7TDMI-S) / Atmel AVR Architecture.
* **Sensor Fusion:** Inductive proximity sensing unit (Range: 0–8mm; Ground Penetration: 5–7cm).
* **Actuation:** Dual L293D H-Bridge drivers managing 4x High-Torque DC gear motors.
* **Telemetry:** UART-based HC-05 Bluetooth module for remote instruction execution.
* **Toolchain:** Keil µVision (C-Compiler), Proteus (Hardware Simulation), Arduino IDE.

## ⚙️ Technical Implementation

### 1. Register-Level Firmware Design

The control firmware was architected in **Embedded C**, utilizing direct register manipulation for high-speed I/O. I implemented bit-masking on the `IO0DIR` and `IO0PIN` registers to manage the state machine for sensor interrupts and motor actuation, ensuring minimal instruction cycle latency.

### 2. Signal Integrity & Detection Logic

To ensure high-fidelity detection across varied metallic compositions (Iron, Aluminum, Copper), the logic filters coil induction noise. The system validates signal density thresholds before triggering the piezoelectric buzzer and 16x2 LCD dot-matrix feedback.

### 3. Remote Telemetry

Implemented a wireless control radius of 15 meters using Bluetooth SPP (Serial Port Profile), allowing for safe operator distance during hazardous material sweep operations.

## 🚀 Key Impacts

* **Accuracy:** Optimized signal-to-noise ratios to enable consistent identification of sub-surface metallic objects at a depth of 7cm.
* **Operational Safety:** Eliminated manual risk by transitioning detection to a remotely operated robotic platform.
* **Latency:** Achieved near-zero millisecond latency between sensor triggering and operator notification via hardware interrupts.

---

