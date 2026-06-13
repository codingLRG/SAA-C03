---
aliases:
  - EBS Volume Type
---
[[EBS]]

| Type | Use Case            | Dominant Performance Attribute     | Boot Volume for EC2? |
| ---- | ------------------- | ---------------------------------- | -------------------- |
| SSD  | Frequent read write | Input/Output operations per second | Yes                  |
| HDD  | Data achive         | Throughput                         | No                   |
> Types
- General Purpose SSD
	- Recommended for most workloads, most cost effective
	- Configurable and consistent IOps
- Provisioned IOPS SSD (can be attached to multiple [[EC2]] at the same time)
	- Mission-critical, low-latency or high-throughput workloads
	- Sub-millisecond latency
	- Where DB storage is bottleneck
	- EBS Multi-Attach (only allowed for [[Nitro]]-based instances of [[EC2]])
		- Cannot modify same file at the same time in multi instances
			- If feature needed, use [[EFS]]
- Throughput Optimized HDD
	- Low cost for frequently accessed, throughput-intensive workloads
- Cold HDD
	- Lowest cost, meant for data store for infrequently used data