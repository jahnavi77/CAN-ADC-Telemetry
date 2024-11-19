# CAN Bus Communication Between STM32F407G and STM32F446RE Boards

This project demonstrates **CAN bus communication** between two STM32 microcontroller boards, using a CAN basic transceiver to enable reliable data exchange. The STM32F407G Discovery board reads analog values from a potentiometer, transmits the data via CAN, and the STM32F446RE board monitors the received data to activate an LED based on a threshold.

---

## Overview
The project highlights the practical use of the **Controller Area Network (CAN)** protocol for real-time data exchange between microcontrollers. It involves:
1. **Reading analog values from a potentiometer** on the STM32F407G Discovery board.
2. **Transmitting these values via CAN** to the STM32F446RE board every 100 ms.
3. **Monitoring received data** on the STM32F446RE board and activating an LED if a threshold is exceeded.

---

## Repository Structure
The repository contains two separate folders, each representing the project for one of the STM32 boards. These folders can be directly opened and modified in **STM32CubeIDE**:

- **`CAN_Sender`**: Contains the project for the **STM32F407G Discovery Board**, which reads the potentiometer values and transmits them over CAN.
- **`CAN_Receiver`**: Contains the project for the **STM32F446RE Nucleo Board**, which receives the CAN messages and controls the LED based on the received values.

Each folder includes:
- CubeIDE project files (`.project`, `.cproject`, etc.)
- Source code (`Src/`, `Inc/`)
- STM32CubeMX configuration files (`.ioc`)

---

## Features
- **CAN Communication:** Configured CAN peripherals on both boards using STM32CubeMX for robust communication.
- **Analog Input Monitoring:** Reads potentiometer values with an 8-bit resolution from the STM32F407G board.
- **Threshold-Based LED Control:** Activates an LED on the STM32F446RE board when the received value surpasses a predefined threshold.
- **Periodic Updates:** Transmits data every 100 ms, ensuring consistent communication.

---

## Hardware Requirements
- **STM32F407G Discovery Board**
- **STM32F446RE Nucleo Board**
- **CAN Transceiver Modules** (e.g., MCP2551 or SN65HVD230)
- **Potentiometer**
- **LED and Resistor**
- **Breadboard and Jumper Wires**

---

## Software Requirements
- [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)
- [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)

---

## Implementation Details

### 1. **STM32F407G Discovery Board (Transmitter):**
   - Configured the **ADC** to read analog values from a potentiometer with 8-bit resolution.
   - Set up the **CAN peripheral** to transmit messages every 100 ms.
   - CAN message structure:
     - **ID:** Fixed identifier for this board.
     - **Data:** Single byte representing the potentiometer value.

### 2. **STM32F446RE Nucleo Board (Receiver):**
   - Configured the **CAN peripheral** to receive messages and process data using interrupts.
   - Monitors the received potentiometer value:
     - If the value exceeds a predefined threshold, activates an LED.
     - Otherwise, keeps the LED off.

### 3. **CAN Peripheral Configuration:**
   - **Baud Rate:** 500 kbps.
   - **Filters:** Configured to accept messages from the transmitter's identifier.
   - **Interrupts:** Used for efficient message reception and handling.

### 4. **Communication Setup:**
   - Connected CAN transceivers between the boards:
     - CAN High (CANH) and CAN Low (CANL) lines.
   - Ensured proper termination resistors (120 Ω) at both ends of the CAN bus.

---

## Usage

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/username/CAN-Bus-STM32.git
   cd CAN-Bus-STM32
