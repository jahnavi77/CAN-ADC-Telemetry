# CAN Bus Communication Between Two STM32 Boards

This project demonstrates the implementation of **CAN bus communication** between STM32 microcontroller boards: the STM32F446RE and STM32F407G. The project leverages **STM32CubeMX** and **STM32CubeIDE** for configuration and development, showcasing an interrupt-driven communication system to synchronize the boards.

## Overview
The project focuses on establishing two-way communication between two STM32 boards using the **Controller Area Network (CAN)** protocol. It includes configuring the CAN peripheral on both boards, enabling communication via interrupts, and demonstrating message exchange with onboard buttons and LEDs.

---

## Features
- **CAN Peripheral Configuration:** Configured master and slave nodes using **STM32CubeMX**.
- **Interrupt-Driven Communication:** Optimized synchronization between microcontrollers with interrupt-based CAN messaging.
- **Two-Way Messaging:** Onboard buttons send messages; LEDs indicate received messages on both boards.
- **Scalable Design:** Easily extendable for more advanced CAN bus applications.

---

## Hardware Requirements
- STM32F446RE Nucleo Board
- STM32F407G Discovery Board
- CAN transceiver modules (e.g., MCP2551 or SN65HVD230)
- Jumper wires for CAN High (CANH) and CAN Low (CANL) connections
- Breadboard (optional)

---

## Software Requirements
- [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)
- [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)

---

## Implementation Details

1. **CAN Peripheral Initialization:**
   - Configured the CAN peripheral on both STM32 boards using STM32CubeMX.
   - Set baud rates, filters, and modes for both master (transmitter) and slave (receiver).

2. **Interrupt-Driven Messaging:**
   - Enabled CAN interrupts to handle message transmission and reception efficiently.
   - Improved synchronization by avoiding polling-based approaches.

3. **Demonstration with LEDs and Buttons:**
   - Button presses on one board trigger a CAN message sent to the other board.
   - Received messages toggle corresponding LEDs to visualize communication.

---

## Setup and Usage

1. Clone this repository:
```bash
   git clone https://github.com/WassimHedfi/CAN_Protocol_STM32f446re_V_STM32f407G
   cd can-bus-stm32
```

2. Connect the hardware:
  * Wire the CAN transceiver modules to the STM32 boards.
  * Connect CANH and CANL lines between the two transceivers.
3. Flash the firmware:
  * Open the project in STM32CubeIDE.
  * Build and flash the code onto both STM32 boards.

4. Test the communication:
  * Press the button on one board to send a message.
  * Observe the LED response on the other board.
