Metric Alarm
- Single [[CloudWatch]] metric

Composite Alarm
- Alarm based on multiple other alarm states

Receive notifications when metric or alarm fall outside of threshold

Specify:
- [[Period]]
- [[Evaluation Periods]]
- [[Datapoints to Alarm]]
- [[Conditions]]

States:
- OK
- ALARM
- INSUFFICIENT DATA

Actions:
- [[SNS]] topic
- Configure resources