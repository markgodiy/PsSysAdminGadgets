# PsSysAdminGadgets

## PsSysAdminGadgets - Console Project

**PsSysAdminGadgets** is a toolkit for IT System Administrators, designed to interface with the **Adafruit FT232H breakout board** and connected peripherals via the **.NET IoT library**. This repository focuses on creating a console-based solution that will later be expanded with a GUI wrapper.

### Table of Contents
1. [Project Overview](#project-overview)
2. [Hardware Requirements](#hardware-requirements)
3. [Software Requirements](#software-requirements)
4. [Getting Started](#getting-started)
5. [Development Phases](#development-phases)
6. [Contributing](#contributing)
7. [License](#license)

---

### Project Overview

The **PsSysAdminGadgets** console project interfaces with hardware components like buttons, RGB LEDs, an OLED display, and various connected peripherals. The project is designed to:
- Provide basic controls via GPIO (buttons, LEDs).
- Display system and gadget information via I2C on an SSD1306 OLED display.
- Communicate with peripheral gadgets via an RJ45 connection, allowing modular expansion of additional sensors, actuators, and other control devices.
- Handle power management using USB-C for basic operation and an auxiliary power supply for more power-hungry gadgets.

This repository will be modular and scalable, with future plans to integrate with a GUI wrapper project.

### Hardware Requirements

To use **PsSysAdminGadgets**, you will need the following hardware components:

![image](https://github.com/user-attachments/assets/8ae66eb4-9bc3-49bf-9f24-2327da9ef055)

- **Adafruit FT232H breakout board**
- **2 x Push Buttons** connected to GPIO
- **2 x RGB LEDs** connected to GPIO
- **SSD1306 OLED display** (I2C interface)
- **RJ45 breakout board** (for connecting peripheral gadgets)
- **Auxiliary Power Socket** (optional for high-power peripherals)
- **USB-C cable** (for basic power supply to the control board)

### Software Requirements

- **.NET 6 or later**
- **.NET IoT Library**
- **FTDI FTD2xx DLL wrapper** (for FT232H interaction)
- **Visual Studio or VS Code** for development
- **Windows 10/11** (or another compatible operating system)
- **PowerShell** (for integrating later as a PowerShell module)

### Getting Started

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-repo/PsSysAdminGadgets.git
    cd PsSysAdminGadgets
    ```

2. **Install .NET dependencies**:
    Make sure you have the required .NET IoT packages installed:
    ```bash
    dotnet add package System.Device.Gpio
    dotnet add package Iot.Device.Bindings
    ```

3. **Configure hardware**:
    - Connect the FT232H board to your PC via USB-C.
    - Wire the buttons, LEDs, and display according to the [Hardware Setup Guide](./HARDWARE_SETUP.md).

4. **Run the project**:
    Use the following command to build and run the project:
    ```bash
    dotnet run
    ```

---

### Development Phases

The project is broken into development phases to progressively build the toolkit’s features and prepare for future GUI integration.

#### Phase 1: Core Console App with GPIO and I2C Integration
- **Goal**: Set up the core hardware interfacing with buttons, LEDs, and the SSD1306 OLED display.
- **Tasks**:
  - Initialize GPIO for buttons and RGB LEDs.
  - Interface with the SSD1306 display over I2C to show system status.
  - Implement a basic control loop that toggles LEDs based on button presses.
  - Display status information (e.g., button press feedback, system uptime) on the OLED display.
- **Outcome**: A working console app that interacts with basic hardware.

#### Phase 2: RJ45 Peripheral Communication
- **Goal**: Establish communication with peripherals connected via the RJ45 breakout board.
- **Tasks**:
  - Define the data protocol for communication with connected gadgets.
  - Implement pin management (C0-C8) for peripheral interactions.
  - Send and receive data between the main gadget and peripheral devices.
- **Outcome**: A system that can communicate and control connected gadgets via the RJ45 interface.

#### Phase 3: Power Management Integration
- **Goal**: Add support for auxiliary power to handle power-hungry peripherals.
- **Tasks**:
  - Integrate power switching logic (use relays or GPIO-controlled circuits) to manage auxiliary power supply.
  - Implement current monitoring or voltage checks to ensure safe power distribution.
  - Ensure peripherals can switch between USB-C and auxiliary power when required.
- **Outcome**: Stable power management with both USB-C and auxiliary power support.

#### Phase 4: PowerShell Module Integration
- **Goal**: Package the console app as a PowerShell module for easy usage by IT administrators.
- **Tasks**:
  - Wrap core functionalities in PowerShell cmdlets.
  - Export key functions (e.g., gadget control, system monitoring) as cmdlets.
  - Ensure cross-compatibility between the console app and PowerShell environment.
- **Outcome**: A PowerShell module that wraps the core console functionalities.

#### Phase 5: Future Expansion (Optional)
- **Goal**: Build advanced functionalities for the control gadget and prepare for GUI integration.
- **Tasks**:
  - Add new peripherals (e.g., temperature sensors, servos) connected via the RJ45 breakout.
  - Optimize the communication protocol for multiple gadgets.
  - Prepare the console app for seamless transition to a WPF GUI wrapper.
- **Outcome**: A feature-rich console project that can be expanded with additional gadgets.

---

### Contributing

We welcome contributions! Please follow the guidelines outlined in [CONTRIBUTING.md](./CONTRIBUTING.md) to submit issues, feature requests, and pull requests.

### License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
