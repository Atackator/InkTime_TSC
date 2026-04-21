InkTime-TSC Project

This project presents the design and development of a low-power, multi-functional smartwatch platform. The system is built around the nRF52840 SoC and integrates an E-paper display, motion sensing capabilities, and optimized power management within a compact PCB tailored for wearable devices.

BILL OF MATERIALS

1	ANT1	2450AT18B100E	ANTC3216X140N	Antennas 2.45GHz ANTENNA	2450AT18B100E
4	C1, C2, C17, C18	12pF	201	Generic chip capacitor	
3	C1-EP-DR, C24, C39	10uF	402	Generic chip capacitor	
3	C10, C13, C22	N.C.	201	Generic chip capacitor	
1	C11	100pF	201	Generic chip capacitor	
1	C15	1.0uF	201	Generic chip capacitor	
1	C16	47nF	201	Generic chip capacitor	
1	C2-EP-DR	4.7uF/25V	402	Generic chip capacitor	
4	C23, C27, C34, C42	0.1uF	201	Check availability	
2	C25, C33	22uF	402	Generic chip capacitor	
6	C29, C30, C31, C32, C37, C38	1uF	201	Generic chip capacitor	
2	C3, C4	1pF	201	Generic chip capacitor	
1	C43	4.7uF	201	Generic chip capacitor	
5	C5, C7, C8, C12, C19	100nF	201	Generic chip capacitor	
4	C6, C14, C20, C21	4.7uF	201	Generic chip capacitor	
1	C9	820pF	201	Generic chip capacitor	
3	D2, D4, D5	MBR0530	SOD123	Schottky Diode 0.5A 30V	
1	D3	USBLC6-2SC6Y	SOT-23-6	ESD Protection	
9	EPD_C1 ... EPD_C12	1uF/50V	402	Generic chip capacitor	
1	IC1	BQ25180YBGR	8-DSBGA	Charger IC Lithium Ion	Texas Instruments
1	IC2	DRV2605YZFR	9-DSBGA	Haptic Driver	DRV2605YZFR
1	IC3	BMA421	BMA423	Accelerometer Triaxial	BMA423
1	IC9	RT6160AWSC	15-WL-CSP	Buck-Boost Regulator	RT6160AWSC
1	J1	503480-2400	FPC-24	FFC & FPC Connectors 0.5mm	503480-2400
1	J4	USB-C 16P	KH-TYPE-C-16P	Type-C Connector	
1	L5	68uH	SMD	Inductor	744043680
1	L7	FTC252012SR47MBCA	806	SMD Inductor 0.47uH	C5832368
1	Q1	20V/4.2A	SOT23-3	P-channel MOSFET	
6	R2, R3, R4, R5, R7, R8	0 / 10k	201	Thick Film Resistor	
14	TP1 ... TP_VREG	Test Point	TP20R	Test pad	
1	U1	NRF52840_QF	AQFN-73	nRF52840 SoC	
1	X1	32MHZ	4-SMD	Crystal	

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
