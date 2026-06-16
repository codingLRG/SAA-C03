[[RDS]]
Prominent DB engines:
- [[Microsoft SQL]]
- [[MySQL]]
- [[MariaDB]]
- [[PostgreSQL]]
- [[Oracle]]
- [[Aurora]]

Can be deployed using:
- [[CloudFormation]]
- [[Management Console]]
- [[CLI]]
- [[RDS API]]

Hardware, patching and backups is managed by [[AWS]]
Can purchase a [[Reserved Instances]] of DB

Technically can be ran on [[EC2]] however all maintenance and backup is required by you
- Gain access to direct remote connection via [[SSH]]

Instead of modifying SQL config files depending on engine, modifying the database config is done via:
- Parameter Group
- Options Group

Can designated downtime window for patches and maintenance

Single [[Availability Zone]] (Primary) or multi [[Availability Zone]] (Standby -> Synch Replic. or Read Replica -> Asynch Replic.)

Suitable for constantly changing data

[[ACID]] compliant

Feature called [[Vocabulary/RDS Proxy]]