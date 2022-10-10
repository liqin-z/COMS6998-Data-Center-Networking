## Data Center TCP (DCTCP)

Current Problem:
- Existing TCP protocol let large burst packets drop
- Wasted buffer, adds significant latency
- TCP is still widely used in most cloud service providers
Solution: DCTCP
- leverages ECN to provide multi-bit feedback to end hosts
- less buffer space used
- high burst tolerance and low latency for short flows

Microsoft Bing:
- measured 6k server production cluster
- 150t compressed data 
	- delay-sensitive
	- throughput-sensitive

Impairments:
- incast
- queue buildup
- buffer pressure
Goal: Low queue occupancy & high throughput

Key Idea:
1. React in proportion to congestion. Not its presence
2. Mark based on instantaneous queue length

Algorithm:
- Switch: mark packets when queue length \> k
- Sender: maintain running average

Conclusion:
1. Handle burst well
2. Keep queue delay low
3. High throughput
