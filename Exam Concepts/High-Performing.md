# File Storage
## [[EFS]]
> Sharable across [[EC2]], performant file system
- [[EBS]] can only be mounted to one [[EC2]]
- [[ec2 instance store]] can only be mounted within the [[EC2]] itself, can not be shared
- [[S3]] is not a file system, it is a object store, can not be mounted to [[EC2]]
## [[S3]]
> If you need a system with both file sharing and versioning capability out of the box for the cheapest, [[S3]] is the way to go
- [[EFS]] and [[EBS]] are not the way to go simply because versioning is not something they support by themselves
	- [[EFS]] is mainly useful for [[POSIX]]
	- [[EBS]] is for low latency storage
## [[EBS]]
> [[EBS]] enables operating system access, so in instances where the application needs to install certain files to operate a Oracles Database server, [[EBS]] is the way to go
- For fast storage, [[EBS types]] SSD are a must
- For cheap storage, magnetic works
- [[RDS]] works with Oracle DataBases, however it does not have operating system access
- [[DynamoDB]] is a [[NoSQL]] DB, Oracle is a relational DB

## FSx for...
> [[FSx for Windows File Server]] is best used for SharePoint file storage migration with [[AD control]]
- [[EFS]] does not natively integrate with [[AD control]]
- [[SMB]] on [[Storage Gateway]] does not integrate with [[AD control]]
- [[S3]] mounted on a Windows Server does not integrate with [[AD control]]
- With [[FSx for Windows File Server]], [[FSx File Gateway]] is not needed

> [[FSx for Lustre]] handles all underlying infrastructure, maintenance and backups, qualifying as being fully managed
- [[Storage Gateway]] is not fully managed, as you would need to manage the [[EC2]]
- [[EFS]] is not configurable to [[Lustre]], only [[NFS]]


# Minimal Overhead
## Data Processing
> Utilizing [[S3]] as a data storage, [[Lambda]] for function and [[Aurora]] for result storage, this minimizes overhead and provides scalability that is highly available
- Using an [[EC2]] instead of [[Lambda]] will require managing and scaling servers
- [[EBS]] and [[EC2]] are less scalable and available than [[S3]] and [[Lambda]]
- [[SQS]] and [[ECS]] add more complexity as opposed to [[S3]] and [[Lambda]]

> To transfer objects from one [[S3]] to another via [[Lambda]] and upload the data to [[SageMaker]] at the same time, using an [[EventBridge]] can automate any new files entering the initial bucket, as this will trigger the [[Lambda]] and [[SageMaker]] to act 
- Utilizing [[Lambda]] to check if new items are in [[S3]] will require [[Lambda]] to poll the [[S3]], which is more manual configuration than needed
- [[S3 replication]] requires manual configuration

