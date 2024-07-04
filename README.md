 # AUTOSAR : AUTomotive Open System ARchitecture
# Layer of AUTOSAR

1. Application Layer : Basically this is our application 

2. Runtine Environment(RTE) : Kind of adapter in between BSW and application layer

3. Basic Software (BSW) : Is the software

4. Microcontroller : Hardware 

**The BSW layer is splitted to  different layers: Services, ECU Abstraction, Microcontroller Abstraction and Complex Drivers.**

*Complex Drivers are not related to AUTOSAR. To communicate directly so as to reduce timing.*

**BSW are further divided into functional groups (Stacks). Examples of Services are System, Memory and Communication Services.**

- System stack are related to system level things. Eg: ECU Manager, OS

- Memory stack (Mem Stack): Deals with memory things. Eg: Flash handling, EPROM

- I/O Ports: Handling of the ports

- Communication stacks: for communication services like CAN, FlexRay, Ethernet

- BSW Horizontal division: Layers, vertical division: Stacks

# Architecture - Overview of software layers

**Microcontroller Abstraction Layer**

- Lowest layer in the architecture

- Task: Make higher software layers independent of microcontroller

- Properties: Implementation is microcontroller dependent where as the upper interface are 
  standardized and microcontroller independent

**ECU Abstraction Layer**

- Important layer in AUTOSAR

- Provide abstraction to the drivers and also to the external devices

- Control the lower layers like for microcontroller

- Task: Make higher software layers independent of ECU hardware layout

- Properties: Microcontroller independent and ECU harware dependent implementation, 
  Microcontroller and ECU harware independent upper interface


**Compex Drivers Layer**

- Task: provide the possibility to integrate special purpose functionality; Eg: drivers for 
  devices which are not specified within AUTOSAR, with very high timing constrains or for 
  migration purpose etc.

- Properties: Implementation might be application, microcontroller and ECU hardware dependent. 
  The upper interface might be application, microcontroller and ECU hardware dependent.
  
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
 
- Properties: The implementation mostly microcontro;er and ECU hardware independent. Upper 
  interface is microcontroller and ECU hardware independent.     

**AUTOSAR Runtime Environment(RTE)**

- Provide communication services to the application software (AUTOSAR Software Components and 
  or AUTOSAR Sensor Actuator components)

- The AUTOSAR Software Components communicate with other components an or services via the RTE.

- Task: Make AUTOSAR Software Components independent from the mapping to a specific ECU.

- Properties: ECU and application specific, Upper interface are completely ECU independent.

# Architecture - Introduction to Basic Software Module Types

**Driver (Internal)**
- A driver contains the functionality to control and access an internal or an external device

- Internal devices are located inside the microcontroller. Eg: Internal EEPROM, internal CAN 
  controller and Internal ADC

- A driver for an internal device is called internal driver and is located in the 
  microcontroller Abstraction layer.

**Interface (Interface module)**
- It contains functionality to abstract from modules which are architecturally placed below 
  them. Eg; an interface module which abstracts from the hardware realization of a specific 
  device.

- It provides a generic API to access a specific type of device independent on the number of 
  existing devices of that type and independent on the hardware realization of the different 
  devices.

- The interface does not change the content of the data.

- The interfaces are located in the ECU Abstraction Layer.

- Example: an interface for a CAN controller communication system provides a generica API to 
  access CAN communication networks independent on the number of CAN controllers within an ECU 
  and independent of the hardware realization (on chip, off chip).

**Handler**
- Control the concurrent, multiple and asynchronous access of one or multiple clients to one 
  or more drivers.

- It performs buffering, queuing, arbitration, multiplexing

- The handler does not change the content of the data

- Handler functionality is often incorporated in the driver or interface (eg: 
  SPIHandlerDriver, ADC Driver)

**Manager**
- Offers specific services for multiple clients.

- It is needed in all cases where pure handler functionality is not enough to abstract from 
  multiple clients.

- Can evaluate and change or adapt the content of the data.

- Managers are located in service layer.

- Example: The NVRAM manager manages the concurrent access to internal and/or external memory 
  devices like flash and EEPROM memory. It also performs distributed and reliable data 
  storage, data checking, provision of default values etc.

# Architecture - contenet of software layers 
**Microcontroller Abstraction Layer**
- Communication Drivers
  Drivers for ECU onboard (eg:SPI) and vehicle communication (eg: CAN), OSI-Layer: Part of Data link layer

- I/O Drivers
  Drivers for analog and digital I/O (eg:ADC, PWM, DIO)

