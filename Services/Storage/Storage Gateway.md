Connects on-premises applications and data storage to [[AWS]]

File Gateway:
- Store and retrieve in [[S3]]
	- [[NFS]] and [[SMB]]
- Can be integrated with AD
- Provides hardware appliance hosted on-site

Volume Gateway:
- Block storage to on-premises apps with low-latency via [[iSCSI]]
- Uses [[S3]] for point-in-time snapshots of [[EBS]]
- Cached mode:
	- Stores subset of frequent data
	- [[S3]] storage
- Stored mode:
	- Entire dataset
	- Asynch backup

Tape Gateway:
- Uses [[S3]] to backup tapes
	- Archives can be [[S3 Glacier]] (or Deep Archive)
- On premises connect tape gateway as [[iSCSI]] devices
- Reduces cost by eliminating physical tapes

If planning to migrate onsite to cloud entirely, then use [[DataSync]] instead