Integrated Embedded System for Autonomous Metal Detection
Electronics Corporation of India Limited (ECIL) | R&D Internship Project

📌 Project Overview
This repository contains the design, firmware, and simulation assets for a remotely operated robotic vehicle engineered for high-precision metal detection. The system leverages inductive sensing technology to bridge the gap between raw analog signals and digital control logic, providing a scalable prototype for autonomous landmine detection and geological surveying.

📂 Repository Structure & File Mapping
Note: To align with professional standards, I recommend renaming your files as follows:

Plaintext
├── .assets/               # Project images and circuit diagrams for README
├── docs/
│   └── Technical_Report.pdf   <-- [Rename: Metal Detection Robot Documentation.pdf]
├── firmware/
│   ├── main.c             # System core logic and I/O initialization
│   ├── motor_control.c    # L293D driver logic and PWM signaling
│   └── sensor_input.h     # Inductive sensor threshold definitions
├── simulation/
│   ├── schematics.pdsprj  # Proteus simulation design file
│   └── circuit_layout.png # Visual representation of the hardware bus
└── README.md              # Technical documentation
🛠️ Technical Specifications
Core Logic: ARM LPC2148 (32-bit ARM7TDMI-S) and Atmel AVR architecture.

Signal Ingestion: Inductive proximity sensor with a 0–8mm detection range, optimized for up to 7cm of ground penetration.

Power & Actuation: L293D H-Bridge motor driver managing a high-torque DC gear-motor configuration.

Telemetry: UART-based Bluetooth interface for remote telemetry and command execution.

Toolchain: Keil µVision (Compiler/Debugger), Proteus (Hardware Simulation).

⚙️ Engineering Implementation
1. Register-Level Firmware Design

The firmware was architected in Embedded C, focusing on low-latency I/O response. I implemented specific bit-masking on the IO0DIR and IO0PIN registers to manage the state machine for sensor interrupts and motor actuation.

2. Signal Integrity & Validation

To ensure high-fidelity detection across varied metallic compositions (Iron, Aluminum, Copper), I developed a validation logic that filters out noise from the inductive coil, ensuring the buzzer alarm and LCD feedback trigger only upon verified material density thresholds.

🚀 Key Impacts
Accuracy: Improved signal-to-noise ratio in detection logic, enabling consistent identification of metallic objects 7cm underground.

Efficiency: Automated the data feedback loop, reducing the latency between physical detection and operator notification to near-zero.

Safety: Removed the human element from high-risk detection zones via a 15-meter stable remote control radius.
