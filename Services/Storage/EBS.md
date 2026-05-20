---
aliases:
  - Elastic Block Store
  - EBS Volumes
---
> Elastic Block Store

Persistent block-level storage service
Mounted to [[EC2]] instances
[[Zonal]]
Can be [[encrypted at rest]] using [[KMS]]

| Type | Use Case            | Dominant Performance Attribute     | Boot Volume for EC2? |
| ---- | ------------------- | ---------------------------------- | -------------------- |
| SSD  | Frequent read write | Input/Output operations per second | Yes                  |
| HDD  | Data achive         | Throughput                         | No                   |
> Types
- General Purpose SSD
- Provisioned IOPS SSD (can be attached to multiple [[EC2]] at the same time)
	- EBS Multi-Attach (only allowed for [[Nitro]]-based instances of [[EC2]])
		- Cannot modify same file at the same time in multi instances
			- If feature needed, use [[EFS]]
- Throughput Optimized HDD
- Cold HDD

Faster data retrieval than:
- [[S3]]
- [[EFS]]

