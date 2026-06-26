# ELV Converter

## 1. Requirements

#### [info] Application
The ELV Converter is meant to cover the needs of [Solar Mini](https://github.com/Rosef-Engineering/requirements-and-architecture/tree/main/components/solar_mini) and [Battery Mini](https://github.com/Rosef-Engineering/requirements-and-architecture/tree/main/components/battery_mini). The main requirements are listed out below.

#### Port A Voltage Range
ELV Converter shall be able to operate with Port A voltages up to 65V.

#### Port B Voltage
ELV Converter shall be able to operate with Port B voltages from 46V to 50V.

#### Port B Start-up
ELV Converter shall be able to start operation with 0V at Port B if the voltage at Port A is at least 12V.

#### Nominal Power
ELV Converter shall be able to transfer at least 600W of power continuously between Port A and Port B in both directions, if the voltage at Port A is at least 33V.

#### Port A Current
ELV Converter shall be able to source and sink up to 18A of current at Port A, provided that the voltage at Port A is between 24V and 33V.

#### Port A Ripple
ELV Converter shall generate at most 1.5Vpp of ripple at Port A.

#### Port B Ripple
ELV Converter shall generate at most 0.1Vpp of ripple at Port B.

## 2. Architecture

### General Design Decisions

#### Zero Voltage Switching (ZVS)
Other than the first commutation at the begining of operation, every commutation shall be ZVS and such that the voltage derivative of the switching node is at most ±10V/ns.

### Power Stage Concept

The selected topology is the four switch buck boost, because of its non-inverting buck and boost capabilities as well as low passives count (e.g. compared to SEPIC/Zeta and cascaded boost-buck) and because of its ZVS capability even with a wide input voltage range.

<img src="power-stage-concept.svg" alt="Power Stage Concept" width="600"/>

### Auxiliary Power Supply Concept

<img src="aux-supplies-concept.svg" alt="Auxiliary Power Supply Concept" width="600"/>

### Converter Control Concept

<img src="control-block-diagram.svg" alt="Converter Control Concept Block Diagram" width="600"/>

<img src="current-waveform-pos.svg" alt="Example Inductor Current Waveform" width="500"/>

<img src="current-waveform-neg.svg" alt="Example Inductor Current Waveform" width="500"/>

<img src="u2di.svg" alt="Control Signal u Decomposition" width="350"/>

- The current $i_u$ in the above graph is the current closer to zero between $i_1$ and $i_2$, i.e. if $sign(u) == sign(v_A-v_B)$, then $i_1 = i_u$, else $i_2 = i_u$.
- The minimum $d_{4min}$ is necessary so that $i_s$ can be sampled with a finite current sensor bandwidth.

<img src="ulim.svg" alt="Control Signal u Limiting" width="350"/>


### Measurements and Protection Concept

<img src="measurements-concept.svg" alt="Measurements and Protection Concept" width="600"/>

- The inductor current is sampled during $d_4$ via CT417 (or CT427 if more precision is needed) to obtain $i_s$ as necessary for the current shaping deadbeat control.

- The output of the ACS37042 sensors is used to determine the input and output currents.

