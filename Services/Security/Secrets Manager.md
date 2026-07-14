Protects secrets of apps, services and IT resources
Enables to easily rotate, manage and retrieve sensitive credentials
Built-in integrations for:
- [[RDS]]
- [[Redshift]]
- [[DocumentDB]]
- [[Lambda]]
Central access to secrets, good for auditing
Storing plaintext is not possible and needs [[KMS]]
Secret name ID
Dynamic credential
```YAML
MasterUsername: '{{resolve:secretmanager:mySecret:SecretString:username}}'
```
Not recommended for encryption keys or key materials since it ==does not use [[HSM]]==