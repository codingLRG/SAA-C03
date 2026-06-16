You can clone settings from existing bucket
ACLs can be enabled but not encouraged, since [[S3]] policies simplify this
Bucket versioning
Tagging
Encryption:
- Server sided encryption (SSE)
	- With [[S3]] managed keys
	- With [[KMS]] keys
- Dual layer encryption with [[KMS]]
	- Cost more
- Bucket Key
	- Reduces cost for SSE [[KMS]]
Object lock

[[Directory buckets]]

General bucket options:

| Objects                           | Properties                                     | Permissions                                   | Metrics                            | Management                               | Access Points                                                                     |
| --------------------------------- | ---------------------------------------------- | --------------------------------------------- | ---------------------------------- | ---------------------------------------- | --------------------------------------------------------------------------------- |
| Stored [[S3]] objects and folders | Configure bucket wide settings like versioning | Manage access and security like public access | Bucket usage for cost optimization | Lifecycle policies and replication rules | Unique access pathways with custom permissions tailored to different applications |
