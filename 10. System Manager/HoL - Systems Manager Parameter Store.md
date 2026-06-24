[[Systems Manager Parameter Store]]
# Parameter details
- Name
	- Hierarchy in naming convention
- Description
- Tier
- Type
- Data type
- Value

```Bash
aws ssm get-parameter --name "/dir/to/key/keyName"
# Returns encrypted if type to secure string
# To decrypt, add flag --with-decryption
ENV=dir
aws ssm get-parameter --name "/{ENV}/to/key/keyName"
```

Utilize [[CloudTrail]] to track and log
To deny a user access, create an Inline Policy in [[IAM Policy]]
Example:
```JSON
{
	"Version": '2012-10-17',
	"Statements": [
		{
			"Effect": "Deny",
			"Action": [
				"ssm:GetParameter"
			],
			"Resource": "arn:aws:ssm:*:*:parameter/dir/to/key/keyName*"
		}
	]
}
```
