# Mixed-Signal Embedded Control Board (STM32F407)

A custom **4-layer mixed-signal embedded control board** built around the **STM32F407VGT6**, designed in **Altium Designer** as part of a complex mixed-signal board design course.

The board combines Ethernet, dual DC-motor drivers (36 W each), a 24-bit load-cell ADC, a stereo audio DAC with digital microphone, USB/UART connectivity, and an on-board JTAG/SWD debugger on a single PCB powered from 12 V.

| | |
|---|---|
| **Document** | MSD-001, Revision V1.0 |
| **Date** | 06-10-2026 |
| **Designer** | Maulik Italiya |
| **Tool** | Altium Designer |
| **PCB** | 4-layer, approx. 1.6 mm |

---

## Block Diagram

```
                     +---------------+
   Ethernet PHY ---- |               | ---- STM32F103 debugger (JTAG/SWD)
   DP83826  (MII)    |               |
   Motor driver 1 -- |   STM32F407   | ---- CH340C USB-UART (UART)
   Motor driver 2 -- |               |
   ADS122C04 (I2C) - |               | ---- CS43L22 DAC + IMP34DT05 mic
                     +---------------+
        12 V input -> +12 V / +3.3 V / +1.8 V rails
```

---

## Key Features

| Subsystem | Implementation |
|---|---|
| **Controller** | STM32F407VGT6, 8 MHz crystal, reset switch, UART and CAN logic-level headers |
| **Ethernet** | DP83826 PHY over MII, 25 MHz crystal, RJ45 with ESD protection, status LEDs |
| **Motor control** | 2× DRV8701 gate drivers with DMHT6016LFJ-13 N-MOSFET bridges, 50 mΩ current sensing, 12 V / 3 A (36 W) per channel |
| **Analog acquisition** | ADS122C04 24-bit ADC (I²C) for load-cell measurement, with input RC filtering |
| **Audio** | CS43L22 stereo DAC (I²S), headphone/line and speaker outputs, IMP34DT05 digital MEMS microphone |
| **Debug / USB** | STM32F103C8T6 JTAG/SWD programmer and CH340C USB-to-UART bridge (USB mini-B) |
| **Power** | 12 V input, +3.3 V and +1.8 V linear regulators, reverse-polarity Schottky diodes |

### Interfaces used

MII (Ethernet) · I²C (ADC, DAC control) · I²S (audio) · PDM (microphone) · UART · JTAG/SWD · PWM, GPIO and analog input (motor drivers)

---

## Power Budget

| Load | Current | Rail |
|---|---|---|
| Motor driver 1 / 2 | 3 A each | +12 V |
| STM32F407 | 240 mA | +3.3 V |
| STM32F103 | 150 mA | +3.3 V |
| Ethernet PHY | 55 mA | +3.3 V |
| ADC, DAC, microphone | 10 mA each | +3.3 V |
| **+3.3 V total** | **475 mA** | |
| **12 V input (6.13 A + 25 % margin)** | **7.66 A** | |

> These are design-budget values from the schematic. Verify final current and thermal performance on the assembled board.

---

## PCB Stack-Up

| Layer | Function |
|---|---|
| L1 | Top signal + components |
| L2 | Solid GND plane |
| L3 | Power plane (+12 V / +3.3 V / +1.8 V, no signal routing) |
| L4 | Bottom signal + components |

Layout priorities: separate high-current motor switching from analog/audio sections, keep Ethernet routing controlled and away from noisy areas, and place decoupling capacitors close to supply pins.

---

## Documentation

| Document | Link |
|---|---|
| Electrical schematic (11 pages) | [Schematic PDF](Documentation/Schematic/Mixed-Signal-Embedded-Board-Schematic.pdf) |
| Design overview (PDF) | [Design Overview](Documentation/Design_Overview/Design_Overview.pdf) |
| Design overview (LaTeX source) | [Design_Overview.tex](Documentation/Design_Overview/Design_Overview.tex) |

### Schematic sheets

| # | Sheet | # | Sheet |
|---|---|---|---|
| 1 | Block diagram | 7 | 24-bit ADC (load cell) |
| 2 | Power budget | 8 | Stereo DAC and microphone |
| 3 | STM32F103 debugger | 9 | STM32F407 controller |
| 4 | Ethernet PHY | 10 | Motor driver 2 |
| 5 | Motor driver 1 | 11 | Power input and regulators |
| 6 | CH340C USB-UART | | |

---

## Repository Structure

```
Mixed-Signal-Board/
├── README.md
├── Documentation/
│   ├── Schematic/
│   │   └── Mixed-Signal-Embedded-Board-Schematic.pdf
│   └── Design_Overview/
│       ├── Design_Overview.tex
│       ├── Design_Overview.pdf
│       └── images/              (PCB top/bottom and 3D views)
├── PCB/                                                 
└── Manufacturing/               
```

---

## Project Status

- [x] Electrical schematic
- [x] PCB layout
- [x] Design overview document
- [x] PCB documentation (layer views, 3D renders)
- [ ] Bill of Materials
- [ ] Manufacturing files (Gerber / drill)
- [ ] Board bring-up and test results

---

## Tools

- **Altium Designer**: schematic capture and PCB layout
- **LaTeX**: design documentation

---

## Author

**Maulik Italiya**
M.Sc. Embedded Systems Design, Hochschule Bremerhaven

*This repository documents the engineering design of the board for technical and portfolio purposes.*
