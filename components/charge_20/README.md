# Charge 20

## Requirements

### 1.1. Context
[info] Context Block Diagram

[info] ELV Socket
The ELV Socket, as show in the Context Block Diagram, is two wire electrical connection to an extra-low-voltage (ELV) line, nominally at 48V. In general, the ELV Socket is the power input for Charger.

[info] Phone
A phone is a consumer device that can be connected to a charger via a USB connector using an appropriate cable.

### 1.2. General Requirements

#### 1.2.1. Input voltage
Charger 20 shall be able to operate with any input voltage from 46V to 50V at the ELV Socket.

#### 1.2.2. Input power
Charger 20 shall be able to provide sufficient power to the consumers with maximum input power of 24W (max current 0.5A)

#### 1.2.3.	Output power 
Charger 20 shall be able to provide different power at different voltage level like following
5V	3A	15W
9V	2A	18W
12V	1.75A	21W

#### 1.2.4.	USB Interface
Charger 20 shall have USB Type C (USB-C) connector at output to be able to operate with different kind of phones using different kind of cables.

#### 1.2.5.	Supported charging protocols
Charger 20 shall support:
- USB Power Delivery 3.0 (fixed PDO)
- Qualcomm Quick Charge 2.0 / 3.0
- USB Battery Charging Specification 1.2 (BC1.2)
- USB Type-C Current Advertisement

#### 1.2.6.	Overcurrent protection (OCP)
Charger 20 shall limit output current to prevent damage to the power supply and connected device under overload conditions.

#### 1.2.7.	Overvoltage protection (OVP)
The output voltage shall be monitored and limited to safe thresholds for each negotiated charging profile

#### 1.2.8.	Sort circuit protection (SCP)
Charger 20 shall detect output short-circuit conditions and immediately disable or limit output to prevent damage

#### 1.2.9.	Overtemperature protection (OTP)
The charger shall monitor internal temperature and reduce output power or shut down safely when thermal limits are exceeded.

#### 1.2.10.	Electrostatic discharge protection (ESD)
The USB data and configuration lines (including CC, D+, and D− where applicable) shall be protected against electrostatic discharge in accordance with IEC 61000-4-2.

#### 1.2.11. Reverse Polarity Protection
The input stage of the device shall incorporate reverse polarity protection to prevent damage in the event that the positive and negative supply terminals are incorrectly connected. The protection circuit shall ensure that no reverse current flows into the device under any input polarity condition and shall not cause permanent damage or degradation of performance after correct reconnection.

## Architecture


