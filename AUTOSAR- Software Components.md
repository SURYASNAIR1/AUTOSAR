# What are Software Components?

- Application software within AUTOSAR is organized in self contained units called atomic 
  software components types.
  
- Such atomic software components together for the complete functional implemetation of the 
  software.

- Application software contain 3 types of software components

- Software components types:

 1. AtomicSwComponents

    - ApplicationSWComponent
      
    - NVBlockSwComponent

    - ComplexDeviceDriverSwComponent

    - ServiceSwComponent

    - ServiceProxySwComponent

    - EcuAbstractionSwComponent

    - SensorActuatorSwComponent

2. ParameterSwComponents

3. CompositionSwComponents


# Detailed Description

- ApplicationSWComponent: Examples: Performing calculation, decision making etc.
  Real Example : If we take start stop function the application sw component can decide the 
  algorithm like when to start and stop vehicle.

- NVBlockSwComponent: Used whenever we have a requirement to save critical info. in the       
  hardware memory that needs to reused in future. Act as bridge for application sw to access 
  the NVM manager of the BSW. 

Example: To calculate the kilometers the vehicle travelled we need to store the info. in NVM.
**NVM:** Non-Volatile Memory --> can keep the sw data even after power off and can be restored 
         during power on. 

- ComplexDeviceDriverSwComponent: specialised layer. The data will transfer from application   
  to microcontroller directlt through RTE. The BSW components will take more time sometimes 
  for data transfer thus we make use of this component.
  
  Example: Activating the airbag or fuel injector can be time critical

- ServiceSwComponent: To provide services to ASW from BSW

- ServiceProxySwComponent: Is used if a particular service is to be used from a different ECU 
  AUTOSAR

- EcuAbstractionSwComponent: Part of BSW that act as an interface between MCAL and the 
  application layer 















