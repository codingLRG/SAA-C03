
# Private communication
## [[Security Group]]
> Allows services such as [[EC2]]s and [[Database]]s in separate private [[Subnets]] to communicate to one another
- Can also deny traffic from each other
- [[Peering connection]] allows complete communication between each [[Subnet]] as if they were one, however this can lead to unwanted ability to connect between services in separate [[Subnets]]
- There is no need to add services to a public subnet nor allow any traffic to any port, big no no

> To allow access to a bastion host on a public subnet within the internal network: update the security group to allow access from the internal ip range
- Access via external IP reduces security

> To allow access to a private server on a private subnet within the internal network: connect to the bastion host first, then allow access from the bastion's private ip
- Access via bastion's public ip reduces security
- Access via network's private ip does not allow the bastion host to negate unwanted connections
## [[CIDR Block]]
> [[AWS]] reserves ==5 IP addresses== from block (first 4 and last) for each [[VPC]]
1. Network Address
2. [[VPC]] Router
3. [[DNS Server]]
4. Reserved for future use
5. Broadcast address
## [[VPC Endpoint]]
> Good for privatizing [[VPC]]s from public internet and allowing connection to other private [[AWS]] services
- Can connect to other [[AWS]] services, including [[S3]]
- [[S3]] can not utilize [[API Gateway]]s to communicate
- [[IAM]] profiles do not isolate communication from internet
- [[Route 53]] is for [[DNS]] resolution, so basically only good for domain names
- A [[NAT Gateway]] would route through the internet
- [[Site-to-Site VPN]] would still go through the internet
- [[IAM User]] can grant access to too much access to services if stored on [[EC2]]

> To allow access across applications, a [[IAM Role]] is necessary to the service using the principle of least privilege
- Do not allow oupbound connectivity through network [[ACL]] as this exposes the application to the public internet
- Do not embed access keys in applications
## [[HoL - Connect to instance with EC2 Instance Connect]]
> Allow inbound traffic on port 22 (SSH) to your network to connect via SSH
- During [[VPC]] creation, create a [[VPN]] connection
- No need to make a public subnet
- [[NAT Interface]] needs to be connected, however this should also occur during [[VPC]] creation
## [[VPC]]
> Secure connection across [[VPC]]s with no single point of failure or bandwidth bottlenecks can occur with a feature called [[Peering connection]]
- [[VPC Endpoint]]s does not allow complete communication, only supported services can utilize this feature
- [[Virtual Private Gateway]]s are only one way, not bidirectional, so the connection has a single point of failure
- [[Private virtual interfaces]] are also only one way, so the same issue applies
- [[Security Group]] allowing traffic from the public IP of the [[VPC]] unnecessarily exposes the [[VPC]] to the internet
- For the love of god, don't assign the resource a public ip if you want it to be private
- A [[EC2]] proxy that forwards wanted request needlessly adds complexity and security risks 

# Least privilege
## [[FSx for Windows File Server]]
> For existing AD integration with permissions in tact, you can join the [[FSx for Windows File Server]] to the on-premises AD
- [[AD Connector]] does not inherit permissions
- Tagging would require recreating the permission
- [[IAM]] service link role also does not assist with permission integration
## [[Security Group]]
> Utilize [[Security Group IDs]] to enable rules between application tiers
- [[Instance IDs]] allow access to those instances, and if the instance is compromised, then all allowed connections from that instance is also accessible for the users assigned to that instance
- [[VPC]] [[CIDR Block]] is too broad, allowing access to the whole [[VPC]], as oppose to the specific applications within the [[VPC]]
- [[Subnet]] [[CIDR Block]] is also too broad, allowing access to the whole [[Subnet]]
## [[WAF]] and [[Shield]]
> [[WAF]] is utilized for protecting against exploits on web applications (such as SQL injection or XSS)
> [[Shield]] is utilized for protecting against DDoS attacks (such as SYN or UDP floods)
- [[GuardDuty]] is a detection service
- [[Shield]] has multiple tiers, if expecting large scale, go advanced
## [[S3]] access
> Adjust [[S3 Bucket Policy]] to limit access to users
- [[CloudTrail]] is for logging, not policy enforcement, this can be confused with [[Config]] 
- Indivdual tagging is possible to set access to user, however if all users are a part of an [[Organization]], that can be used instead and will be less overhead
## [[IAM]]
> [[IAM Role]] is good for temporary access for vendors as there is no long term credentials provided
- [[IAM User]] have permanent credentials
- Adding the vendors [[IAM User]] to the [[IAM Group]] shares permanent credential and group permissions
- Creating a new identity provider is used to authenticate users, not grant access

