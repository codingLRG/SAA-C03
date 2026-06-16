---
aliases:
  - Standby Replica
---
> Standby Replica

Very useful for mission critical applications
- If required to eliminate single point of failure

Can not be in different [[Region]]
- No multi-[[Region]] disaster recovery

Failover duration only lasts about a minute
- Changes CNAME to point to other [[RDS Multi-AZ Deployments|Standby Replica]]

Primary uses:
- Provides high availability
- Improves redundancy
- Minimizes latency spikes during backups

Internal Steps:
- Take a snapshot of primary DB instance
- Launch new [[RDS Multi-AZ Deployments|Standby Replica]] in different [[Availability Zone]]
- Configure synchronous replication

[[RDS]] uses internal [[EC2]] 
Maintains DB performance while regular process of patching DB engine due to automatic failover
- If [[RDS Multi-AZ Deployments|Standby Replica]] is being patched, there is no disruption in performance

Also good for non-scalable architectures
Highly recommend to have both [[RDS Multi-AZ Deployments|Standby Replica]] and [[RDS Read Replica]]

Not suitable for short [[Recovery Point Objective]] and [[Recovery Time Objective]], this is [[Aurora]]'s job

Does not read or write application data or live traffic, so not a scaling tool