InkTime-TSC Project

This project presents the design and development of a low-power, multi-functional smartwatch platform. The system is built around the nRF52840 SoC and integrates an E-paper display, motion sensing capabilities, and optimized power management within a compact PCB tailored for wearable devices.

### Bill of Materials (BOM) - PCB INKTIME

| Cant. | Referințe | Valoare | Capsulă | Descriere | MPN |
|:---:|:---|:---|:---|:---|:---|
| 1 | ANT1 | 2450AT18B100E | ANTC3216 | Antennas 2.45GHz | 2450AT18B100E |
| 4 | C1, C2, C17, C18 | 12pF | 0201 | Generic chip capacitor | - |
| 6 | C29, C30, C31, C32, C37, C38 | 1uF | 0201 | Generic chip capacitor | - |
| 1 | IC1 | BQ25180YBGR | 8-DSBGA | Charger IC Li-Ion | Texas Instruments |
| 1 | IC2 | DRV2605YZFR | 9-DSBGA | Haptic Driver | DRV2605YZFR |
| 1 | IC9 | RT6160AWSC | 15-WLCSP | Buck-Boost Regulator | RT6160AWSC |
| 1 | U1 | NRF52840_QF | AQFN-73 | nRF52840 SoC | - |
| 14 | TP1...TP_VREG | Test Point | TP20R | Test pads | - |

Hardware Overview
1. Core Processing Unit: nRF52840

The nRF52840 System-on-Chip serves as the central controller, chosen for its strong balance between computational performance and low energy consumption.

Main Characteristics:

ARM Cortex-M4F core with floating-point support
Native USB functionality
Flexible GPIO configuration supporting SPI and I2C interfaces

Clocking:

32 MHz external crystal for high-speed operation
32.768 kHz crystal for accurate timekeeping during low-power modes

Wireless Capability:

Integrated 2.4 GHz RF frontend paired with a ceramic antenna for Bluetooth Low Energy (BLE) communication
2. Power Management and Charging

The device includes a carefully designed power architecture to support portable operation.

USB-C Port:

Provides 5V input and data connectivity
Protected against electrostatic discharge using the USBLC6-2SC6Y

Battery Charging and Regulation:

BQ25180 handles LiPo charging and power path management
RT6160 DC/DC converter ensures efficient voltage regulation

Filtering and Stability:

LC filtering network reduces noise and stabilizes supply rails

Battery Monitoring:

MAX17048 fuel gauge communicates via I2C to estimate battery charge level accurately
3. E-Paper Display Module

A 1.54-inch E-paper display is used as the main visual interface, connected through a 24-pin FPC connector.

Driving Mechanism:

A custom boost circuit (using MOSFETs, Schottky diodes, and capacitors) generates the required high voltages

Communication:

SPI interface with dedicated control signals: DC (Data/Command), RST (Reset), and BUSY

Design Motivation:

The display retains the image without continuous power, making it ideal for always-on wearable applications
4. Motion Sensing and Haptic Feedback

IMU Sensor:

BMA421 accelerometer used for motion tracking
I2C communication interface
Interrupt pins (INT1, INT2) allow the MCU to wake on movement or gesture detection

Haptic System:

DRV2605 driver controls vibration feedback
Offloads waveform generation from the MCU for efficient operation
5. User Interface and Debugging

Buttons:

Three physical buttons (Up, Enter, Down) connected to GPIOs for navigation
