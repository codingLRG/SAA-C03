Dedicated host:
- Hardware on rack is dedicated to single user
- Some software may have per-core requirements
- Good for launching Servers that are bound to particular VMs, sockets or physical CPU cores

Dedicated instance:
- Regular VMs that run in a [[VPC]] on hardware that's dedicated to a single user
- Isolated at a hardware level
- May share hardware with other [[EC2]] instances if:
	- In the same [[AWS]]
	- Not a type of dedicated instance
- Launch dedicated [[Spot Instances]], dedicated [[On-Demand EC2 Instances]], or dedicated [[Reserved Instances]]