 # AUTOSAR
# Layer of AUTOSAR

1. Application Layer : Basically this is our application 
2. Runtine Environment : Kind of adapter in between BSW and application layer
3. Basic Software (BSW) : Is the software
4. Microcontroller : Hardware 

**The BSW layer is splitted to  different layers: Services, ECU Abstraction, Microcontroller Abstraction and Complex Drivers.**

*Complex Drivers are not related to AUTOSAR. To communicate directly so as to reduce timing.*

**BSW are further divided into functional groups (Stacks). Examples of Services are System, Memory and Communication Services.**

- System stack are related to system level things. Eg: ECU Manager, OS

- Memory stack (Mem Stack): Deals with memory things. Eg: Flash handling, EPROM

- I/O Ports: Handling of the ports

- Communication stacks: for communication services like CAN, FlexRay, Ethernet


# Architecture - Overview of software layers

**Microcontroller Abstraction Layer**

- Lowest layer in the architecture
- Task: Make higher software layers independent of microcontroller
- Properties: Implementation is microcontroller dependent where as the upper interface are standardized and microcontroller independent

**ECU Abstraction Layer**

- Important layer in AUTOSAR
- Provide abstraction to the drivers and also to the external devices
- Control the lower layers like for microcontroller
- Task: Make higher software layers independent of ECU hardware layout
- Properties: Microcontroller independent and ECU harware dependent implementation, Microcontroller and ECU harware independent upper interface


**Compex Drivers Layer**

- Task: provide the possibility to integrate special purpose functionality; Eg: drivers for devices which are not specified within AUTOSAR, with very high timing constrains or for migration purpose etc.
- Properties: Implementation might be application, microcontroller and ECU hardware dependent. The upper interface might be application, microcontroller and ECU hardware dependent.
  
**Services Layer**

- Highest layer 
- Task:
  1. OS functionality
  2. Vehicle network communication and management services
  3. Memory services (NVRAM management)
  4. Diagnostic services (including UDS communication, error memory and fault treatment)
  5. ECU state management, node management
  6. Logical and temporal program flow monitoring (Wdg manager)
  7. Cryptogrpahic Services (Crypto Service Manager)
  8. Provide basic services for application, RTE and basic software modules.
 
- Properties: The implementation mostly microcontro;er and ECU hardware independent. Upper interface is microcontroller and ECU hardware independent.     

**AUTOSAR Runtime Environment(RTE)**

- Provide communication services to the application software (AUTOSAR Software Components and or AUTOSAR Sensor Actuator components)
- The AUTOSAR Software Components communicate with other components an or services via the RTE.
- Task: Make AUTOSAR Software Components independent from the mapping to a specific ECU.
- Properties: ECU and application specific, Upper interface are completely ECU independent.

# Architecture - Introduction to Basic Software Module Types

**Driver (Internal)**
- A driver contains the functionality to control and access an internal or an external device
- Internal devices are located inside the microcontroller. Eg: Internal EEPROM, internal CAN controller and Internal ADC
- A driver for an internal device is called internal driver and is located in the microcontroller Abstraction layer.












