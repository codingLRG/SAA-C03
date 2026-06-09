---
aliases:
  - Elastic Block Store
  - EBS Volumes
---
> Elastic Block Store

Persistent block-level storage service
- Will not get lost in case instance was stopped, restarted or terminated
Mounted to [[EC2]] instances
- Multiple EBS instances can be attached to a single [[EC2]]
[[Zonal]]
Can be [[encrypted at rest]] using [[KMS]]

[[EBS types]]

Faster data retrieval than:
- [[S3]]
	- but [[S3]] is cheaper
- [[EFS]]
	- but [[EFS]] and [[FSx for Lustre]]/[[FSx for Windows File Server]] can modify the same file at the same time in multi instances
