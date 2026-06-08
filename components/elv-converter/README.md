# Battery Mini

## 1. Requirements

## 2. Architecture

### Power Stage Concept

<img src="power-stage-concept.svg" alt="Power Stage Concept" width="1200"/>

### Auxiliary Power Supply Concept

<img src="aux-supplies-concept.svg" alt="Auxiliary Power Supply Concept" width="1200"/>

### Converter Control Concept

<img src="control-block-diagram.svg" alt="Converter Control Concept Block Diagram" width="1200"/>

<img src="current-shape.svg" alt="Inductor Current Shape" width="600"/>

$$ i_A = i_1 d_1 + i_2 d_2 $$


### Measurements and Protection Concept

<img src="measurements-concept.svg" alt="Measurements and Protection Concept" width="1200"/>

- If possible, we'll use center-pulse-sampling or oversampling and averaging of the inductor current via CT417 (or CT427 if more precision is needed) to determine all currents of interest.

- In case it is not possible, we can use ACS37042 for the input and output currents.

