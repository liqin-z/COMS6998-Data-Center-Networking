## Swift: Delay is Simple and Effective for Congestion Control in the Datacenter
Swift congestion control - delay based
- low-latency
- high utilization
- near zero loss
- large-scale incast

Why we need datacenter CC?
- New apps with low latency requirements 
- New stacks and new sources of congestions
- Increasing line-rates and robustness to heterogeneity

### Design
- end-to-end delay decomposition of a packet and its ACK
- Swift maintains 2 congestion-windows
	- fabric delay
	- endpoint delay
- Scaling of target-delay
- Loss recovery and ACK policy
- Coexistence via QoS

### Performance
- loss rate very small
- same cluster throughput as GCN
- can maintain avg fabric round-trip around the target config delay
- wide range of workflows



