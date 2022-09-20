## PortLand: A Scalable Fault-Tolerant Layer 2 Data Center Network Fabric
---- 
### Goals
- scalable layer 2 routing, forwarding and addressing
- plug and play switch deployment
### Design
- Assume existing fat-free topology
- switch know their location in topology
### Requirements
- Any VM can migrate to physical machine
- No config required for deploying switches
- efficient communication between host and DCN
- No forwarding loop
- Rapid failure detection

### Fabric Manager (FM)
- Centralized user process on dedicated machine
- Maintain soft state of network config
### Positional Pseudo MAC address (PMAC)
Format: `pod.position.port.vmid`
Unique to every end host
- Ingress switch sees a new MAC
- AMAC and IP mapped to new PMAC in local table
- FM stores mapping for use in ARP response
- Egress switch adds flow table to rewrite PMAC to AMAC address
### Proxy-based ARP
- FM reduces ARP overhead
- ARP msg intercepted by edge switch and forwarded to FM

### Label Distribution Protocol (LDP Algorithm)
A protocol in which routers capable of Multiprotocol Label Switching (MPLS) exchange label mapping information. Two routers with an established session are called LDP peers and the exchange of information is bi-directional. LDP is used to build and maintain LSP databases that are used to forward traffic through MPLS networks. LDP can be used to distribute the inner label and outer label (path label) in MPLS. For inner label distribution, targeted LDP (tLDP) is used. 

Forwarding: Switch forwarding tables are populated using neighbors topological positions.

Implementation: FM is using OpenFlow (a communications protocol that gives access to the forwarding plane of a network switch or router over the network.)
