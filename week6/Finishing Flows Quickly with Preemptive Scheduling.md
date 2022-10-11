## Finishing Flows Quickly with Preemptive Scheduling
- Datacenter applications 
	- minimize flow completion time
	- meet soft-real-time ddl
- Existing: TCP, RCP, ICTCP, DCTCP
	- fair sharing
	- not optimal

Centralized Algorithm
- max sending rate of flow
- expected flow transmission time of flow I
> Whenever a network load changes, the centralized scheduler recomputes the flow transmission schedule.

Fully distributed implementation
- sender 
- receiver
- switch
Propagate flow info with explicit feedback in packet headers
- when feedback reaches the receiver, it return to the sender in an ACK packet

PDQ sender
- maintains state variable
	- current sending rate
	- switches who has stop the flow
	- flow ddl
	- expected flow transmission time
	- inter-probing time
	- measured rtt
- send packets with rate
	- send probe packet every rat
	- attach scheduling header
- when ack packet arrives
	- update by feedback, remain flow size, arrival rate

PDQ receiver
- copy scheduling header from data packet to its corresponding ACK
- Reduce if it exceeds processing capacity
	- avoid buffer overrun on receiver

PDQ switch
- maintain state about flows on each link
	- rcp does not require per-flow state
	- partial shift 
- decides whether to accept or pause the flow
- flow acceptance

Several optimization
- early start
- early termination
- dampening 
- suppressed probing