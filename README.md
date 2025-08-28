# CAN-Based ADC Telemetry and Control System  
*STM32F103C8T6 | MCP2551 | STM32CubeIDE | CANalyzer*

## 📌 Project Overview
This project implements a **CAN bus telemetry and control system** using STM32 microcontrollers and MCP2551 transceivers.  
The setup demonstrates how analog sensor data can be sampled, transmitted over CAN, and processed by another MCU for real-time control applications.

Key functions:
- Sampling analog data with the **12-bit ADC** of an STM32F103C8T6.  
- Transmitting sensor values periodically over **CAN bus**.  
- Receiving messages on a second MCU and applying **threshold-based control logic** (e.g., toggling an LED).  
- Verifying performance using **Vector CANalyzer**.  

---

## 🔧 Features
- **CAN Communication**  
  Configured 125 kbps CAN bus with **11-bit standard IDs** and hardware filters for reliable communication.  

- **Analog Data Acquisition**  
  Continuous 12-bit ADC sampling at 72 MHz HSE clock.  

- **Interrupt-Driven Reception**  
  Implemented HAL CAN interrupts for error-free, non-blocking message handling.  

- **Error-Free Performance**  
  Achieved **0% frame error rate** across 1,000+ consecutive messages in testing.  

- **Modular Design**  
  Separate sender and receiver firmware, each as an independent STM32CubeIDE project.  

---

## 🗂 Repository Structure
- **CAN_Sender/**  
  Firmware for the STM32F103C8T6 board that reads analog values (e.g., potentiometer) and transmits them over CAN.  

- **CAN_Receiver/**  
  Firmware for the receiving STM32F103C8T6 board that listens for CAN messages and drives an LED (or other actuator) when thresholds are met.  

Each project folder includes:
- `Src/` and `Inc/` source files  
- `.ioc` configuration files (STM32CubeMX)  
- CubeIDE project settings  

---

## 🛠 Hardware Requirements
- STM32F103C8T6 boards (Blue Pill or equivalent)  
- MCP2551 CAN transceiver modules (or SN65HVD230 as an alternative)  
- Potentiometer (for analog input)  
- LED + resistor (for receiver output)  
- Breadboard & jumper wires  
- 120 Ω termination resistors for CAN bus  

---

## 💻 Software Requirements
- [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html)  
- [STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html)  
- [CANalyzer](https://www.vector.com/int/en/products/products-a-z/software/canalyzer/) (or equivalent CAN monitoring tool)  

---

## ⚙️ Implementation Details
### Sender (STM32F103C8T6)
- Configured ADC to sample analog input (12-bit).  
- Periodically transmits data frames with fixed identifier.  
- Data field: single byte (scaled ADC value).  

### Receiver (STM32F103C8T6)
- Configured CAN in interrupt mode to receive messages.  
- Parses ADC value from received CAN frame.  
- Activates LED if value exceeds predefined threshold.  

### CAN Settings
- **Baud Rate**: 125 kbps  
- **Identifier**: Standard 11-bit ID  
- **Filters**: Hardware filters configured for sender’s ID only  
- **Interrupts**: Enabled for message reception  

---

## 🔌 Connection Setup
- Connect both MCP2551 transceivers to their respective STM32 boards.  
- Tie together CAN High (CANH) and CAN Low (CANL).  
- Place 120 Ω termination resistors at both ends of the CAN bus.  


