

# Integrated Embedded System for Autonomous Metal Detection

**R&D Project | Electronics Corporation of India Limited (ECIL)**

## 📌 Executive Summary

Engineered a sensor-integrated robotic platform designed for real-time metallic anomaly detection in high-risk environments. This project focuses on bridging raw analog inductive signals with digital control logic to automate hazardous material sweeps. Developed under the **Computer Education Division of ECIL (Department of Atomic Energy)**, the system prioritizes signal integrity, low-latency interrupt handling, and remote telemetry.

## 📂 Repository Structure

*Note: Due to the proprietary nature of the R&D environment, source firmware is represented via architectural logic below. Full engineering findings are available in the technical report.*

```text
├── docs/
│   └── Technical_Report.pdf     # Primary Engineering Specs & R&D findings
├── simulation/
│   ├── schematic_view.png       # Circuit trace and bus configuration
│   └── logic_flowchart.png      # Firmware state-machine visualization
└── README.md                    # System architecture and technical summary

```

## 🛠️ Engineering Stack & Specifications

* **Core Logic:** ARM LPC2148 (32-bit ARM7TDMI-S) / Atmel AVR Architecture.
* **Sensor Fusion:** Inductive proximity sensing unit (Range: 0–8mm; Ground Penetration: 5–7cm).
* **Actuation:** Dual L293D H-Bridge drivers managing 4x High-Torque DC gear motors.
* **Telemetry:** UART-based HC-05 Bluetooth module (Serial Port Profile).
* **Toolchain:** Keil µVision (C-Compiler), Proteus (Hardware Simulation).

## 🧩 System Architecture

The system utilizes a **Hardware-Interrupt Driven** model to ensure safety-critical responses to sensor data.

### 1. Signal Acquisition & Processing

The inductive coil generates an electromagnetic field; the presence of metal (Fe, Al, Cu) induces eddy currents, shifting the oscillator frequency. This frequency shift is captured by the MCU, which compares the input against a pre-calibrated noise floor to filter out environmental interference from mineralized soil.

### 2. Firmware Logic (High-Level)

The control logic was architected in **Embedded C**, utilizing direct register manipulation for high-speed I/O response:

* **Bit-Masking:** Used on `IO0DIR` and `IO0PIN` registers to manage the state machine for sensor interrupts.
* **Prioritization:** The sensor feedback loop is mapped to a high-priority hardware interrupt; upon detection, all PWM signals to the L293D drivers are instantly pulled `LOW` to halt movement.

## ⚠️ Engineering Constraints & Design Choices

* **EMI Mitigation:** Integrated software-level debouncing and physical separation of the inductive coil from the DC motor housings to minimize electromagnetic interference.
* **Power Optimization:** Designed a distributed power rail to support the high current draw of the 4-motor chassis without causing voltage drops to the MCU.
* **Material Specificity:** Optimized detection thresholds for three distinct metallic profiles: Iron, Aluminum, and Copper, as documented in the [Technical Report](https://www.google.com/search?q=./docs/Technical_Report.pdf).

## 🚀 Key Impacts

* **Precision:** Achieved consistent identification of sub-surface metallic objects at a depth of **7cm**.
* **Operational Safety:** Eliminated manual risk by transitioning detection to a remotely operated robotic platform with a **15-meter stable control radius**.
* **Performance:** Achieved near-zero millisecond latency between sensor triggering and operator notification via hardware-level interrupts.

