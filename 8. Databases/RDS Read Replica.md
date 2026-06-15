Primary Node: Source
Secondary Node: Replica

Synchronous Replication: 2-Way Replication
- Used for Standby Replica to increase redundancy

Asynchronous Replication: 1-Way Replication (Primary to Secondary)
- Used for Read Replica to increase durability and availability

| Standby Replica                                             | Read Replica                                        |
| ----------------------------------------------------------- | --------------------------------------------------- |
| Does not accept live traffic without failover               | Can accept live traffic                             |
| Cannot be seen in [[RDS]] Console as a separate DB instance | Can be seen as separate DB instance                 |
| DB Endpoint is the same as the primary DB instance          | DB Endpoint is different as the primary DB instance |
[[Binary log]]
Can be launched:
- Same [[Region]] as primary DB
- Different [[Region]]

Can be changed to read_only in parameters group
- Must reboot DB instance to apply changes

Read Replica can be promoted to primary
- Database sharding
- Failure recovery
- Performing [[Data Definition Language]] operations

Cannot encrypt a Read Replica from a non encrypted DB source
- Cross-[[Region]] encryption is possible via [[KMS]] being supplied

Read Replica Use-cases:
- Offloading heavy read tasks from primary DB 
- Separate read requests from write requests

Cannot be used for ensuring DB availability during outage
- Multi-[[Availability Zone]] deployment configuration for this feature
- Read Replica does not automatically failover if primary DB is out in a different [[Region]], this feature is only available for Standby Replica

Promoting Read Replica to primary node is possible, but takes considerable time to deploy
- [[Aurora]] is suitable for this as it usually takes under 1 second to deploy