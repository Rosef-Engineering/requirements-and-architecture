# Battery Mini

<p style="color:red">
Reviewed by Lazar on 14/04. Comments given in red. General opinion: Beyond cosmetic things, I think that more effort should be placed on defining operating conditions and coordination between multiple grid-forming converters in order for the system to function properly under a wide range of operating conditions (e.g., no generation, excess generation with batteries fully charged, excess generation with batteries not fully charged, etc.). In my opinion, establishing these requirements upfront will reduce the number of iterations needed later during full system integration.
</p>

## 1. Requirements

### 1.1. Context

#### [info] Context Block Diagram  
<img src="context-block-diagram.svg" alt="Context Block Diagram" width="500"/>

#### [info] ELV Connection
The ELV Connection, as show in the [Context Block Diagram](#info-context-block-diagram), is an electrical connection to an extra-low-voltage (ELV) node, formed either by Battery Mini or by other devices connected to the same node.

<span style="color:red">I would add a bit of clarification for electrical connection to keep it less abstract. Something like: *two wire dc line nominaly at 48V*. Part *formed by either battery mini or other device*, should be better explained later.</span>

#### [info] Battery
The Battery, as show in the [Context Block Diagram](#info-context-block-diagram), is an electrochemical energy storage device, optionally provided as part of Battery Mini, which can be detached an reattahced to Battery Mini. It can be charged and discharged by Battery Mini, i.e. it provides energy storage through Battery Mini to the [ELV Connection](#info-elv-connection).

<span style="color:red"> Conditions and reasons for detachment should be clarified, like *detached (i.e. for usage in electro mobility)*. Also what happens to the system when battery is detached, can it continue to function and under what conditions? </span>

#### [info] Rosef CAN Bus
The Rosef CAN Bus (RCAN), as show in the [Context Block Diagram](#info-context-block-diagram), is an electrical connection to a set of CAN bus lines, through which communication to other devices connected to the same [ELV Connection](#info-elv-connection) is possible and can be used to coordinate power transfer.

### 1.1. General Requirements

#### 1.1.1. Provide ELV  
Battery Mini shall be able to provide a constant voltage (nominally 48V) to the [ELV Connection](#info-elv-connection).

<span style="color:red"> Maybe better call it grid forming operation to be consistant with previously used therminology.
Nominaly it can balance the excess and shortage in power by charging and discharging the battery, but what happens when battery is fully discharged or charged. </span>

#### 1.1.2. Connect to ELV  
Battery Mini shall be able to shall be able to start operation when connected to another source of 48V at the [ELV Connection](#info-elv-connection).

#### 1.1.3. Parallel Operation  
Battery Mini shall be able to operate in parallel to another source connected to the [ELV Connection](#info-elv-connection) (e.g. another Battery Mini).

<p style="color:red">
I think this should be widen a bit to inculde coordinated operation among different grid forming converters (features like power sharing, etc..).
</p>

#### 1.1.4. Nominal Power (Bidirectional)  
Battery Mini shall be able to transfer at least 600W of power between the [Battery](#info-battery) and the [ELV Connection](#info-elv-connection) in both directions.

#### 1.1.5. Rosef CAN Communication  
Battery Mini shall communicate with other devices connected to the same [Rosef CAN Bus](info-rosef-can-bus) according to the [Rosef CAN Specification](https://github.com/Rosef-Engineering/requirements-and-architecture/tree/main/system/RCAN/).

#### 1.1.6. Communication Interface for UI
Battery Mini shall have a communication interface dedicated for connecting to a user interface for displaying information to the user and accepting input from the user.

### 1.2. Battery

#### 1.2.1 Maximum Battery Voltage
Battery Mini shall be able to operate with any [Battery](#info-battery) voltage up to 63V.

#### [info] Nominal Li-ion Battery Voltage
Since the maximum voltage of a lithium ion battery cell is 4.2V, and the nominal voltage is 3.7V, the maximum nominal battery voltage is 63V/4.2*3.7 = 56V.

<p style="color:red">
Add a clarification to formula so that you state that we will have 15 series cells.
</p>

#### 1.2.2. Minimum Battery Voltage
Battery Mini shall be able to transfer the [Nominal Power](#114-nominal-power-bidirectional) continuously with any [Battery](#info-battery) voltage down to 30V.

#### 1.2.3. Battery Recovery
Battery Mini shall be able to charge a connected [Battery](#info-battery) even if it has been fully discharged down to 0V.

<p style="color:red">
I would add another point: *ensuring proper battery charge cycle with CC and CV charging modes*.
</p>

## 2. Architecture

### Power Stage Concept

<img src="power-stage-concept.svg" alt="Power Stage Concept" width="1200"/>

### Auxiliary Power Supply Concept

<img src="aux-supplies-concept.svg" alt="Auxiliary Power Supply Concept" width="1200"/>
