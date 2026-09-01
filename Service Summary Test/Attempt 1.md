# Analytics
- [x] [[Athena]]: Suite of analytical tools that prompt via sql queries
- [x] [[CloudSearch]]: create a search domain feature
- [ ] [[Data Pipeline]]: automate the movement and transformation of data
- [ ] [[EMR]]: also lets you transform and move large amounts of data into and out of other AWS data stores and databases, such as [[S3]] and [[DynamoDB]].
- [ ] [[ES]]: seach feature utilizing [[Elasticsearch]]
- [ ] [[Glue]]: [[Serverless]] [[ETL|Extract, transform and load]] service, mainly used for [[Athena]]
- [ ] [[Kinesis]]: Data process streaming suite, record, analyse and send for cheap
- [ ] [[Lake Formation]]: Data lake for machine learning
- [ ] [[QuickSight]]: AI buisiness insight overview with interactable dashboard
- [ ] [[Managed Streaming for Apache Kafka]]: [[Apache Kafka]] bs
# App Integration
- [ ] [[AppFlow]]: [[SaaS]] integration tool
- [ ] [[AppSync]]: Integration with [[GraphQL]]
- [ ] [[EventBridge]]: Event buses recieve an event and forward to 0 or more targets and pipes are single target 
- [ ] [[MQ]]: [[Apache ActiveMQ]] message broker
- [x] [[SNS]]: Publish topics and targets subscribe
- [x] [[SQS]]: Queue service that sends to multiple targets with requeing in case of host failure to process
- [x] [[Step Functions]]: [[Lambda]] state machine
# Audit and Compliance
- [ ] [[Artifact]]: fancy compliance records
- [ ] [[CloudTrail]]: API audit tracking
- [x] [[Organization Trail]]: User audit tracking
- [x] [[Security Hub]]: overview of security recommendation and posture
# Compute
- [x] [[Batch]]: large batch process job handler
- [x] [[EC2]]: the main cloud computadora
- [x] [[Elastic Beanstalk]]: web developer compute, good for dynamic and static websites
- [x] [[Lambda]]: [[Serverless]] compute
- [ ] [[LightSail]]: pre-configured cloud resources
- [ ] [[Outposts]]: Run [[AWS]] infrastructure and services on premises
# Container
- [ ] [[A2C]]: Java and .NET to containers
- [ ] [[Copilot]]: Similar to [[A2C]]
- [ ] [[ECR]]: [[Docker]] registry
- [x] [[ECS]]: [[Docker]] container
- [x] [[EKS]]: [[Kubernetes]] container 
- [ ] [[Fargate]]: [[Serverless]] for containers
# Database
- [ ] [[Aurora]]: [[AWS]] DB engine with highest scalability
- [ ] [[DocumentDB]]: DB for [[MongoDB]], [[NoSQL]] esq
- [x] [[DynamoDB]]: [[NoSQL]] [[Serverless]] DB
- [ ] [[ElastiCache]]: Caching for DBs
- [ ] [[Keyspaces]]: [[Apache Cassandra]]
- [ ] [[Neptune]]: Node based DB
- [ ] [[QLDB]]: Crypto ledure
- [ ] [[RDS]]: Relational Database Service, SQL based hosts
- [ ] [[Redshift]]: Data warehouse
- [ ] [[Timestream]]: Easy-to-manage time-series databases
# Deployment
- [x] [[CloudFormation]]: [[Infrastructure as Code]] 
- [ ] [[CodeDeploy]]: slow rollout with ease to revert changes
- [x] [[ECS Anywhere]]: on site [[ECS]]
- [x] [[EKS Anywhere]]: on site [[EKS]]
- [x] [[EKS Distro]]: [[EKS]] distro store
- [ ] [[OpsWorks]]: Streamlining devops with automated lifecycle
- [x] [[Proton]]: dead after october so who cares
# Identity
- [ ] [[Cognito]]: enables main providers as sign in (sign in with Google, Facebook)
- [ ] [[Directory Service]]: [[AWS]] Active Directory service, integration with [[AD Connector]]
- [x] [[IAM]]: [[IAM User]] is an account, [[IAM Group]] is a group of [[IAM User]], [[IAM Role]] is a not an account however still grants access to outside parties
- [x] [[SSO]]: Single sign on
# Machine Learning
- [ ] [[A2I]]: build the workflows required for human review of ML predictions
- [x] [[CodeGuru]]: suite of tools for development
- [ ] [[CodeWhisperer]]: VS Code AI coding assistant (ew)
- [x] [[Comprehend]]: Read document and pull sentement
- [ ] [[DevOps Guru]]: offload the administrative tasks associated with identifying operational issues
- [x] [[Forecast]]: predictive model base on previous usage
- [x] [[Fraud Detector]]: fraud detector base on irregular use of application or account
- [ ] [[Kendra]]: intelligent search service that uses natural language processing
- [ ] [[Lex]]: chatbot
- [ ] [[Lookout for Metrics]]: business anomoly detection
- [ ] [[Lookout for Vision]]: physical anomoly detection
- [ ] [[Personalize]]: Youtube recommendation, Amazon shopping recommendation, etc
- [x] [[Polly]]: Text to speech
- [x] [[Rekognition]]: Visual recognition of person or item of photo or video
- [ ] [[SageMaker]]: Suite for training ML models
- [x] [[Textract]]: pull text from non text file 
- [x] [[Transcribe]]: audio to text and insight
- [x] [[Translate]]: language translation tool
# Management and Governance
- [x] [[CLI]]: [[AWS]] terminal
- [x] [[Config]]: enforce consistent policies across services
- [ ] [[Console Mobile Application]]: [[AWS]] management mobile application
- [ ] [[Control Tower]]: multi [[AWS]] account service management
- [ ] [[Management Console]]: web console
- [ ] [[Organization]]: centralize multiple [[AWS]] accounts
- [ ] [[RAM]]: share services across [[Organization]]
- [ ] [[Service Catalog]]: service catalog
- [ ] [[SSM]]: service manager
# Monitoring
- [x] [[CloudWatch]]: view service hardware utilization
- [ ] [[Health API]]: events and system outages via API
- [ ] [[Personal Health Dashboard]]: events and system outages
- [ ] [[Service Health Dashboard]]: overall health of [[Region]]
# Networking and Content Delivery
- [ ] [[API Gateway]]: creating, publishing, maintaining, monitoring, and securing REST, HTTP, and WebSocket APIs at any scale
- [ ] [[App Mesh]]: microservice communication
- [ ] [[Cloud Map]]: use to map logical names to the backend services and resources that your applications depend on
- [x] [[CloudFront]]: content caching for distant [[Region]]s
- [ ] [[Direct Connect]]: Onsite to [[VPC]] connection service
- [x] [[ELB]]: Handles traffic load and distributes best it can across multi targets
- [x] [[Global Accelerator]]: to improve the performance of your applications for local and global users
- [ ] [[PrivateLink]]: private connectivity between VPCs, AWS services, and your on-premises networks, without exposing your traffic to the public internet.
- [x] [[Route 53]]: DNS routing table
- [ ] [[Transit Gateway]]: network transit hub used to interconnect virtual private clouds (VPCs) and on-premises networks
- [ ] [[VPC]]: virtual private cloud
- [ ] [[VPN]]: virtual private network
# Security
- [x] [[ACM]]: Store and manage SSL certificates
- [ ] [[CloudHSM]]: Hardware security model in the cloud
- [ ] [[Detective]]: investigate attacks post mortom
- [ ] [[Firewall Manager]]: manages firewall rules across multiple [[AWS]] accounts
- [ ] [[GuardDuty]]: manage threat detection, not prevention
- [ ] [[Inspector]]: app vulnerability detection
- [x] [[KMS]]: Store and rotate encryption keys
- [ ] [[Macie]]: detect sensitive data via ML
- [x] [[Secrets Manager]]: Store and rotate secret credentials
- [x] [[Shield]]: DoS attack, get advanced if anticipating DDoS
- [x] [[WAF]]: SQL injection attacks
# Storage
- [x] [[Backup]]: automatic backup of [[AWS]] services
- [x] [[EBS]]: elastic block storage for fast data reads on [[EC2]], non [[ephemeral]]
- [x] [[EFS]]: [[POSIX]] file storage for linux
- [x] [[FSx for Lustre]]: [[POSIX]] for [[Lustre]]
- [x] [[FSx for Windows File Server]]: [[POSIX]] for Windows
- [x] [[S3]]: Mass object storage, pretty dope
- [x] [[S3 Glacier]]: Archive object store
- [x] [[Storage Gateway]]: on site file storage to [[AWS]]
# Transfer and Migration
- [ ] [[Application Discovery Service]]: investigation tool for pre migration from on site to cloud
- [ ] [[DataSync]]: online data transfer
- [ ] [[DMS]]: other migration service that sees full availability
- [ ] [[Migration Evaluator]]: more planning
- [ ] [[Migration Hub]]: more planning
- [ ] [[SMS]]: Automate, schedule and track incremental replications
- [ ] [[Snowball Family]]: physical data move service
- [ ] [[Transfer Family]]