> To store and access data in real time through an API, utilizing [[API Gateway]] and [[Lambda]] is the way to go
- [[Athena]] and [[QuickSight]] is for analytics, not really suited for real time usage
- [[Data Analytics]] is for streaming data sources, not utilizing an API
## [[Athena]]
> For advanced analysis on logs and build visualizations, utilize [[Athena]] for SQL queries on the [[CloudFront]] logs store in an [[S3]] for analysis, and [[QuickSight]] for visualization
- [[Glue]] is for [[ETL|Extract, transform and load]], not analytics
- [[DynamoDB]] is a [[NoSQL]], so it can not handle SQL queries, which [[QuickSight]] relies on
## [[Elastic Beanstalk]]
> [[Elastic Beanstalk]] primary use is for [[Serverless]] web development that also [[High-Performing#Increasing Performance|optimizes performance]] 
- [[EC2]] have a ton of overhead if you want a public webserver
- [[CloudFormation]] is for infrastructure specifically
- [[S3]] can host static websites, but not optimal for web dev because code can not be deployed in [[S3]]
## Application Segregation
> Utilize [[ECS]] to break up an application into microservices via containers, and set up a [[ALB]] to provide high scalability and minimizing overhead
- [[Lambda]] can not break an application into microservices
- [[Amplify]] is a web app tool, not containerizing
- [[EC2]] requires more overhead than [[ECS]] to scale and manage
# Increasing Performance
## [[ALB|Application Load Balancer]] and [[EC2 auto scaling]]
> If an application performs best at a specific hardware utilization, [[EC2 Auto Scaling types#Target Tracking|Target Tracking]] can dynamically adjust the number of instances 
- [[EC2 Auto Scaling types#Simple Scaling|Simple Scaling]] may cause fluctuate as they are threshold based
- [[Lambda]]s require additional logic while [[EC2 Auto Scaling types#Target Tracking|Target Tracking]] handles this automatically
- [[EC2 Auto Scaling types#Scheduled Scaling|Schedule Scaling]] is an option, however this can not be set to track hardware

> If a web application utilizes its own companies's SSL certificate and [[EC2]], utilizing a [[ALB]] with a [[HTTPS]] listener looking at a [[ACM]] with the SSL certificate can handle SSL encryption/decryption capacity consumption
- Installing the SSL on each [[EC2]] will not address the capacity consumption for the encryption and decryption
- Moving the SSL cert to a [[S3]] will not offload the encryption/decryption load
- Utilizing a proxy [[EC2]] will not address the capacity consumption issue, as a single [[EC2]] is still handing the encryption/decryption

> For migrating on premises to Cloud for transaction drop resistance, use [[SQS]] for messaging between [[EC2]] in an [[Auto Scaling Groups]], monitor [[SQS]] queue length with [[CloudWatch]] and scale up on failure
- [[Lambda]]s would be more complex and expensive as [[SQS]] are designed for asynchronous messaging
- [[SNS]] does not have queue length monitoring for [[EC2 auto scaling]]
- Performance history would over-provision resources instead of utilizing [[EC2 auto scaling]]
## [[NLB|Network Load Balancer]] 
> [[Global Accelerator]] can be used to connect applications across ==different continental== [[Region]]s (Europe to US) by creating [[endpoint group]]s for the specific [[Region]]s, and add [[NLB]]s as the endpoints
- [[Route 53 routing policies#Geolocation]] will not route traffic to all continental [[Region]] instances
## [[S3]] Direct Upload
> [[S3]] support direct upload via pre signed URLs, this will reduce server usage to upload to [[S3]].
## [[CloudFront]]
> To enable caching media files so users around the world can access the files faster, utilize [[CloudFront edge servers]]
- [[Global Accelerator]]s are for applications specifically, not media
- [[DataSync]] is for data transfer between services, not for end users
- [[S3]] would not improve performance or user experience
- Increasing [[EC2]] would only assist with more concurrent users, not with individual performance

> Cost-effective solution that provisions infrastructure on demand and scales automatically globally
- [[Lambda]] and [[DynamoDB]] do not address scaling and performance
- [[ALB]] and [[EC2 auto scaling]] address scaling, but do not address performance optimization
- [[Route 53]] with internal [[ALB]]s don't provide global delivery

> Invalidating [[CloudFront]] cache will force fetch latest version of website files from [[S3]] 

> Best for static sites now getting global attention, utilize [[Route 53]] records to point [[CloudFront]] distributions
- [[Global Accelerator]] is way more expensive, but better for web applications
- [[S3]] duplication across regions with [[Route 53 routing policies]] is more complex and expensive
- [[S3 Transfer Acceleration]] is for client to [[S3]] not [[S3]] to client

## [[CloudWatch]]
> To set up alerts to monitor multiple hardware utilization, with minimal false alerts, [[composite alerts]] are the solution
- Single [[metric alarm]] with multiple thresholds would lead to more false positives as it would go off if one of the hardware flags are triggered
- [[Cloudwatch Dashboard]] is good for visualization, no automation however
- [[CloudWatch Synthetic]] is for monitoring application availability and performance, not metrics
## [[Gateways]]
> For important files to experience low-latency leverage [[Gateway-Cached]] 
# Network
## [[CIDR Block]]
> Takes up range /16 to /28 inside a [[VPC]]
> [[AWS]] reserves 5 IP addresses from block (first 4 and last)
1. Network Address
2. [[VPC]] Router
3. [[DNS Server]]
4. Reserved for future use
5. Broadcast address
## [[DataSync]]
> [[Direct Connect]] allows for private connection across [[AWS]] services and [[DataSync]] for data transfer of large, sensitive data
- for the love of god, do not transfer sensitive data over the internet
- [[DMS]] is good for databases, however [[DataSync]] is better for [[S3]]

## [[SQS]]
> To minimize duplicate messages, adjust [[ReceiveMessage]] wait time API
- [[ChangeMessageVisibility]] actually makes the situation worse as more hosts are able to read the message and process it when an instance fails
- [[MessageGroupID]] can assign a ID to each message to prevent duplicate message but ordering is lost

> [[DelaySeconds]] is a [[SQS]] API setting that hides from consumer interfaces when a new message is added to the [[SQS]] queue

> [[Glue]] can prevent reprocessing old data by utilizing [[Job Bookmarks]]
- Deleting data after processing would result in the data being reprocessed every time the job is ran
- [[NumberOfWorkers]] does not effect reprocessing
- [[FindMatches]] does not prevent reprocessing processed data, only duplicates in data set

> [[WaitTimeSeconds]] makes the [[SQS]] service wait a certain amount of time for one or more messages to be available before closing the connection
# Database
## [[Aurora]]
> [[Aurora]] provides the largest database capacity of 128TB compared to any other [[RDS]] engine, with fastest read replica, with replica lag being under 120 milliseconds 
## [[IOPS]]
> [[IOSP]] SSD storage provides more consistent latency than GP2 for insert heavy workloads

## [[RDS Read Replica]]
> [[RDS Read Replica]] allow traffic to be separated from write traffic, enables to be scaled horizontal. 
- [[RDS Multi-AZ Deployments]] do not stop reads from coming from primary [[Availability Zone]], only useful for [[Origin Failover]]
- To prevent bottle necking, [[RDS Read Replica]]s should be deployed with the same compute as source

## [[RDS Multi-AZ Deployments]]
> For [[Recovery Point Objective|RPO]] less than 1 second will be achieved by enabling [[RDS Multi-AZ Deployments]]
- [[Auto Scaling Groups]] does not provide high availability or data replication
- [[RDS Read Replica]] do not provide [[Recovery Point Objective|RPO]] of less than 1 second [[RDS Read Replica#Read Replica Use-cases|Use Cases]] 
- [[DMS]] does not provide [[Recovery Point Objective|RPO]] of less than 1 second

> For increased performance during production data staging