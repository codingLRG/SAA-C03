Systems Manager > Quick Setup > Create configuration

# Patch policy name
Name the policy for identification

# Scanning and installation
- Patch operation
	- Scan
		- Detect missing patches
	- Scan and install
		- Detect and automatically install missing patches
	- Scanning schedule
		- Default
		- Custom schedule

# Patch baseline
Rules for auto-approving patches
- [[AWS]] recommended
- Custom patch baseline

# Patching log storage
- Output to [[S3]]

# Targets
- Entire org
- Custom [[Organization]] Units
- Current account

# Rate control
- Concurrency: How many to patch at the same time
- Error threshold

# Instance profile options
Add required [[IAM]] to existing instances

# Local deployment roles
Used for controlling least control privileges
- Create and use new [[IAM Role]]
- Use existing [[IAM Role]]

# Enable Explorer role
Used for aggregating patch data to centralized dash
- Create and use new [[IAM Role]]
- Use existing [[IAM Role]]