- Memory Drivers
  for on-chip memory devices (internal flash, internal EEPROM) and memory mapped extenal memory devices (eg: external flash)

- Microcontroller Drivers
  Drivers for internal peripherals (eg: watchdog and general purpose timer)
  Function with direct microcontroller access (eg: Core test)

**Microcontroller Abstraction Layer: SPIHandlerDriver**

- Allow concurrent access of several clients to one or more SPU busses.

- To abstract all features of a SPI microcontroller pins dedicated to chip select, those shall 
  directly be handled by the SPIHandlerDriver. That means those pins shall not be available in 
  DIO Driver.

**Complex Drivers**
- Is a module which implements non-standardized functionality within the basic software stack.

- Eg: Complex sensor,actuators

- Task: Fulfill the special functional and timing requirements for handling comple sensors and 
  actuators

- Properties: Implementation highly microcontroller, ECU and pplication dependent. Upper 
  interface to SW-Cs specified and implemented according to AUTOSAR. Lower interface 
  restricted access to standardized interfaces.

**Communication Hardware Abstraction**
- It abstract from the location of communication controllers and the ECU hardware layout.
- For all communication systems a specific communication hardware abstraction is required (LIN, CAN, FlexRay)
- Example: An ECU has a microcontroller with 2 internal CAN channels and an additional on-board ASIC with 4 CAN controlers. The CAN-ASIC is connected to the microcontroller via SPI.
-Task: Provide equal mechanisms to access a bus channe; regardless of it's location (on chip/ on board)
- Properties: Implementation is microcontroller independent, ECU hardware dependent and external device dependent. Upper interface is bus dependent, microcontroller and ECU hardware independent.
  
** Communication Stack - CAN**
- The CAN communication services are a group of modules for vehicle network communication with the communication system CAN.
- Provide a uniform interface to the CAN network
- Hide protocols and message properties from the application
- Supports: Classic CAN communication (CAN 2.0), CAN FD communication 

** Communication Stack - LIN (LIN Master)**
- LIN communication services are a group of modules for vehicle network communication with the communication system LIN.
- Task: Provide a uniform interface to the LIN network. Hide protocol and message properties from the application.
- Properties:
   - A LIN 2.1 complaint communication stack with
      - Schedule table manager for transmitting LIN frames and to handle requests to switch to 
         other schedule tables
      - Transport protocol, used for diagnostics
      - A wakeup and sleep interface
   - An underlying LIN driver:
       - Implementing the LIN protocol and adaptation the specific hardware
       -  Supporting both simple UART and complex frame based LIN hardware
       
**Communication Stack - FlexRay**

- Provide a uniform interface to the FlexRay network.
- Hide protocol and messade properties from the application
- 2 transport protocol modules in the FlexRay stack are :
  - FrTp: FlexRay ISO Transport Layer
  - FrArTP: FlexRay AUTOSAR Transport Layer, provides bus compatibility to AUTOSAR R3.x

**Communication Stack - TCP/IP**

Task: Provide an uniform interface to the TCP/IP network. Hide protocol and message properties from the application.

**Communication Stack - General**

- IPDU multiplexing provides the possibility to add information to enable the multiplexing of I-PDUs contents but same IDs on the bus.
- Multi I-PDU to container mapping provides the possibility to combine several I-PDUs to one larger I-PDU to be transmitted in one frame.

- R20-11 is the latest version of AUTOSAR

**Core partner** : Bosch, ford, Daimler,BMW
**Premium partner** : Honda, volvo, kia
**Development partner** : Cosmic, C&S

# How AUTOSAR
**Yesterday**

- High coupling between software and hardware. Software will directly use the hardware.
  
- Difficult to reuse SW from one ECU to another

**Today**
- No coupling between software and hardware - reducing development  time and costs

- Easier to reuse SW from one ECU ro another

- Enhance quality 

- AUTOSAR component must be reusable

- Cooperate on standards, compete on implementation --> Quote from AUTOSAR

# Application Layer
   Example: To control the speed of wiper
   
- Application software component: could be calculated at any ECU

- Actuator software component, sensor software component: Placed in the Application software component but have specific actuator and sensor.

# Runtime Environment(RTE)
- For communication between Application and Basic software layer as well as between different application software component. 

- **Virtual Funtion Bus(VFB):** communication mechanism that allows SW-components to interact. It's a virtual concept. Its used at the system design time to represent what all the s/w components shall be present in the system and how they shall interact communicate with one another. Using this the OEM can get to know how the ECUs will communicate with each other.
















