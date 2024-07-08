# Gateway in AUTOSAR

- A signal, a signal group or a pdu rxvd from one source bus is transmitted over another destination bus.

- The gateway of signal, signal group or pdu can be over 2 buses communicating over a same or different protocol.

- AUTOSAR Gateway functionality consists of 2 parts:

1. Gateway functionality on pdu level (pdu based gateway): Provided by the pdu router module

2. Gateway functionality on signal level(signal based gateway): Provided by the signal gateway which is integral part of COM

# Signal Gateway

- Signal level gatewaying happens through the COM module in AUTOSAR.

- Once a gateway rvs a signal or signal group for gatewaying, it immediately acts as a sender of that signal.

- The config. of the gateway is done as a part of ComGwMapping container.

# PDU Gateway

- Happens through the pdur module in autosar.

- Gatewaying in pdu after the complete pdu is rxvd is called as **direct gatewaying**.

- Transmitting the pdu when a configures number of bytes are rxvd without the complete pdu being rxvd is called as **gatewaying on the fly**.
