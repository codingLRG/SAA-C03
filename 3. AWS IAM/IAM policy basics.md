Version is in reference to the policy access language
Statement Element:
> Sid: ID of statement (optional)
> Effect: Allow or Deny
> Principal: refers to particular [[IAM identities]] (Required if [[Identity-based Policy]], can't be used if policy is intended to be attach to [[IAM User]], or [[IAM Role]])
> Action: Permitted code to run (Wildcard allowed)
> Resource: What resource is being effected (Optional for [[Resource-based Policy]], wildcard allowed)
> Condition: Preliminary rules (Optional)