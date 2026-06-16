[[Relational Database]] vs [[NoSQL]]

[[DynamoDB]] is [[NoSQL]]
Dynamo first [[AWS]] SQL server engine
[[DynamoDB]]Local is a local version of the service that can be ran on non [[AWS]]

| Relational DB Item  | [[DynamoDB]] Item           |
| ------------------- | --------------------------- |
| Table               | Table                       |
| Row                 | Item                        |
| Column              | Attribute                   |
| Primary Key         | Primary Key / Partition Key |
| Index               | Secondary Index             |
| View                | Global Secondary Index      |
| Nested Table/Object | Map                         |
| Array               | List                        |
Secondary Index serves as a subsection of the table, allowing for faster queries

| [[Local Secondary Index]]                                    | [[Global Secondary Index]]          |
| ------------------------------------------------------------ | ----------------------------------- |
| Queries over single partition                                | Queries data across all partion     |
| Supports both eventual and strong consistency                | Only supports eventual consistency  |
| Can only be added at the same time you create the base table | Can be added or deleted at any time |
[[DynamoDB]] Global Tables tasks to create and replicate tables across multiple [[Region]]s are done automatically

[[DynamoDB Streams]]
[[DynamoDB TTL]]
[[DynamoDB Transactions]]
[[DAX]]

Scaling [[RCU]] and [[WCU]]

| Provisioned Capacity                                                         | On-Demand Capacity                                     |
| ---------------------------------------------------------------------------- | ------------------------------------------------------ |
| For predictable traffic                                                      | For unpredictable traffic or variable expected traffic |
| Enables manual provisioning [[RCU]] and [[WCU]]                              | No manual provisioning                                 |
| Can set target utilization                                                   |                                                        |
| More expensive than On-Demand if traffic doesn't utilize provisioned outlook | More expensive than Provisioned if traffic is steady   |

Utilize [[VPC]] [[Gateway Endpoint]] and route table entry to traverse from [[EC2]] to [[DynamoDB]] without going through open internet

[[IAM]] supported to allow or block actions


| Point-in-time Recovery                            | On-Demand Backup and Restore                           |
| ------------------------------------------------- | ------------------------------------------------------ |
| Automated backup                                  | Manual backup                                          |
| Continuous backups                                | No continuous backups                                  |
| Restore table at a point in time that you specify | Can only restore to a particular backup you have taken |
| More expensive                                    | Cost effective                                         |
