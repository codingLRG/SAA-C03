Utilize subscriptions to track events
- Select source type
	- Specify parameter group
- Select event type
- Select target
	- [[SNS]]
	- Note: [[SQS]] is not a valid target

Fanout Event Notification
- A [[SNS]] topic gits sent
- A message filter sends individual messages to different [[SQS]] queues
- The [[SQS]] queue triggers the consumer (ie. [[Lambda]], [[ECS]])
