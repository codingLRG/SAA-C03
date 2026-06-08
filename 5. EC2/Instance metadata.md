A manifest to each and every VM regarding to the instance
Also controls specific [[AWS]] services a particular instance can access via [[IAM]]
- [[Vocabulary/AMI|AMI]]
- Hostname
- Public and Private [[ip address]]
- [[EC2 Instance Type]]
- MAC
- [[Security Group]]
- Security credentials
- [[IAM Role]] for instance

[[Instance Data Service]] (session layer option available for extra security, 1 sec min, 6 hour max)
Retrievable via:
- Linux: curl
- Windows: Invoke-RestMethod -uri

Append option to [[Instance Data Service]] retrieve method for info