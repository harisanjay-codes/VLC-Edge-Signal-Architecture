# VLC-Edge-Signal-Architecture

**A secure, air-gapped optical communication protocol for RF-denied and mission-critical environments.**



## Overview
Traditional RF-based communication (Wi-Fi, Bluetooth) is fundamentally compromised by susceptibility to electromagnetic interference (EMI), jamming attacks, and interception. **VLC-Edge-Signal-Architecture** addresses these vulnerabilities by utilizing Visible Light Communication (VLC) to create a physically constrained, air-gapped data bridge.

This project implements a custom **Manchester-encoded firmware architecture** on an ESP8266/Arduino stack to modulate high-intensity LED sources, converting digital data packets into a secure, line-of-sight optical stream.

## System Architecture
The following diagram illustrates the data flow from the digital source to the optical physical layer:



## Key Technical Features
* **Physical Layer Security:** Data is transmitted via visible light, ensuring interception is impossible without direct line-of-sight.
* **RF Immunity:** Operates entirely outside the radio frequency spectrum, immune to RF jamming.
* **Manchester Encoding:** Implemented at the firmware level to ensure robust data integrity and clock synchronization.
* **Edge-Computing:** The entire modulation/demodulation stack runs on bare-metal firmware, minimizing latency.

## Hardware Stack
| Component | Function |
| :--- | :--- |
| **NodeMCU ESP8266** | Transmitter (Light modulation engine) |
| **Arduino Nano** | Receiver (High-speed pulse decoding) |
| **3W High-Power LED** | Optical signal source |
| **Laser Receiver Module** | Photodiode-based signal capture |

## Firmware Logic
The transmitter uses a custom bit-banging algorithm to toggle the LED state at specific intervals defined by the Manchester protocol. The receiver utilizes a fast polling loop to detect state changes on the photodiode, performing real-time signal conditioning to filter out ambient light noise before reconstructing the binary bitstream.

## Getting Started

### Prerequisites
* Arduino IDE
* ESP8266 Board Package

### Installation
1. Clone this repository: `git clone https://github.com/yourusername/VLC-Edge-Signal-Architecture.git`
2. Open `transmitter.ino` in Arduino IDE and upload to the NodeMCU.
3. Open `receiver.ino` in Arduino IDE and upload to the Arduino Nano.
4. Align the LED and the photodiode within a direct line-of-sight.

## Demonstrations
* **Interruption Test:** Blocking the light path immediately suspends the data stream, demonstrating the physical-layer air-gap.
* **Robustness Test:** Varying the distance between the transmitter and receiver to verify signal integrity.

---
*Developed as an Interdisciplinary Project (IDP).*
