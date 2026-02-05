# STM32 Smart Light System (Dimmer + Safety Shutdown) 💡

A robust embedded system project based on **STM32F103**, featuring analog brightness control (PWM), emergency shutdown mechanism (EXTI), and real-time status logging (UART).

This project is fully simulated in **Proteus** and implemented using the **HAL Library** in STM32CubeIDE.

---

## 📂 Project Structure

Based on the repository organization:

| Folder/File | Description |
| :--- | :--- |
| **`SmartLight/`** | Contains the STM32CubeIDE source code, drivers, and build files. |
| **`proteus/`** | Contains the Proteus simulation file (`.pdsprj`). |
| **`Report.pdf`** | Full documentation and technical report of the project. |

---

## 🚀 Key Features

* **Smooth Dimming:** Controls LED brightness linearly using **PWM** (Timer 2) driven by a Potentiometer (**ADC1**).
* **Emergency Stop:** Immediate system shutdown via a Push Button using **External Interrupts (EXTI)**.
* **Status Logging:** Real-time system status ("System Ready", "SHUTDOWN", "Resumed") sent via **UART1**.
* **Anti-Flicker Logic:** optimized PWM frequency and duty cycle calculations to prevent LED flickering.
* **Fail-Safe:** System starts in a safe "Ready" state and handles toggling between modes without crashing.

---

## 🛠 Hardware Pinout

The project is configured for **STM32F103C6/C8** as follows:

| Component | STM32 Pin | Function |
| :--- | :--- | :--- |
| **Potentiometer** | `PA0` | ADC Input (Control brightness) |
| **LED (Yellow)** | `PA1` | TIM2_CH2 (PWM Output) |
| **Button** | `PC13` | EXTI13 (Falling Edge Interrupt) |
| **Virtual Terminal** | `PA9` (TX) | USART1 Transmit |
| **System Clock** | - | Internal 8MHz (HSI) |

---

## 💻 How to Run (Simulation)

1.  **Open Source Code:**
    * Navigate to the `SmartLight/` folder.
    * Open the project with **STM32CubeIDE**.
    * Build the project (Hammer icon) to generate the `.hex` or `.elf` file.

2.  **Run Simulation:**
    * Navigate to the `proteus/` folder.
    * Open the Proteus project file.
    * Double-click the STM32 microcontroller component.
    * Load the compiled `.hex` or `.elf` file from `SmartLight/Debug/`.
    * Press the **Play** button.

---

## 📊 Usage Guide

1.  **Dimming:** Turn the Potentiometer (RV1) to adjust the LED brightness from 0% to 100%.
2.  **Shutdown:** Press the Button to trigger the "Safety Mode". The LED will turn OFF immediately, and the terminal will show `!!! SHUTDOWN !!!`.
3.  **Resume:** Press the Button again to resume normal operation.

---

## 📝 License

This project is open-source and available for educational purposes.