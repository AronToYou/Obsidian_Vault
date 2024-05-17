## NIC (Network Interface Controller/Card)
- Physical & Data Link layer device acting as a network endpoint
- Identified by a MAC address
## MAC (Medium Access Control) Address
- For use as a network address in communications within a **Network Segment**
- Devices in different **Network Segments** may share the same MAC address
## ARP (Address Resolution Protocol)
- Determines the Layer 2 Data Link (MAC) address associated with a Layer 3 Internet/Network address (IPv4)
# Network Segments
- **Layer 1 Segment**s: 
	- **Electrical Segment**: Networked devices sharing a single shared electrical medium. e.g. a coax cable tapped by multiple devices
	- **Collision Domain**: One or many **Electrical Segments** joined by repeaters.
- **Layer 2 Segments**:
	- Multiple Layer 1 segments joined together by **bridges** or **switches** (aka **Broadcast Domain**), enabling communication between any 2 nodes via MAC addressing or broadcasts.
	- Can be divided into **VLAN**s (Virtual LAN).
- **Layer 3 Segments**:
	- **Subnetwork**: An IP Network where all nodes share the same network prefix and mask.
	- A **Router** is required for communication between Layer 3 segments.
## 5-4-3 Rule (roughly)
- A half-duplex Ethernet **Collision Domain** can have no more than 5 *segments* and 4 *repeaters* in series, of which no more than 3 may be *mixing segments* (the rest must be *link segments*).
	- *Segment*: A single electrical non-repeated medium.
	- *Mixing Segment*: A segment based on a single connection (half-duplex) medium (in other words, a single wire) between 2 or more devices.
	- *Link Segment*: A segment based on a point-to-point (full-duplex) medium between exactly 2 devices.
	- *Repeater*: A device with many ports for connecting *segments*; which upon receiving a signal into a port, repeats the signal at the output of every port except for the receiving port. 
## NAT (Network Address Translation)
- Translation between IP address spaces across routing devices.
	- **Router**: Connected to 2 or more data lines from different IP Networks (**Layer 3 Segments**).
	- An address is translated either directly via a **Routing Table** or recursively via a **Routing Policy**.
	- **One-to-Many NAT**: Nodes on a private network all share the router's single public address. The router tracks who in the private network has opened which connections to the internet in order to correctly route back received traffic.

## SNMP (Simple Network Management Protocol)
Based on **(UDP) User Datagram Protocol**.
### Players
### Managers or Administrative Machines
#### (NMS) Network Managment System
##### (PDU) Protocol Data Unit
##### (MIB) Management Information Base
Made up of **(OID) Object Identifier**s which are used to interpret trap messages.

### Managed Devices
#### SNMP Agent
##### Traps
Defined in RFC 1215 of Internet Engineering Task Force
###### coldStart
###### warmStart
###### linkUp \ linkDown
Monitors the port operating status of a switch (or SNMP Client). E.g. when an ethernet cable is plugged in \ unplugged respectively.

###### authenticationFailure
###### egpNeighborLoss
###### *Enterprise-specific traps*

### Versions
#### SNMPv1
#### SNMPv2c