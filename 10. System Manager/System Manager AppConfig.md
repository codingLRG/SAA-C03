System Manager > Application Tools > AppConfig
Useful for
- Updating feature toggles
- Operational settings
- Dynamic config values

# Select Config Type
- Feature flag
	- Enable feature rollouts without modifying code
- Freeform config
	- Define JSON, YAML or text-base config data
- Config profile name

# Specify Config Data
- Config definition
	- AppConfig hosted config
		- Manual input config
	- [[S3]]
		- Requires [[S3]] object source 
		- Requires [[IAM Role]] for access
	- [[CodePipeline]]
		- No additional Params
	- [[Systems Manager Parameter Store]]
		- Retrieves and validates data
- Validator
	- Verify if data is syntactically and semantically valid to reduce risk of malformed configs