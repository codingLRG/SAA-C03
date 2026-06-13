Since [[EBS]] console does not provide automated management backup on the fly
Replaces need to create custom [[Lambda]] functions 
Can create backups, move backups to different accounts for [[Disaster Recovery]] and delete old backups to save on costs

Create a policy
- [[EBS]] snapshot
	- for existing [[EBS]]
- [[EBS]]-backed [[AMI]]
	- [[AMI]]s that are backed with a single or multiple [[EBS]] volume
- Cross-account event
	- copying shared snapshots across [[AWS]] accounts

Define the tags
Define the schedule and frequency
Define retention
