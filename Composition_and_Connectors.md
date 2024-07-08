- We need to know about this when we're working in the application layer of AUTOSAR.

- Compositions: A software component type that aggregates s/w components or compositions. Its's a 
  container that can hold group of s/w components.

- Connectors: Used to complete the connections b/w port prototypes.

   - Assembly Connector: Connects a provider and rxvr port
   - Delegation Connector: Connects the same port types to delegate ports to outer composition


# Example
Let's take a sw that has sender rxvr and client server commn. with 2 provider and 2 rxvr ports. We shall place them under a composition called as composition 1. To connect these 2 ports we can use assembly connector. **Assembly Connector** is used to connect 2 ports within the same composition. Now let's consider another s/w component in the system swc 3. This is placed inside composition2. Composition 2 encapsulate composition1 also. Composition can have components and compositions.

The rule for using an assembly connector is that the ports to be connected from s/w components should have same parent compositions.

Here sw3's port cannot connect with sw1's and sw2's port through assembly connection because sw1 and sw2 have parent composition1 and for swc-3 parent is composition2.

Thus we will extend the existing ports to outer composition using delegation connector swc1 and 2 for this we will make use of delegation sw connector.

Assembly connector connects a provider and rxvr ports.

Delegation connector connects the same type either provided to provider or rxvr to rxvr.
