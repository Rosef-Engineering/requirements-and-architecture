# PayGo Module

## Requirements

### 1.1. Context

<img src="context-block-diagram.svg" alt="TO-DO: Context Block Diagram" width="500"/>

### 1.2. General

#### 1.2.1.
PAYGo Controller Mini shall authorize or block Solar Mini energy production based on OpenPAYGO token credit.

#### 1.2.2.
PAYGo Controller Mini shall communicate with Solar Mini over CAN using an Ethernet/RJ45 cable as the physical cable.

#### 1.2.3. Architecture
User pays
  ↓
Backend confirms payment
  ↓
Backend generates OpenPAYGO token
  ↓
PAYGo Controller receives token
  ↓
PAYGo Controller validates token
  ↓
PAYGo Controller sends CAN authorization
  ↓
Solar Mini enables / limits / disables output

#### 1.2.4.
PAYGo Controller Mini shall support:  
|   Mode                |          Meaning                            |  
|-----------------------|---------------------------------------------|  
| Daily credit          | User paid for today / number of days        |  
| Monthly credit        | User paid for current month / 30-day period |  
| Offline token mode    | Device can unlock without internet          |  
| CAN control mode      | Solar Mini receives authorization over CAN  |  

### 1.3 Hardware Requirements
#### 1.3.1 Microcontroller
PAYGo Controller Mini shall include a microcontroller, for example : STM32 with native CAN/FDCAN

#### 1.3.2 CAN Interface  
PAYGo Controller Mini shall include:  
CAN transceiver	 
RJ45/Ethernet connector	 
ESD protection	
120 Ω termination?	
CAN bus-off recovery?  

#### 1.3.3 Power Supply  
PAYGo Controller Mini shall be powered from the ELV system.  
Input range:  Compatible with Solar-Mini voltage range?? (or ELV??)  
5V regulator  
Fuse protection  
Reverse polarity protection  
Brownout_detection  

#### 1.3.4 Memory  
PAYGo Controller Mini shall store:  
Device ID  
OpenPaygo secret key  
Token counter  
Remaining credit  
Paygo state  
CAN node ID  
Old tokens  

#### 1.3.5 User/Service Interface
LEDs >  indicate if active,inactive, fault  
USB_uart  > debuging, QA  
Keypad for token input??  
GSM  
BLE?  
Wi-fi?  

### 1.4 Software Requirements
#### 1.4.1 Token Handling
PAYGo Controller Mini shall:  
Receive OpenPAYGO token.  
Decode token.  
Check token validity.  
Check token counter.  
Reject reused tokens.  
Add or set credit time.  
Store new credit state.  
Send PAYGo status over CAN.  
#### 1.4.2 Backend requirements  
Backend enables that payment provider is not relevant to a given paygo device.  
The device only needs a valid token.  
  
Registed devices  
Store device keys  
Receive payment confirmation  
Generate OpenPayGO tokens  
Deliver tokens by sms or can or other type of entry  




> [!IMPORTANT]  
> TO-DO: Define token results, device states, credit handling,can req, solar mini response req. security requirements, failure requirements



## Architecture


