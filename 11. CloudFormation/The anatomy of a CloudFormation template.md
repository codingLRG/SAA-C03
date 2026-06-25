[[CloudFormation]]
- Resources
	- [[Logical ID]]
	- Type: What kind of resource is it
	- Properties: What properties of the resource does it have
- Version
	- Version of the template, automatically assumes latest version is wanted on creation
- Description
	- Comments about template
- Metadata
	- Details about resources in templates
- Parameters
	- Create custom values each time a [[Stack]] is created or updated
```YAML
  VarThatIsReferencing: !Ref ReferencedVar
```
- Rules
- Mappings
	```YAML
	Mapping:
		Map:
			LocalA:
				"var": "value1"
			LocalB:
				"var": "value2"
	
	# To reference: !FindInMap ["Map","LocalX","var"]
	```
- Conditions
- Outputs
	- Allows to export from one [[Stack]] to another [[Stack]]
```YML
# Returned value from AWS
Value: !Ref ReferencedVar
Export:
	# Name of resource for import?
	Name: !Sub "Name" 
```


| Parameters                                                       | Mappings                                                                       | Outputs                                                                                             |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| Mainly for associating values to a parameter                     | Mainly used if you want to use a single key to corresponding ==set of values== | Exports values with a unique name                                                                   |
| Enables input of ==custom values== and call using [[Logical ID]] | Matches ==key== to corresponding set                                           | Values can be exported to other [[Stack]]s using export field to perform cross-[[Stack]] references |
| Uses Ref intrinsic function to reference a param                 | Uses the Fn::FindInMap intrinsic function to retrieve values in a map          | Uses intrinsic function Fn::ImportValue to import values (shocker)                                  |
> DO NOT STORE SENSITIVE DATA HERE

