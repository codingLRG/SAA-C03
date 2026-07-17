[[Security Group]] and [[Network ACL]]
Both:
- Created by default with [[VPC]]
- Acts as virtual firewall
- In out rules that can have one IP or [[CIDR Block]] as source

[[Network ACL]] -> [[Availability Zone]] -> [[Security Group]] -> [[EC2]]

[[Network ACL]] works at [[Subnet]] level

[[Network ACL]] -> Blacklist
[[Security Group]] -> Whitelist

[[Network ACL]] -> rule number
[[Security Group]] -> no rule number

[[Network ACL]] -> can't inherit from other ACL
[[Security Group]] -> can use [[Security Group]] as source