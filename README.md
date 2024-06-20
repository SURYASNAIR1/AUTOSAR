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


