> [[IAM Role]] can be attached to preexisting [[EC2]]s and does not require a reboot to apply
# Encryption at rest and in transit
## [[S3]]
> Server-side encryption allows for data to be encrypted while uploaded (transit) and stored (rest)
- [[S3]] encryption with [[KMS]] allows for encryption at rest, but not in transit
- Client-side encryption only addresses at rest data, the data is encrypted, however the communication is not
- [[S3 Bucket Policy]] can enforce encryption, but ==this does not actually encrypt the data or communication itself==, an important distinction
## [[NLB|Network Load Balancer]]
> Utilize listener rules to redirect traffic from [[HTTP]] to [[HTTPS]]
- Rules replacing [[HTTP]] to [[HTTPS]] in the url does not address the issue of requests coming on port 80 ([[HTTP]])
- [[Network ACL]] blocking port 80 denies service, which is not what we want for [[HTTP]] requests
- [[Server Name Indication]] is a solution to redirect [[HTTP]] to [[HTTPS]], however [[NLB]]s can do this as well, and does not warrant replacing entirely
## [[CloudFront]]
> To protect sensitive user data during submittion, configure field-level encryption in [[CloudFront]]
- Signed URLs restricts data access, but there is no encryption
- Signed cookies also restricts data access, but provides no encryption
- Policy enforcement over HTTPS does not encrypt data
## [[KMS]] and [[ACM]]
> [[KMS]] can encrypt at rest, [[ACM]] can encrypt in transit (roles can not be switched)
-  Using the root account to enable encrypt at rest and in transit is terrible for security, but technically possible
- BitLocker can encrypt data at rest for Windows Servers, however has no integration to [[KMS]] so security keys can not be stored

> [[KMS]] provides automatic rotation option and logged when used, allowing use to be audited
- Server side encryption doesn't log usage
- [[S3 managed keys]] are not automatically rotated
- [[KMS]] can also be manually rotated
# Accidental deletion
## [[S3]]
> To prevent accidental deletion of data with an [[S3]], [[MFA Delete]] and [[Versioning]] can be enabled
- This method still allows deletion, just prevents accidental deletion, to prevent deleting all together, utilize [[S3 Object Lock]]
- [[MFA]] on [[IAM User]] is good for security, but does not address accidental deletion
- [[Lifecycle policy]] can not prevent data from being deleted prematurely, only automates transitions of objects over time
- Encryption and restricting access to the bucket does not address accidental deletion

> To prevent unwanted changes, [[Config]] can enforce the right rules while monitoring specific changes
- [[Trusted Advisor]] does not prevent changes, it is used for recommendations for:
	- Save money
	- Improve system availability
	- Close security gaps
- [[Inspector]] is for [[EC2]]s, not [[S3]]s
- Server access logging does not prevent changes to the bucket, only logging (hence the name)
- [[EventBridge]] or [[CloudWatch Events]] can trigger alerts on log events, but this does not detect unauthorized changes

> [[S3 Object Lock]] has two modes, [[Compliance mode]] and [[Governance mode]]
> Both very similar, however [[Compliance mode]] has a very strict no files can be deleted compared to [[Governance mode]], which allows designated users to modify and delete
- To ensure a file is not modified or deleted, utilize a [[legal hold]]
- [[IAM Role]] can not make [[S3]] objects immutible
- Don't use a [[Lambda]] to track hashes for the love of god

> Only the owners of a bucket can delete items in a [[S3]], this includes public buckets
# Securing credentials
## [[Secrets Manager]]
> User credentials can be safely stored within [[Secrets Manager]] to access services, including [[AWS]]es. 
> Credentials can also easily be updated regularly via automation. 
> Enabling [[Multi-Region secret replication]] allows for credentials from different regions to be saved and updated.
- [[SSM|Systems Manager]] is for managing [[EC2]] automated creation, can not store secrets
- [[S3]] can store secrets, especially if the bucket is encrypted (please for the love of god), however credential update automation is not a available feature
- Utilizing [[KMS]] locally on each server adds a security risk as the servers get exposed access to the keys locally
## [[KMS]]
> Primary use case is to easily create, manage and control encryption keys
- [[ACM]] is for SSL/TLS certs
- [[IAM Policy]] can help control key access, this does not handle the creation and managing of the keys
## [[Organization]]
> The term "Owner" refers to the Root account
- [[IAM Role]]s do not change this terms meaning

> Secure access to Root user, [[MFA]] and using a strong password is the best course of action
- Storing password in an encrypted [[S3]] opens risk of keys being retrieved
- Assigning root to [[IAM Group]] does not remove full admin access that root has
# Patching
## [[EC2]]
> For system patching from [[EC2 auto scaling]], utilize [[bootstrap]]ping script that installs the latest updated
- Ensure that the update process is immediate and not manual
- This patching is not automatic by default, action will be needed
- 