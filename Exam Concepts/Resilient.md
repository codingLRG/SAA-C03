# High availability
## [[EC2 auto scaling]]
> [[Auto Scaling Groups]] are able to be assigned to multiple [[Availability Zone]]s to provide redundancy, allowing for high availability without modifying the application code
- Creating separate [[Auto Scaling Groups]] in different [[Availability Zone]]s does not provide high availability without modifying the application code, as now the traffic will have to be shifted
- Using [[Lambda]] to automatically switch does not provide real-time high availability and would also require changes to the code to work

# Networking
## [[Route 53]]
> Utilizing [[Route 53 routing policies#Geolocation|Geolocation]] can eliminate connecting to the wrong continental environment to resolve language barrier

> [[Route 53 routing policies]] include:
> Simple, Failover, Geolocation, Geoproximity, Latency-Based, Multivalue Answer, Weighted
- Geolocation cannot dynamically shift traffic from one [[Region]] to another, use Geoproximity routing instead
- Geoproximity is not fully capable of reducing Internet latency, use latency-based routing instead
	- If app is expecting millions of users, use [[CloudFront]] or [[Global Accelerator]]
## [[Amazon EC2 networking]]
> [[Elastic IP address]]es remain associated with the instance, even after shutdown

> [[NAT Gateway]]s allow connecting your public subnet your private subnet with high availability, keeping your private subnet private, while enabling internet connectivity
- [[Internet Gateway]] will make the private subnet public, this should be connected to your public subnet
- [[NAT Instance]] will not allow for high availability unless you utilize multiple, however this can add up in cost
- [[VPC Endpoint]] allows private connectivity from an [[AWS]] service, not the internet

## Failure Recovery
> In the case of data failing to arrive due to network connection issues, requiring manually running the process again, configure the retry settings to increase the number of retries and longer wait time
- Multiple [[Availability Zone]] deployment would not help as the notification would still fail process when a network issue occurs
- Caching the data would not ensure the data is eventually processed

> For [[EC2]] DB automatic failover, launching [[EC2]] instances in different [[Availability Zone]]s, configure the instances as a cluster with DB replication
- Using failover in different [[Region]]s will cause higher latency
- Avoid utilizing only 1 [[Availability Zone]] as this makes it less resilient to zone-specific disruptions
- [[AMI]]s is a backup image, not a failover option

> For [[RDS]] automatic failover, utilize [[RDS Multi-AZ Deployments]] to copy data synchronously
- This only works with one active one standby, +3 deployments does not exist
- [[S3]] versioning is not a DB service

> [[CloudFormation]] is [[Infrastructure as Code]] allowing to deploy a replica of existing architecture and infrastructure into a different region in minutes
- [[CloudFront]] is for media caching, [[CloudTrail]] is for auditing, [[CloudWatch]] is for monitoring services, [[CloudSearch]] is for searching on a website, [[CloudHSM]] is for SSL Processing
- [[EC2]], [[AMI]] and [[EBS]] handles [[EC2]] replica deployment, however this doesn't handle any other service in your architecture
- [[Elastic Beanstalk]] can not be used to deploy infrastructure in a different region


## [[SQS]]
> For sending messages between application that have a high throughput and in the case the processing fails, the messages must be retained for 2 days while not impacting the process of other messages, [[SQS]] fits this use case
- [[EC2]] utilizing [[Redis]] does not retain messages for failed processes
- [[Kinesis]] has limited throughput and does not have built-in support for retaining failed messages
- [[SNS]] topics do not have retaining failed messages capability for up to 2 days

> Some effects of [[SQS]] standard queue are that the queue does not serve the order they are generated in due to multiple hosts handling the queue, with each host not waiting for the order to be completed, and if the host does not finish the message, it is recent back into the queue

> A [[SQS]] can be utilized to store from [[EC2]] to a DB like [[RDS]] while automatically processing order if an outage happens
- Using [[SNS]] with a [[Lambda]] attached to a topic would add needless complexity and cost
- [[ALB|Application Load Balancer]] would not assist if the system were to go down
- Utilizing a [[ECS]] targeted by a [[EventBridge]] would require a refactoring the [[EC2]]

> [[SQS]] can be retained for up to 14 days

> Enabling long polling by setting the [[SQS]] config to ReceiveMessageWaitTimeSeconds will reduce CPU cycles compared to short polling, which will return empty responses
- The max wait time is 20 seconds

> [[SQS]]s can assist with processing [[SNS]] notifications to a [[Lambda]] by persisting the messages even if the [[Lambda]] fails to process the notification

> Coordinating jobs across servers by utilizing a [[SQS]] and [[EC2 auto scaling]] for compute nodes based on [[SQS]] queue size is the most efficient way to handle variable workloads
- Better than scheduled scaling
- [[CloudTrail]] does not enable decoupling or scaling capabilities
- Using just [[EC2 auto scaling]] does not account for variable compute node's workload
# Migration
## [[Aurora]]
> Migrating from onsite to [[Aurora]], it is best to make a backup copy of the DB on onsite computer and then create an ongoing replication process between the DBs
- This ensures that the DB is available during replication and in sync
- A cut-over migration would make the original DB unavailable
- Utilizing [[S3]] to store snapshots would require [[Aurora]] to be updated manually, causing the DB not to be synchronized in real time

## [[FSx for Windows File Server]]
> In the case for a migration to a [[AWS]] file share, and the company is already utilizing Windows file shares, its best to utilize [[FSx for Windows File Server]]
- [[S3]] is a bad for a file system, its object storage
- [[IAM]] usage would change how users access files, which will change workflow
- [[EFS]] is Linux only
# Long-term
## [[S3]] modes
> To ensure documents are not overwritten or deleted while being encrypted with keys rotated out every year, utilize [[S3 Object Lock]] compliance or governance mode with the least amount of overhead
- [[SSE-S3]] and [[KMS]] require manual swapping of keys
- Can grant certain permissions to users to allow delete override
## [[Transcribe]]
> To record and analyze audio calls that can recognize multiple speakers and create transcripts, utilize [[Transcribe]]. To store for long duration, utilize [[S3]] long-term storage. To analyze from [[S3]], use [[Athena]]
- [[Comprehend]] is text analysis, [[Rekognition]] is visual extraction like text and faces, [[Translate]] is language translation, [[Textract]] is for text extraction
## Messaging and storing
> To send messages to users via SMS use either [[Pinpoint]], [[Connect]] or [[SNS]], to process and store for one year, [[Lambda]] is a way to go
- [[Lambda]] can store information for up to one year
- [[Kinesis]] can not store replies for 1 year
- [[SQS]] can not send SMS to users

## [[Backup]]
> [[Backup]] provides automatic scheduled backups, lifecycle management to transition backups to cold storage, and long term retention policies to meet requirements
- No need to write custom scripts for automation backups

# Encryption
## [[EBS]]
> [[EBS]] can not be encrypted after being created, only on creation
- Can create an encrypted snapshot of an unencrypted snapshot