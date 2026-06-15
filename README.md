# Parking Slot Detection System

![Platform](https://img.shields.io/badge/Platform-Arduino%20Uno-teal)
![License](https://img.shields.io/badge/License-MIT-yellow)

An Arduino-based smart parking system that uses ultrasonic sensors to detect occupied and free slots, displays available spaces on a 16×2 LCD near the entry point, and controls a servo motor gate for entry and exit.

## Table of Contents

- [Overview](#overview)
- [Components](#components)
- [How It Works](#how-it-works)
- [Simulation](#simulation)
- [Limitations](#limitations)
- [License](#license)

## Overview

The system addresses the time and fuel wasted searching for a free parking spot. Ultrasonic sensors monitor each parking slot; the count of available spaces is shown on an LCD display at the entry point so drivers can decide before entering the lot. A push-button and servo motor handle the entry gate.

## Components

| Component | Purpose |
|-----------|---------|
| Arduino Uno R3 | Microcontroller |
| HC-SR04 Ultrasonic Sensor | Detects vehicle presence in each slot |
| 16×2 LCD | Displays available slot count at entry |
| Servo Motor | Controls the entry/exit gate |
| Push-button | Driver input to request entry |
| Resistor | Current limiting for button circuit |
| Breadboard | Prototyping connections |

## How It Works

**Entry point**
1. A driver presses the push-button at the entry gate.
2. The Arduino checks the LCD-displayed slot count; if a space is free, it opens the servo motor gate.
3. The driver proceeds to the indicated slot.

**Slot detection**
1. An ultrasonic sensor at each parking slot continuously measures distance.
2. When a vehicle occupies a slot, the sensor reading drops below the detection threshold and the slot is marked unavailable.
3. When the vehicle leaves, the sensor detects the increased distance and the available count increments.
4. The updated count is shown on the LCD in real time.

## Simulation

The implementation is available as two linked Tinkercad simulations (no source code is committed to this repository):

| Module | Tinkercad Link |
|--------|---------------|
| Car Entry Point | https://www.tinkercad.com/things/bWh9BLlzTsF |
| Car Exit Point | https://www.tinkercad.com/things/czc2nLRfFg7 |

## Limitations

- **Simulation only** — no source code is committed to this repository; the full implementation exists only in the Tinkercad projects linked above.
- **Fixed threshold** — slot occupancy is determined by a hardcoded distance threshold; calibration would be needed for different vehicle sizes or sensor mounting heights.
- **Single entry/exit lane** — the current design handles one gate per simulation; a multi-lane lot would require additional logic.
- **No persistence** — slot state resets if power is lost; a real deployment would need non-volatile storage or a network-connected backend.

## License

Released under the [MIT License](LICENSE).
