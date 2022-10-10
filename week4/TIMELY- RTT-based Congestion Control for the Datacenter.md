## TIMELY: RTT-based Congestion Control for the Datacenter

Congestion control in Datacenter signal: RTT
- fine-grained and informative
- quick response time
- no switch support need
- end2end metric

Performance requirements:
- tightly coupled computing tasks
- require high throughput & low latency
- packet loss too costly

Target: ECN -\> RTT
1. Show how to measure RTT accurately
2. Timely

Hardware assisted RTT Measurements:
1. Timestamps: migrate noises
2. Ack: avoid overhead
RTT is a multi-bit signal, correlates with queuing delay

TIMELY Overview
- RTT Measurement engine
- rate computation engine
- pacing engine -\> paced data
	- computes the send time using segment size, flow rate, time of last transmission

Set up
- small scale: incast traffic pattern with 10 clients and 1 server
-  few hundreds of machine in a classic Clos-network 
