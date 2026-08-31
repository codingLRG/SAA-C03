# Time To Live Data
## [[DynamoDB]]
> [[DynamoDB]] can have it's time to live to automatically expire data over a set age
- Utilizing a separate monitoring tool will incur extra costs
- [[DynamoDB Streams]] will require extra coding to achieve the same effect
## [[S3 Lifecycle]]
> When storing log files that generates high volume (+10TB a month), [[S3]]'s provide the best price. For files older than a set time (a month) that are expected be no longer needed immediately, they can be moved to [[S3 Glacier|S3 Deep Glacier]]
- [[Backup]] can do the same transfer from [[S3]] to [[S3 Glacier]], however since the data is already in [[S3]], [[S3 Lifecycle]] makes more sense to use
- [[CloudWatch]] can store logs, but not to the level of high volume or retention time needed for this
- [[Lifecycle policy]] require the data to originate in [[S3]], [[Backup]] will be needed to move from [[CloudWatch]] to [[S3 Glacier]]

> If time elapsing leads to expected data access to decrease, a [[Lifecycle policy]] that transitions from [[S3 storage classes#Standard|Standard]] to [[S3 storage classes#Standard-IA|Standard-IA]] 
- [[S3 storage classes#Intelligent-Tiering|Intelligent-Tiering]] incurs higher cost than [[S3 storage classes#Standard|Standard]] as it monitors access patterns, the benefit is if data access is irregular
- [[S3 Inventory]] provides visibility into objects, doesn't handles transitions
# Storage Options
## [[S3]]
> For non database files like JSON holding data, with high accessibility (miliseconds), using a [[S3]] is best cost-effective option
- [[OpenSearch]] is overkill
- [[S3 Glacier]] is for long-term storage, not highly accessible
- [[RDS]] is not optimized for storing JSON files

> [[S3]] is less expensive than [[EBS]] or [[EFS]], so in most cases for data storage and you are looking to save on cost, especially long-term storage, [[S3]] is the answer

## [[EBS]]
> For cheap encryption at rest, configure the drive for encryption upon creation
- When the application is writing the data, that data is not at rest
# Expected Usage
## [[Reserved Instances]]
> [[Reserved Instances]] are good for a service that needs to run 24/7, mission critical, with the ability to commit for a extended amount of time (1 year)
- [[Spot Instances]] - goes down, terrible for mission critical applications, good and cheap for interruptible processes
- [[On-Demand EC2 Instances]] - Most expensive option per hour, if the app needs to run 24/7 there is no benefit to using this
## [[EventBridge]]
> In the event where a service needs to be started and stopped at expected times that has no built in scheduler, [[Lambda]] and [[EventBridge]] is the cheapest option to start and stop the service
- In the case of [[RDS]], there is no automatic start and stop feature
- Using an [[EC2]] is significantly more expensive, but possible to achieve the same effect
## Development environment
> When introducing a dev environment into your [[EC2 auto scaling]] group, reducing the maximum number of allowed instances is the most cost effective solution because dev environments will not be receiving that much traffic
- Having only one [[EC2]] instance in dev environment is not advisable as there would be no high availability or fault tolerance
## [[EC2 Auto Scaling types]]
> [[EC2 Auto Scaling types#Scheduled Scaling|Schedule Scaling]] is best for anticipated workloads and bypassing [[Instance warmup]]
- [[Auto Scaling Groups]] capacity does not effect [[Instance warmup]]

> If users are reporting an application is slow in the morning, monitoring CPU threshold and decreasing [[Cool Down]] period can assist via [[EC2 Auto Scaling types#Step Scaling|Step Scaling]]
- [[EC2 Auto Scaling types#Scheduled Scaling|Scheduled scaling]] can work, however setting desired capacity before anticipated usage will cause unuse usage unless declared afterwards
- [[EC2 Auto Scaling types#Target Tracking|Target Tracking]] can scale too aggressively
## [[CloudWatch alarms]]
> [[Application Auto Scaling]] with target tracking to scale when [[CloudWatch alarms]] metric is breach is best for reducing cost during peak periods followed by traffic decreases
- [[Lambda]] requires writing custom code, which is unnecessary
- [[EC2 Auto Scaling types#Simple Scaling|Simple Scaling]] scale only in one direction

# One Time Events
## [[SNS]]
> [[SNS]] is the most cost-effective for one-time text message for confirming registration
- [[Security Token Service]] requires a web service that enables you to request temporary access
- [[EC2]] is possible, but WAYYY more complicated to do this use case, plus way more expensive
## [[Direct Connect]]
> In the event of transferring from onsite to [[AWS]] data warehouse, hosting the [[Direct Connect]] link in the same [[Region]] as the warehouse and access the link is the lowest cost (free)
- Do not host on-site and query as public internet transfer cost will eat you alive
- Basically if the answer has internet or query anywhere in it, that's the ==WRONG== answer
## [[Spot Instances]]
> Utilizing [[Spot Instances]] for burst traffic that raises above capacity is a good idea for handling traffic above your baseline
- [[On-Demand EC2 Instances]] is not price effective, but immediately available. Good for flexibility of no long-term commitment and per-second billing.
## [[Redshift]]
> For monthly reporting, [[Redshift]] is a good way to optimize large analytic workloads due to using a separate data warehouse
- Larger instance class would increase performance, but less cost effective
- [[RDS Multi-AZ Deployments|Standby Replica]] would have the same performance characteristics as the primary
## [[Lambda]]
> For infrequent API calls, using [[API Gateway]] targetting a [[Lambda]] can be the most cost effective way for to return a [[RESTful]] response
- [[ECS]], [[LightSail]], [[EC2]] are all needed to be ran continuously

> Developer needs to run code without provisioning or managing servers? [[Lambda]]
- [[API Gateway]] can't run code
- [[S3]] can't run code
- [[EC2]] needs to be provisioned and managed
# Cost Analysis
## [[Cost Explorer]]
> Provides pre-built reports to analyze cost by different services, users, or resources.
- [[Athena]] requires creating queries, [[Cost Explorer]] does this automatically
- [[Billing Dashboard]] only shows total costs, not cost breakdown
- [[HoL - Budgets|Budgets]] is for alerts, not analysis
## [[Trusted Advisor]]
> To reduce [[RDS]] costs, [[Trusted Advisor]] can make recommendations to the billing account and check for instance optimization
- Does not check for idle instances
- Does not make recommendations for the accounts where the instances are running