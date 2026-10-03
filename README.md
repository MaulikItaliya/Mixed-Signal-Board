# Mixed-Signal Embedded Control Board

A custom 4-layer mixed-signal embedded control board designed around the **STM32F407** microcontroller.

The board integrates digital communication, analog signal processing, USB/UART connectivity, and external peripheral interfaces on a single PCB.

## Project Overview

This project covers the electrical and PCB design of a custom embedded control board, including the schematic design, component selection, power architecture, signal interfaces, and mixed-signal PCB layout.

The current repository contains the electrical schematic documentation. PCB layout and manufacturing documentation will be added separately.

## Key Features

- STM32F407 microcontroller
- 4-layer PCB
- Ethernet interface
- USB-UART interface
- External ADC
- DAC
- Audio / microphone circuitry
- I²C communication
- SPI communication
- Power supply and regulation circuitry
- Mixed-signal analog and digital design

## Hardware Design

The board was designed with consideration for:

- Digital and analog signal integrity
- Power distribution and decoupling
- Grounding and return-current paths
- Component placement
- PCB routing
- Interface connectivity
- Manufacturability

## Design Tools

- **Altium Designer** — Schematic and PCB design
- **STM32F407** — Main microcontroller

## Repository Contents

```text
mixed-signal-embedded-board/
│
├── README.md
│
└── Documentation/
    └── Schematic/
        └── Mixed-Signal-Embedded-Board-Schematic.pdf
```

### Schematic

The schematic documentation contains **11 pages** covering the electrical design of the complete board.

[View Schematic](Documentation/Schematic/Mixed-Signal-Embedded-Board-Schematic.pdf)

## Project Status

- [x] Electrical schematic completed
- [x] PCB design completed
- [ ] PCB documentation
- [ ] Manufacturing documentation
- [ ] Bill of Materials
- [ ] Additional project documentation

## Author

**Maulik Italiya**

M.Sc. Embedded Systems Design  
Electronics & Communication Engineering

---

*This repository documents the engineering design and development of the board for technical and portfolio purposes.*
