Different from [[IAM]]
- [[IAM]] is used for accessing resources within a single [[AWS]] account
- [[AWS]] user identity

[[Organization]]s
- Manage multiple [[AWS]] accounts from a management account
- [[AWS]] account typically contains multiple [[IAM]] users

Basically root account
- Used for managing your org only, not to provision resources
- Used to send invitations to [[Organizational Units]]
- Two options for [[Organization]]s
	- Support All Features
		- Recommended
	- Consolidated Billing Only

[[Organizational Units]]
[[SCP|Service Control Policies]]
- Don't affect [[Resource-based Policy]]