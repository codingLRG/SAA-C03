# Default [[VPC]]
Default in each [[Region]]
Can be immediately used to launch [[EC2]], [[ELB]], [[RDS]] and other resources
172.31.0.0/16, [[CIDR Block]]
Important to consider number of available host for auto scaling
# [[VPC]] with single public [[Subnet]]
Good for hosting a public website like a blog
# [[VPC]] with public and private [[Subnets]]
Good for front facing public web app with private DB not intended for public
# [[VPC]] with public and private [[Subnets]] and Hardware [[VPN]] Access
For extending your onsite into [[AWS]] with [[Site-to-Site VPN]]
- Supports v6 to an extent, can't support v6 for [[Site-to-Site VPN]] connections
# [[VPC]] with single private [[Subnets]] and Hardware [[VPN]] Access
Same as above but with no public facing access