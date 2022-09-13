## VL2: A Scalable and Flexible Data Center Network (2009)
Date: Sep 13, 2022
---- 
### Novel Idea
Propose a new network paradigm called VL2, which scales to support huge data centers with uniform high capacity between servers with L2 semantics.

**Motivation: Network is bottleneck to data center computation**

### Today’s DCN(data center networks) problems:
- traffic independence
- tree architecture leads to congestion and computation hot spot
	- limited capacity (oversubscribed ToR - top of rock switch)
- ip config complexity in migration
- tradeoff between reliability and utilization
- fragmentation of server pool
- further burden to involve humane interaction to reassign servers


### Design needs:
 - accommodate to volatile property
- high utilization, cost effective
- handle hot spot
- no need to over provision
- *agility* , ability to assign server to another service

### Design of VL2:
VL2 is named after virtual layer 2, it is virtual because servers in layer2 have independent IP addresses so they provide an illusion for applications with **flat address space**, compared to traditional tree topology it is less hierarchical and less complicated. 
ASes are connected to intermediate switches. ToRs directly connect to ASes which locate in layer 3, a different addressing spaces. L2 switch is flatter and extensible compared to the traditional tree structure network topology. The addressing method in VL2 is L2 addressing, which requires an additional layer in the communication stack. The address resolution is based on table-query, not traditional ARP, which could reduce the traffic. 
Some properties:
- give each service an illusion that all servers assigned to it are connected by a non-switching ethernet switch *virtual layer* (L2 switch)
- location specific IP (public)
- application specific IP (private)
- Clos topology - built with Locator addresses (LA) and application addresses (AA)
- Valient Load Balancing (VLB) to spread out load

Idea of L2 switch: every server connected to other servers in this same network
Kind of similar to the idea of link layer -\> every device is connected to same physical link

- Use multiple path routing to scale out topologies in L2 (instead of tree)
	- very easy routing
	- can have hash collision

### VL2 workflow in action
First an application sends a packet destined to another AA. The VL2 agent will intercept the ARP and converts it to a unicast query to the VL2 directory system for the corresponding LA. 
The LA hashing has *two* levels. First is AA to TOR LA. Second is ToR LA to INT LA. 
Decoupling of the address encapsulation is along from INT router to destination ToR. The hashing could map the flow to different switches, so as to achieve the load balancing. In order to support the directory system, the servers should be maintained. There are two types of directory servers, one is read-optimized look-up server, another is write-optimized RSM servers, and caching is used to speed up the queries. 

### Why VL2?
- LB randomized to deal volatility
- Based on proven networking technology
	- link-state routing
	- equal cost multi path (ECMP) forwarding
	- ip anycasting
	- ip multicasting
- Simple migration with static AA (compared to human labor)

### Evaluation && Conclusion
- provides TCP fairness, perf isolation, high utilization, hotspot free
- simple abstraction for servers