[[Network ACL]] for [[Subnet]], [[Security Group]] for [[EC2]]

| Default Network ACL                  | Custom Network ACL                   |
| ------------------------------------ | ------------------------------------ |
| Exists by default                    | Have to create                       |
| Can be modified                      | Can be modified                      |
| Allows all in out traffic by default | Denies all in out traffic by default |
Lowest num rule is read first
[[Network ACL]] table:

| Rule # | Type (web traffic) | Protocol (TCP/UDP) | Port range | Source | Allow/Deny |
| ------ | ------------------ | ------------------ | ---------- | ------ | ---------- |
[[Ephemeral ports]]
Linux range:
- 32768 - 61000
Windows:
- 1024 - 65535
- 49152 - 65535

A [[EC2]] can have more than 1 [[Security Group]] 
[[Security Group]] cannot have an explicit deny, only explicit allow
[[Security Group]] table:

| Source | Protocol | Port Range | Description |
| ------ | -------- | ---------- | ----------- |

Common needed ports:
- 22 - SSH
- 80 - HTTP
- 443 - HTTPS
- 445 - [[SMB]]
- 1433 - MSSQL
- 3306 - MySQL
- 3389 - RDP


| Default Security Group                                                                            | Custom Security Group                               |
| ------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| Exist on your default [[VPC]]                                                                     | Have to manually create                             |
| Has one inbound rule and one outbound rule                                                        | Has a default outbound rule that allows all traffic |
| Automatically attaches to [[EC2]] if non specified                                                | Has no default inbound rule                         |
| Automatically allows incoming traffic from any resource that also uses the default security group | Denies all inbound and outbound traffic by default  |
| Allows all outgoing traffic that originated from the instance                                     |                                                     |
Linux: 
```bash
iptables -nL INPUT --line-numbers
```

Limitations
- Can not be applied to [[S3]]
- Does not prevent Cross-Site Scripting or SQL Injection attacks
- For geolocking, use [[WAF]] instead

[[VPC Flow Logs]] to assist with debugging