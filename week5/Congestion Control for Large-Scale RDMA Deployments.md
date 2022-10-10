## Congestion Control for Large-Scale RDMA Deployments

Requirements: 
- cloud storage apps require high networking bandwidth
- distributed memory caches and large scale machine learning needs low latency message transfers

Current Models:
- TCP/IP doesn’t satisfy the requirements, high CPU overhead
- Kernel bypass stack like RDMA requires good Congestion control (CC) to scale large networks

This paper:
Addressing congestion control for RoCE networks.
RoCE using priority flow control(PFC) to ensure lossless L2 network
- congestion spreading 
- unfair bandwidth
DCQCN:
- end-to-end CC at a per-flow granularity
- rate control, implemented in host NIC

Challenges with RDMA deployment in Data centers:
- ECN and PFC thresholds chosen in share membership switches to ensure ECN marking generated prior to PFC
- fast convergence
- fairness
- rate stability
	- Using parameters
