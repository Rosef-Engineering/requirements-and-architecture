# Solar Mini

## 1. Requirements

### 1.1. Context

#### [info] Context Block Diagram  

#### [info] ELV Connection
The ELV Connection, as show in the [Context Block Diagram](#info-context-block-diagram), is a two wire electrical connection to an extra-low-voltage (ELV) line, nominally at 48V. As explained in chapter below, it is supplied by Battery Mini and/or other devices connected to the same line.

#### [info] PV Input
The PV Input is a primary power source, shown on the left side of the [Context Block Diagram](#info-context-block-diagram). The system is built for various input voltages, for panels with a nominal voltage of 24V and 36V. Input can be a single-panel or multiple-panel, connected in parallel, with a variation of input power from 0.1kW up to 1kW. 

#### [info] Rosef CAN Bus
The Rosef CAN Bus (RCAN), as show in the [Context Block Diagram](#info-context-block-diagram), is a two wire electrical connection to a CAN bus line, through which communication to other devices connected to the same [ELV Connection](#info-elv-connection) is possible and can be used to coordinate power transfer.

### 1.1. General Requirements

#### 1.1.1. MPPT Control  
Solar Mini is required to maintain a Maximum Power Point Tracking (MPPT) mode, provided that the available PV power and the ELV connection conditions are within the operational limits.

Note: This functionality is limited by the load power consumption, Sun irradiation, and battery state of charge.  

#### 1.1.1. Connect to ELV
Battery Mini is the main voltage regulator of the ELV grid, but in the case when there is no Battery Mini, PV Mini takes this role as well. 

#### 1.1.2. Parallel Operation
PV Mini shall be able to operate in parallel with another source connected to the ELV Connection (e.g. another PV Mini or Battery Mini). Also, the parallel connection of PV arrays is acceptable. 

#### 1.1.3. Nominal Power
PV Mini shall be able to produce a maximum of 1kW of power if the PV array allows that, the weather is optimal, and there is a need for that much power in the system (either directly supplying output or charging the Battery Mini. 

#### 1.1.4. Rosef CAN Communication
PV Mini shall communicate with other devices connected to the same Rosef CAN Bus according to the Rosef CAN Specification.

### 1.2. PV Array limits

#### 1.2.1 Maximum input voltage
Maximum voltage is defined by the PV array. Usually, it is named as Open Circuit voltage, and for 36V PV arrays can go up to 48V. 

#### [info] Nominal Input voltage
Nominal input voltage highly depends on the PV array nominal voltage, weather conditions, and load conditions; it can vary from 20V to 48V.

#### 1.2.2. Minimum Input Voltage
PV mini can work with a 24V input system, and the lowest voltage is reached with very low sunlight. It can be as low as 18V. 


## Architecture


