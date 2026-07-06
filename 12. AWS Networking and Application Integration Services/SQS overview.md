[[SQS]]
Good for decoupling architecture for asynchronous workload processing
[[Consumer]]s 
Adjustable settings:
- Visibility Timeout
- Message Renetion Period
- Delivery Delay
- ==RECEIVEMESSAGE== Wait Time
- Access Policy
	- [[IAM User]], [[IAM Role]], [[AWS]] account

[[Dead-Letter Queue]]
[[Delay Queue]]
[[Temporary Queue]]

Supports encryption [[In-Transit]] (by default) and [[At-Rest]] 

[[EC2 auto scaling]] dependent on:
- Age of oldest message (can have target tracking policy)
- Queue depth
- Number of messages


| Service             | Integration Name              |
| ------------------- | ----------------------------- |
| [[Lambda]]          | Lambda Trigger                |
| [[SNS]]             | Fan-Out Event Notification    |
| [[S3]]              | S3 Event Notification         |
| [[ECS]] and [[EKS]] | Inter-container Communication |
