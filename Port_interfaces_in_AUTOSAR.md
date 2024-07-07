- Port Interfaces : The highest level of description of information exchanged b/w components in an AUTOSAR system. 

- Component used by SWC to communicate.

# 2 types:
  - P PORT (Provider PORT)
  - R PORT (Receiver PORT)
 
# Two communication methods used in AUTOSAR
- **Client-Server Mechanism:** 

- P PORT is used to provide the operation defiition (SERVER).
                             
- R PORT is used to invoke the operations (CLIENT)

- The client initiates the commn. and request a service from the server

- Server performs the request service and sends a response to the request 

- SWC can act as client and server in different commn.

- **Server-Receiver Mechanism:**

- P PORT is used to send the data out (SENDER)

- R PORT is used to read the data (RXVR)

- Sender does not expect any answer from the receiver and ther'll be no answer thus the sender is not blocked. The receiver decides on its own how and when to act on the received information.

# Example to understand these 2 methods
- Consider heating controller as the ASWC, 2 heating coils and 1 led dial as the sensor and actuator swc. The heating controller and the heating coil sw are connectde via the client server interface. The heating controller and led dial swc are connected via sender rvxr interface. So here whenever the heating controller needs to get the temp. info. from the heating coil , the heating element which is acting as a client will request for the service and the coil will act as the server which serves the requested service by responding to the service request but in case of info. to the led dial the requirement is just to send the info. or data about the heating coils to led dial for displaying so a sender rvr interface is used the heating controller which is the sender will send the data directly to the led dial which is the rxvr.








 
