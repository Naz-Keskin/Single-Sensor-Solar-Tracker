# Single-Sensor Solar Tracking System (Sweep Algorithm)

An open-source hardware (OSHW) project demonstrating active solar tracking. Unlike traditional dual-sensor (comparator) setups, this system utilizes a single Light Dependent Resistor (LDR) combined with a software-defined "sweep-and-lock" algorithm to find the optimal light angle.

## System Architecture

The project integrates mechanical actuation with environmental sensing, driven by an Arduino Uno.

* **Actuator:** SG90 Micro Servo (Provides 180° pan movement).
* **Sensor:** Single LDR configured as a voltage divider with a 10kΩ resistor.
* **Mounting:** A rapid-prototyped mini breadboard acts as the dynamic sensor platform mounted directly onto the servo spline.

## Software Logic: The Sweep Algorithm

To compensate for the lack of a second sensor, the system employs a radar-like scanning mechanism:
1.  **Sweep Phase:** The servo incrementally sweeps from 0° to 180°. At each step, the microcontroller samples the analog light intensity.
2.  **Data Acquisition:** The system dynamically compares current readings against the historical maximum, storing the peak value and its corresponding angle in memory.
3.  **Lock Phase:** Upon completing the sweep, the algorithm commands the actuator to return directly to the calculated optimal angle, maximizing solar exposure. The system holds this position before initiating the next scheduled sweep.

## Academic Context
Developed by Naz | TOBB ETU - Electrical and Electronics Engineering.
This project highlights the ability to solve hardware limitations (single sensor) through intelligent software design (search algorithms and memory allocation) in embedded systems.

## Physical Setup

![System Tracker General](./docs/tracker_general.jpg)
*Şekil 2: Servo motor üzerine monte edilmiş mini breadboard ve LDR sensör düzeneğinin genel görünümü.*

![LDR Circuit Detail](ldr-detail.jpg)
*Şekil 3: LDR gerilim bölücü devresinin yakından görünümü.*
