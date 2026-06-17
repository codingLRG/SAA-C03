Suite of services for [[AWS]] and on-site
Metrics repo from [[AWS]] services and custom metrics
Monitors and notifies based on threshold 
Triggers on thresholds
Some services in CloudWatch:
- Metrics
	- Data that describes performance of applications
	- 1 minute service data update time by default for most [[AWS]]
		- [[EC2]] is 5 minutes, unless detailed monitoring is enabled, then its 1
- Logs
	- Monitor, store, access, analyze or query
	- Install CloudWatch Logs agent to [[EC2]] to publish logs to CloudWatch
	- Types of logs:
		- Vended Logs
			- [[VPC]]
			- [[Route 53]]
		- Published by [[AWS]]
			- Most [[AWS]] applications
		- Logs from on-premises server
			- [[CloudWatch]] Agent
			- PutLogData API
- Alarms
	- Alarms for specific threshold
	- Notify using [[SNS]]
	- Trigger custom actions
		- Autoscale
		- Alerts
		- Invoking [[Lambda]]
- Events
	- Monitors and responds in near real time
	- Create a CloudWatch Event rule to track the state of your services
	- Invoke certain action
	- Scheduled job to invoke [[Lambda]]
	- [[EventBridge]] have the same underlying services and API but [[EventBridge]] has more features
	- The difference between Alarms and Events is Alarms are metrics based and Events are system events based
- Dashboards
	- Monitor your resources in a single view
