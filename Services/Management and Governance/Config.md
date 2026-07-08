Assess, audit and evaluate
Automates compliance assessment
Provides visibility on the existing configs
[[Region]]al in scope
- Multi-account and multi-[[Region]] data aggregation by using an [[Aggregator]] 

Identify changes and compares to Config Rules
- Triggered periodically or configuration change-based
- [[CloudWatch]] Events and [[Lambda]] to maintain realtime updates
- Can configure a rule to message an [[SNS]] based on requirement

Can automate compliance with [[SSM|Systems Manager]] Automation document

| [[AWS]] Managed Rule                                    | Custom Rule                                                          |
| ------------------------------------------------------- | -------------------------------------------------------------------- |
| Predefined but customizable rules that [[AWS]] provides | Rule that is associated with [[Lambda]] function that you've created |
