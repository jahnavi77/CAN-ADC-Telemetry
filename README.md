# CAN Bus Communication Between Two STM32 Boards

This project demonstrates **CAN bus communication** between two STM32 microcontroller boards, using a CAN basic transceiver to enable reliable data exchange. The STM32F407G Discovery board reads analog values from a potentiometer, transmits the data via CAN, and the second board monitors the received data to activate an LED based on a threshold.

---

## Overview
The project highlights the practical use of the **Controller Area Network (CAN)** protocol for real-time data exchange between microcontrollers. It involves:
1. **Reading analog values from a potentiometer** on the STM32F407G Discovery board.
2. **Transmitting these values via CAN** to another STM32 board every 100 ms.
3. **Monitoring received data** on the second board and activating an LED if a threshold is exceeded.

---

## Features
- **CAN Communication:** Configured CAN peripherals on both boards using STM32CubeMX for robust communication.
- **Analog Input Monitoring:** Reads potentiometer values with an 8-bit resolution from the STM32F407G board.
- **Threshold-Based LED Control:** Activates an LED on the receiving board when the received value surpasses a predefined threshold.
- **Periodic Updates:** Transmits data every 100 ms, ensuring consistent communication.

---

## Hardware Requirements
- **STM32F407G Discovery Board**
- **Another STM32 Board** (e.g., STM32F446RE or similar)
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

### 2. **Receiving STM32 Board:**
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

1. **Hardware Setup:**
   - Connect the potentiometer to the STM32F407G board's ADC input.
   - Attach the LED and resistor to a GPIO pin on the receiving STM32 board.
   - Link the boards via CAN transceivers and ensure proper wiring.

2. **Run the Code:**
   - Flash the respective firmware onto both boards using STM32CubeIDE.
   - Adjust the threshold value in the receiver's code as needed.

3. **Observe Behavior:**
   - Turn the potentiometer to vary the analog value.
   - The LED on the receiving board lights up if the threshold is exceeded.

---

## Customization
- **Threshold Adjustment:** Modify the threshold value in the receiver's code to fit your application.
- **Baud Rate:** Update the CAN baud rate if needed, ensuring consistency on both boards.
- **LED Behavior:** Customize the LED control logic for different scenarios.

---

## Future Enhancements
- Add more nodes to the CAN network for multi-device communication.
- Implement additional sensors and actuators for complex applications.
- Impliment filtering messages based on ID.
- Include error handling for communication faults.
