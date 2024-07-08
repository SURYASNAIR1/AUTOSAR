Need when working with ASW.

# What are Runnables 

Runnables are the smallest code fragments that are provided by the component

Individual functions that are on a SWC.

Each function in C file need to be defined as runnable in AUTOSAR configuration and should specify the interface within it. The runnables with the events are scheduled by the OS.

# Rules with Runnables
- Runnable swc or a parameter swc cannot  have a runnable since they don't have an associated c 
  file functionality within them.

Runnable is defined inside the tag called Runnable entity.

# Configure RTE to communicate msgs
- Explicit: just pass msg from ports

- Implicit: create dedicate msg buffer for each rxvr, data read and write access is take care 
  here      

# What are Events

- Additional configuration to runnable to specify the OS on when and how to call the runnables.

- Runnables are mapped to the RTE events and further the os and the RTE layer together ensure 
  that the runnable function is called in the expected manner.

# General Events

Events that are common 

- Init Event: if the runnable is used to be called once and runnable is just for the 
  initialization during startup

- Timing Event: Used when we need the OS to call the runnable in a timing period

- External Trigger Occurred Event:  Used when we runnables need to be triggered

- Internal Trigger Occurred Event: Used when we runnables need to be triggered

- Background Event: Used for runnables that need to be run at background

# Client Server Events

Used when client requests the server execution through a synchronous or Asynchronous call
- Operation invoked event

- Asynchronous server call result event

# Data Events
- Data write complete event: is associated with provider port

- Data send complete event: is associated with provider port

- Data receive event: is associated with receiver port. Used for core runtime 
  initialization.

- Data receive error event: is associated with receiver port. Used for core runtime 
  initialization.

# Mode Events
- Mode switch event

- Mode manager error event

- Mode switch ack event










