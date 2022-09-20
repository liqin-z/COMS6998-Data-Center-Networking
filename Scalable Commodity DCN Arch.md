## A Scalable, Commodity Data Center Network Architecture
---- 
### Current Problem
- single point of failure
- oversubscription of links high up in topology
- edge for switch, core, cable cost is too high
### Current Solution
1. leverages specialized hardware and communication protocol (infiniband)
	- can scale with high bandwidth
	- too costly
2. Leverages commodity ethernet switch and router to interconnect cluster machines
	- scale poorly
	- non linear cost increase with cluster size
### Design needs
1. Backwards compatible with existing infra
2. Cost effective
3. Allows host communication at line speed

### Clos Networks & Fat-Tree
The fat tree network is a universal network for provably efficient communication
- Fat tree has identical bandwidth at all bisections 
- Provides great scalability
- Fat tree is easily built
Existing routing protocol:
- OSPF
- OSPF-ECMP
Not available, need to address
- Congestion on traffic
- avoid Congestion
Enforce a new IP scheme -\> two level look up to distribute traffic && maintain packet order (prefix and suffix).
