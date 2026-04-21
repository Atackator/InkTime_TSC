InkTime-TSC Project

This project presents the design and development of a low-power, multi-functional smartwatch platform. The system is built around the nRF52840 SoC and integrates an E-paper display, motion sensing capabilities, and optimized power management within a compact PCB tailored for wearable devices.

[PCB_INKTIME.csv](https://github.com/user-attachments/files/26937854/PCB_INKTIME.csv)

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
