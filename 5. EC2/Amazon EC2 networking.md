# Allocating IP Addresses
[[ENI]]
Can attach multiple per one instance to improve bandwidth
ipv4 by default can't be disabled
ipv4 based on [[CIDR Block]]
Can connect via Internal DNS hostname:
- Looks like: ip-*==privateip==*.ec2.internal

[[Elastic IP address]]
Given External DNS hostname
- ec2-*==publicip==*.compute-1.amazonaws.com
Can associate [[Elastic IP address]] to [[NAT Gateway]]'s public subnet
Can associate [[Elastic IP address]] to [[NLB|Network Load Balancer]] per subnet

Can also use [[Enhanced Networking]] and [[EFA|Elastic Fabric Adapter]]