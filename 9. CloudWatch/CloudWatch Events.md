[[EventBridge]]

Events: Indicate changes in environment, can also be scheduled

Targets: [[EC2]], [[Lambda]], [[ECS]], [[SNS]] Topic, [[SQS]] Queue, Built-in Targets (API Calls)
- Should be in the same [[Region]] as the event rule

Integrated Services:
- [[CloudTrail]]
	- Captures API calls
- [[CloudFormation]]
	- Declare event rules in templates
- [[Config]]
	- Detect and react to changes in the status of events
- [[IAM]]
	- Send [[SNS]] whenever user is created or deleted via API
- [[Lambda]]
	- Set as target when creating event rule