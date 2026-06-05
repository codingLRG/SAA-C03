# Creating a Subnet
Navigate to 1. [[VPC]] > [[Subnets]] > Create subnet
- IPv4 VPC CIDR block is the range of ip to divide from
- IPv4 subnet CIDR block is the slice of the block

Private -> NAT Gateway (Routing Table per subnet)
Public -> Internet Gateway (Group all subnets to the same gateway)

Delete VPC:
- Delete NAT
- Delete VPC
- Delete Elastic IPs

VPC and more allows to create a whole [[VPC]] with a few clicks