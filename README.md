# ESP32 CAN Shield

A compact ESP32 expansion shield designed to provide reliable and protected CAN bus communication for automotive and industrial applications. The shield integrates a high-speed CAN transceiver, automotive input protection, onboard buck converter, status LEDs, and an ESP32-compatible header for seamless CAN interfacing using the ESP32's built-in TWAI (CAN) controller.

---

## Overview

This project implements a custom ESP32 CAN Shield intended for applications requiring robust communication over Controller Area Network (CAN). The board accepts an automotive battery input, converts it to a regulated 3.3 V supply, interfaces directly with an ESP32 development board, and provides protection against common automotive electrical transients.

The hardware has been designed in KiCad with emphasis on simplicity, reliability, and ease of integration with ESP32-based embedded systems.

---

## Features

- ESP32 compatible shield interface
- SN65HVD230 3.3 V CAN transceiver
- Native support for ESP32 TWAI (CAN) peripheral
- Wide input automotive power stage
- TPS5435A synchronous buck converter
- CAN bus termination resistor (120 Ω)
- CANH/CANL ESD & surge protection
- Reverse polarity / over-voltage protection using Zener protection stage
- Automotive fuse protection
- Dual status LEDs
- Compact two-layer PCB
- Designed using KiCad

---

## Hardware Architecture

```
Vehicle Battery (12–24 V)
          │
          ▼
 Input Protection
 (Fuse + Zener)
          │
          ▼
 TPS5435A Buck Converter
        3.3 V
          │
          ├──────────────► ESP32 Header
          │
          ▼
 SN65HVD230 CAN Transceiver
          │
   CANH / CANL
          │
 Vehicle CAN Bus
```

---

## Functional Blocks

### 1. Automotive Power Input

The shield accepts an external automotive battery input through the CAN connector.

Protection circuitry includes:

- 500 mA fuse
- 24 V Zener diode
- Input decoupling capacitors

These components protect the downstream electronics from accidental over-voltage conditions and transient disturbances commonly present in automotive environments.

---

### 2. Buck Converter

The board uses the **TPS5435ADDAR** switching regulator to generate a regulated **3.3 V** rail from the vehicle supply.

Main components include:

- Input filtering capacitors
- Bootstrap capacitor
- External inductor
- Output filter capacitors
- Feedback resistor divider
- Compensation network

Advantages of using a switching regulator:

- High efficiency
- Low heat generation
- Suitable for battery-powered systems
- Wide input voltage range

---

### 3. CAN Transceiver

The communication interface is built around the **SN65HVD230**, a 3.3 V high-speed CAN transceiver.

Features:

- Fully compatible with ISO 11898 CAN
- Direct interface with ESP32 TWAI controller
- Differential CANH/CANL outputs
- Low-power standby capability
- High noise immunity

The ESP32 handles all CAN protocol processing internally while the transceiver performs physical layer conversion.

---

### 4. CAN Protection

The CAN interface includes:

- TVS/Zener protection diode
- 120 Ω termination resistor

These components improve robustness against electrical transients and provide proper CAN bus termination when required.

---

### 5. ESP32 Interface

A dual-row connector exposes the required GPIOs for an ESP32 development board.

The interface provides:

- 3.3 V supply
- Ground
- CAN TX
- CAN RX
- User GPIOs
- Status LED connections

The shield is intended to work directly with the ESP32's built-in TWAI peripheral without requiring an external CAN controller.

---

### 6. Status LEDs

Two onboard LEDs are provided for visual indication.

Possible uses include:

- Power indication
- CAN activity
- Firmware status
- Error indication

LED functionality can be configured in software.

---

## Schematic

The hardware consists of five major blocks:

- Step-Down Buck Converter
- CAN Bus Transceiver
- CANH/CANL Protection
- ESP32 Connector
- Status LEDs

---

## PCB Design

Designed in **KiCad**

Design considerations:

- Two-layer PCB
- Short CAN differential routing
- Dedicated ground plane
- Proper decoupling capacitor placement
- Switching regulator layout optimized for reduced noise
- Compact shield form factor

---

## Applications

- Automotive diagnostics
- OBD-II interfaces
- CAN data logging
- Industrial automation
- Motor control
- Robotics
- Electric vehicles
- Battery Management Systems
- ECU communication
- CAN protocol learning

---

## Future Improvements

- CAN-FD support
- Galvanic isolation
- Reverse polarity MOSFET protection
- Common-mode choke on CAN lines
- Screw terminal CAN connector
- OBD-II connector support
- Power LED and CAN TX/RX LEDs
- Onboard programming interface

---

## Tools Used

- KiCad
- ESP32
- TWAI (ESP32 CAN Controller)

---

## License

This project is open-source and intended for educational and research purposes.
