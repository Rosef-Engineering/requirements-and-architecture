# ELV Converter

## 1. Requirements

## 2. Architecture

### Power Stage Concept

<img src="power-stage-concept.svg" alt="Power Stage Concept" width="600"/>

### Auxiliary Power Supply Concept

<img src="aux-supplies-concept.svg" alt="Auxiliary Power Supply Concept" width="600"/>

### Converter Control Concept

<img src="control-block-diagram.svg" alt="Converter Control Concept Block Diagram" width="600"/>

<img src="current-waveform-pos.svg" alt="Example Inductor Current Waveform" width="500"/>

<img src="current-waveform-neg.svg" alt="Example Inductor Current Waveform" width="500"/>

<img src="u2di.svg" alt="Control Signal u Decomposition" width="350"/>

The current $i_u$ in the above graph is the current closer to zero between $i_1$ and $i_2$, i.e. if $sign(u) == sign(v_A-v_B)$, then $i_1 = i_u$, else $i_2 = i_u$.
The minimum $d_{4min}$ is necessary so that $i_s$ can be sampled with a finite current sensor bandwidth.

<img src="ulim.svg" alt="Control Signal u Limiting" width="350"/>


### Measurements and Protection Concept

<img src="measurements-concept.svg" alt="Measurements and Protection Concept" width="600"/>

- If possible, we'll use center-pulse-sampling or oversampling and averaging of the inductor current via CT417 (or CT427 if more precision is needed) to determine all currents of interest.

- In case it is not possible, we can use ACS37042 for the input and output currents.

