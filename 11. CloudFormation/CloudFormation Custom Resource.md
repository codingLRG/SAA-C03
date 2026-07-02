Bits of logic that you declare to run during the [[Provisioning phase]] of your [[CloudFormation]] template

Good for:
- Resource provisioning for non [[CloudFormation]] resource types
- Resource provisioning for non [[AWS]] resource types
- Provisioning steps not related to infrastructure

# How it works
3 parties
- Template Developer
- Custom Resource Provider
- [[CloudFormation]]

Template developer creates the [[CloudFormation]] template and provides Custom Resource Provider token along with input output params, while [[CloudFormation]] sends the requests with provided token

Requires only the service token for custom resource creation, ie [[Lambda]] or [[SNS]]
- [[Lambda]]
	- function invoked whenever resource is created, updated or deleted
	- called via [[API]]

# CloudFormation Registry
Lists private and public extensions that you can use
Advantages over custom resources:
- modeling, provisioning and managing 3rd party app resources
- [[CRUDL]] ops
	- No need to associate [[Lambda]] function or [[SNS]] topic 
- Drift detection