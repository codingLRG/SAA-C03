Enable [[EC2]] that are in private [[Subnets]] to connect to the public
Prevents the public Internet from initiating connections

| NAT Instance                                      | NAT Gateway            |
| ------------------------------------------------- | ---------------------- |
| Virtualized NAT running in [[EC2]] within [[VPC]] | Not running in [[VPC]] |
| Managed by you                                    | Managed by [[AWS]]     |
| Not highly available/scalable                     | Is highly...           |
NAT gateway is associated with a [[Availability Zone]], implementing redundancy is recommended