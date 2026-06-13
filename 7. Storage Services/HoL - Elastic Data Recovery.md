[[Elastic Data Recovery]]
Cost based on replicating source servers
- Replications servers: lightweight [[EC2]] instances that are used to replicate data between your source servers and [[AWS]]
- Specify volume and [[Security Group]]
	- Replicate new disk automatically is an optional feature
	- [[EBS]] has 3 options, 2 SSD and 1 HDD (cheaper)
	- [[EBS]] encryption
	- Recommend to use [[AWS]] default security group for [[Elastic Data Recovery]]
		- Can use custom in order to manage data recovery
- Configure additional replication setting
	- Control data routing and throttling
	- Configure snapshot retention in days
	- Add [[MAP]] for cost optimization
- Default [[DRS]] launch setting
	- Option for how hardware for instance is selected
	- Instance setting such as start on launch, copy private ip and transfer server tag
	- Licensing for Windows Desktops and Linux servers
- Default [[EC2]] launch template
	- Set subnet, [[Security Group]] and [[EBS types]]