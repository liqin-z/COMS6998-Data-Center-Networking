## dcPIM: near-optimal proactive datacenter transport

Transport design for DCN
- low latency: for short flows
- high throughput: for long flows

To achieve near-optimal latency for short flows
- connection-less design
- packet priorities
- per-packet load balancing
- fast loss recovery

Long flows may contend with short flows / other long flows in-network / at-host

dcPIM transport based design
- matching: each sender is paired with a unique receiver, vice versa
- near optimal throughput for long flows
- near optimal latency for short flows

PIM:
- no hardware
- randomized: simple, robust
- log(n) rounds of matching

dcPIM:
- scales up to DCN scale
- high larger RTT in DCN
- allow each sender/receiver to match with multiple receiver/sender
- token clocking mechanism

Results:
- converge quickly to high network utilization 
- achieve higher network utilization than theoretical bound

