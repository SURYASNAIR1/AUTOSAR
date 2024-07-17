# Secure Onboard Communication (SecOC)

- Protects the communication in AUTOSAR Automotive network
  - CAN

  - Ethernet

  - Flexray

- Adds security to the onboard communication

- Freshness- Adding counter or freshness period

- Authenticity - Adding MAC or signature

- ECU's are sending messages using CAN protocol and is not authenticated thus there is a 
  possibility of attacks. Thus we include SecOC to protect onboard vehicular communication.

- Thus we can integrate secoc to automotive networks like CAN, Ethernet and Flexray.

# Specification of Secure Onboard Communication Architecture

- PDU Router (PduR): Routes the incoming message to SecOC to add security information to the 
  PDU.

- SecOC modules get services like crypto algorithms, keys etc. from Csm (Crypto Service 
  Manager) and crypto modules.
  

- **Authentic I-PDU**: Data from Com to PduR and that data going to SecOC module called as 
  authentic I-PDU

- SecOC performs MAC operations with the help of CSM modules and send backs the plain text+ 
  freshness value+ MAC back to the PduR. This is called **Secured I-PDU**.

- Thus secured I-PDU can be send to the lower layers based on commn. protocols.

# How does SecOC work

- Consider 2 ECU : Sender(ECU1) and Receiver ECU(ECU2)

- ECU1 consist of a MAC generator 

- The inputs to this MAC generator are the data, key and freshness value

- Freshness can be a counter or a start time stamp 

- MAC is generated out of this and is appened to the outgoing secured IPDU and send to the 
  receiver ECU

- At ECU2 the verification process happens

- The key will be already stored in the internal memory of each ECUs

- So the MAC generator gets the input that is the data and freshness value from incoming 
  message and generate the MAC again it will verify the MAC with the received MAC for 
  correctness.

- If it does not match that particular message will be discarded

- If matches the data or message is said to be non-tampered and will be sent to the upper 
  layers.

- CAN has 8 byte of data frame which is limited and appeneding this security info. can lead to 
  having lesser data. Thus there is a feature called **secure pdu collection** in SecOc.

- In secure pdu collection the data and the security content are separately send but for 
  verification both messages should be received. 

- But in Ethernet there is no limitation for data frame so we can send all in one single 
  message.
 

  
