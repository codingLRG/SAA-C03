Contains permissions that explicitly allow or deny access
Policies in [[JSON]], can be created in [[Management Console]] UI

| Standalone Policy                 | Inline Policy                                    |
| --------------------------------- | ------------------------------------------------ |
| Unchanged even if [[IAM]] deleted | Will automatically be deleted if [[IAM]] deleted |
| One-to-many relationship          | One-to-one                                       |
- [[Identity-based Policy]]
- [[Resource-based Policy]]
- [[Permissions Boundaries]]
- Organizations [[SCP]]
- [[S3 ACL]]s
- [[Session]]