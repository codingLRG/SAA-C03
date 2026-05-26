For IT audits
Tracks user activity and API usage across [[AWS]] account, stores data in [[S3]]
Enables risk auditing by monitoring
- [[Management Console]]
- [[SDK]]
- [[API]]
- [[CLI]]


| Name             | Plane   | Description                                                                                                         | Example                                                              |
| ---------------- | ------- | ------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Management Event | Control | Provide info about the management operations performed on your [[AWS]] resource                                     | Attaching an [[IAM Role]], Creating a new [[VPC]], Creating a subnet |
| Data Event       | Data    | Provide information about the resource operations performed ON ([[S3]] bucket) or IN ([[S3]] object) your resources | [[S3]] object-level API activities, Invoking an [[Lambda]] function  |
Cross-account monitoring