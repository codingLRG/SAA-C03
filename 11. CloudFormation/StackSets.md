[[CloudFormation]]
[[Vocabulary/StackSets|StackSets]]
- Isolate critical resources
- Restrict resources to [[Region]]s or accounts
- Spread resources

[[Stack Instance]]

# Create StackSet
Specify [[The anatomy of a CloudFormation template||CloudFormation template]] 
Specify target accounts
Identify [[Region]]s 

# Updating StackSet
Cannot update template of individual [[Stack]]s, effects all [[Stack]]s

# Deleting StackSet
Can delete a single [[Stack]]

# Additional Options
- Max concurrent account
- Failure tolerance
- Retain [[Stack]]s
- [[Region]] concurrency

# Tags
- Key-Value Pairs
	- key : value
	- Used for billing and cost allocation

# Permission Models

| Self-managed                                                                           | Service-managed                                                                                  |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Define [[IAM Role]] required                                                           | No [[IAM Role]] definition required, [[11. CloudFormation/StackSets\|StackSets]] do that for you |
| Can deploy to any [[AWS]] account in which you have permissions to create [[IAM Role]] | Deploy to accounts managed by [[AWS]] Organizations                                              |
