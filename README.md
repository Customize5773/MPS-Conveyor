# PLC Ladder Logic for Single-Cycle Conveyor System – Haiwell AT12M0R

![IMG_20250428_121153-50](https://github.com/user-attachments/assets/8821e049-ec14-4a2b-b8c6-8ad01f5ed49e)

This project implements a **ladder logic program** for a single-cycle conveyor system using the **Haiwell AT12M0R PLC**, expanded with **2x A16XDR I/O extension modules**. Designed as an academic project within a Modular Production System (MPS) environment, it automates material handling using sensors, pneumatic cylinders, twinrod actuators, a suction cup, and indicator lights.

> Backstory : This project was created to deepen my personal understanding of the Modular Production System (MPS) Conveyor after attending a school training program on PLC-Conveyor organized by [PT. Datek Inovasi Nusantara](https://plcdedu.com/) at SMKN 1 Udanawu, Indonesia.

## 🎯 **Project Description**

**Modular Production System (MPS) Conveyor** is one of the essential modules in a modular production system designed to simulate material handling processes in production lines. This module focuses on the movement, detection, and sorting of items using conveyor systems, providing practical experience in designing and controlling industrial automation systems.

This module includes key components such as a **conveyor belt system** for material transport, **sensors** for item detection (e.g., proximity or optical sensors), and **pneumatic actuators** for pick-and-place mechanisms. Additionally, the module is controlled by **Programmable Logic Controllers (PLC)** to implement control logic, and it is equipped with **safety interlocks** to ensure safe operations.

Users of this module can learn various aspects, ranging from programming conveyor logic (such as start/stop, speed control, and item handling), integrating sensors and actuators for automation tasks, to troubleshooting common issues in conveyor systems. This module is also designed to train skills in optimizing material flow to increase production efficiency.

The system controls a conveyor belt that detects and counts incoming items using sensors. Once 3 items are detected, the conveyor stops automatically, and a pneumatic pick-and-place sequence is triggered using a twinrod actuator and suction cup. The system operates in **single-cycle mode**, requiring a manual restart for each new cycle.

The logic includes:
- Emergency stop handling
- Start/Stop control
- Counter logic for item detection
- Step-sequencing of actuators with timer delays
- Indicator lights and buzzer signals
- Safe reset of system and counters

---

## 📝 **Input / Output Table**

> File Download: [Code Input & Output.pdf]([https://github.com/Customize5773/MPS-Machine/blob/main/Code%20Input%20%26%20Output.pdf](https://github.com/Customize5773/MPS-Conveyor/blob/0799f5a12e53bcad05f74813132585c8ba16a0f7/docs/Code%20Input%20%26%20Output.pdf))

### INPUT
| Name                  | Address | Description                               |
|----------------------|---------|-------------------------------------------|
| Start PB              | X2      | Normally open pushbutton (Start)          |
| Stop PB               | X3      | Normally closed pushbutton (Stop)         |
| SC1A                  | X8      | Cylinder 1 front sensor                   |
| SC2A                  | X9      | Cylinder 2 front sensor                   |
| SC3A                  | X10     | Cylinder 3 front sensor                   |
| SC4A                  | X11     | Cylinder 4 front sensor                   |
| STW1-A                | X12     | Twinrod horizontal forward sensor         |
| STW1-B                | X13     | Twinrod horizontal backward sensor        |
| STW2-A                | X14     | Twinrod vertical up sensor                |
| STW2-B                | X15     | Twinrod vertical down sensor              |
| SC                    | X16     | Proximity sensor (metal detection)        |
| SB1                   | X17     | Item sensor 1                             |
| SB2                   | X18     | Item sensor 2                             |
| SB3                   | X19     | Item sensor 3                             |
| SB_OK                 | X20     | Sensor indicates item buffer full (3 items) |
| EMG                   | X21     | Emergency stop pushbutton                 |

### OUTPUT
| Name                  | Address | Description                               |
|----------------------|---------|-------------------------------------------|
| C1                    | Y8      | Cylinder 1 valve                          |
| C2                    | Y9      | Cylinder 2 valve                          |
| C3                    | Y10     | Cylinder 3 valve                          |
| C4                    | Y11     | Cylinder reject valve                     |
| SC                    | Y12     | Suction cup valve                         |
| CTW1A                 | Y13     | Twinrod forward valve                     |
| CTW1B                 | Y14     | Twinrod backward valve                    |
| CTW2                  | Y15     | Twinrod up/down valve                     |
| M0                    | Y16     | Motor conveyor                            |
| L1 (Red)              | Y17     | Red light (alarm)                         |
| L2 (Yellow)           | Y18     | Yellow light (EMG active)                 |
| L3 (Green)            | Y19     | Green light (system active)               |
| BZ                    | Y20     | Buzzer                                    |

---

## 🏷️ **Tag Explanation**

| Symbol | Meaning                 |
|--------|------------------------|
| X      | Digital input           |
| Y      | Digital output          |
| M      | Internal memory bit     |
| T      | Timer                   |
| C      | Counter                 |

---

## 📝 **Process Overview**

1. **Start button pressed (X2)** → System active → motor conveyor (Y16) runs → green light (Y19) ON.
2. Sensors **SB1, SB2, SB3 (X17–X19)** increment counter **C0**.
3. When **C0 reaches 3**, conveyor stops (Y16 OFF), system flags **M1** to indicate "ready to pick".
4. A step-by-step actuator sequence starts:
   - Twinrod lowers (Y15) → suction cup activates (Y12) → twinrod lifts (Y15).
   - Twinrod moves forward (Y13) → lowers (Y15) → suction cup releases (Y12 OFF).
   - Twinrod lifts (Y15) → returns backward (Y14).
5. Each step delayed 1 second using timers **T0–T6**.
6. System resets counters, flags, indicators → returns to idle state.
7. Emergency stop (X21) interrupts all processes, activates yellow light (Y18), and if items were full, also triggers red light (Y17) and buzzer (Y20).

---

## 🏗️ **Hardware Setup**

The system uses:
- **Haiwell AT12M0R PLC** (12 digital inputs, 8 relay outputs)
- Expanded with **2x Haiwell A16XDR extension modules** (adding 32 digital inputs and 32 relay outputs total)
- **5/2 single solenoid pneumatic valves** for cylinder control
- **Twinrod double-acting pneumatic cylinder**
- **Proximity inductive sensor (SC)** for metal detection
- **Magnetic reed switches** for position sensing (SB1, SB2, SB3, STW1-A/B, STW2-A/B)
- Power supply: **24VDC**
- **Sink input configuration**: sensors wired with common 0V
- **Actuators connected via relay interposing** to protect PLC outputs

---

## 🖼️ **Ladder Logic Diagram**

A complete ladder logic diagram is provided in [LadderLogic_MPS_Haiwell](https://github.com/Customize5773/MPS-Conveyor/blob/fb20947a3d5d9922143b40772cc2d211c2b0303e/Haiwell%20Program/Ladder-Logic.md) in this repository.

---

## ⚠️ **Notes**

- Verify sensor wiring and actuator current requirements before deployment.
- Delay timers are set to **1 second (K1000)**; adjust as needed.
- System designed for **single-cycle operation**; press Start again for each new cycle.
- Ensure correct I/O mapping if using additional expansion modules.

---

## 📄 **License**

This project is open for academic and educational use.

---
