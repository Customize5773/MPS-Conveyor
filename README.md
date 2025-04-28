# Modular Production System (MPS) with Siemens S7-300

## Overview

This repository documents the Modular Production System (MPS) concept and its application using Siemens S7-300 PLC.  
It includes both theoretical explanations and practical project examples, aiming to assist developers, engineers, and technical students in understanding, designing, assembling, and programming an MPS Distribution Station.

---

## Table of Contents
- [About MPS](#about-mps)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Learning Modules](#learning-modules)
- [Contributing](#contributing)
- [License](#license)

---

## About MPS

The **Modular Production System (MPS)** is a training platform simulating industrial production processes through modular stations controlled by PLCs.  
Each station integrates pneumatic, electrical, and mechanical components, providing hands-on learning experiences for:
- Industrial automation
- Mechatronics
- Robotics control systems

This repository focuses on the **Distribution Station** using:
- Pneumatic actuators
- Electrical sensors
- Siemens S7-300 PLC
- SIMATIC Step 7 software for programming

---

## Project Structure

```
📁 docs/
    📄 Theory and Design Guide.pdf
📁 plc/
    📄 MPS_Distribution_Station_S7-300_Project.s7p
📁 images/
    📄 schematic_diagram.png
📄 README.md
```

- `docs/` — Learning materials and technical references.
- `plc/` — Sample PLC project files (compatible with Siemens Step 7).
- `images/` — Diagrams and visual supports.

---

## Installation

To work with the project:

1. Install **Siemens SIMATIC Step 7** software (version compatible with S7-300).
2. (Optional) Install **PLCSIM** for simulation without physical hardware.
3. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/mps-s7-300.git
   ```
4. Open the `.s7p` project file via SIMATIC Manager.

---

## Usage

### Running the Example Program

1. Open **SIMATIC Manager**.
2. Load the `MPS_Distribution_Station_S7-300_Project.s7p`.
3. Configure hardware setup if needed (matching your real PLC station).
4. Download the program to the PLC or run a simulation via PLCSIM.
5. Monitor the operation of:
   - Stack Magazine
   - Changer Arm
   - Pneumatic Handling System
6. Test manual and automatic modes for Distribution Station tasks.

### Sample Control Logic
- **Logical AND / OR control**
- **Timer functions (On-Delay, Off-Delay)**
- **Sequential handling (pick-and-place operations)**

---

### Screenshots and Simulations

| MPS System Overview | Simulation Animation |
| :------------------: | :------------------: |
| ![MPS Setup](./images/mps_setup.png) | ![Simulation GIF](./images/mps_simulation.gif) |

- **Left**: Modular Production System Distribution Station physical setup.
- **Right**: Simulation of automated stack magazine to changer arm sequence.

> 📌 Make sure to replace `mps_setup.png` and `mps_simulation.gif` with your actual images inside the `images/` folder.

---

## Learning Modules

- **Module 1**: Basic PLC Programming (ladder logic, I/O management)
- **Module 2**: MPS Distribution Station Design
- **Module 3**: Mechanical Assembly and Wiring
- **Module 4**: Commissioning and Troubleshooting
- **Module 5**: Full Automation Cycle Programming

Each module combines theoretical foundations and step-by-step practical tasks.

---

## Contributing

Feel free to contribute by:
- Improving the learning documentation
- Adding new MPS station examples
- Sharing better simulation models

**Pull requests** are welcome!

---

## License

_This project currently has no license. License information will be updated later._

---
