General
- Name
- [[Availability Zone]]
	- [[Region]]al
	- One [[Zonal]]
- Automatic backups - enabled by default
- Lifecycle management
	- Transition to ==I==nfrequent ==A==ccess
		- Transfer in: Days since last access
		- Transfer out: On first access or none
- Performance mode
	- General for most, Max IO for big data analysis
	- Can test by using General, and check PercentIOLimit metric, if at 100, use Max IO
		- Will need to create a new file system and migrate with [[DataSync]]
- Throughput
	- Bursting - Scales with system
	- Provisioned - Fixed amount
- Encryption
- Tags

Network Access
- [[VPC]]
- Mount targets
	- All [[Availability Zone]] mounted if selected [[Region]]al

File system policy
- Prevent root access by default
- Enforce read-only access by default
- Prevent anonymous accessing
- Enforce in-transit encryption for all clients

Click attached and mount using DNS name