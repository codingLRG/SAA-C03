[[S3]]

| Type                            | Use Case                                  | [[Availability Zone]] | Availability | Minimum Storage Charge | Data Retrieval Fee         |
| ------------------------------- | ----------------------------------------- | --------------------- | ------------ | ---------------------- | -------------------------- |
| Standard                        | Frequent accessed                         | 3+                    | 99.99%       | 0 days                 | None                       |
| Standard-IA (Infrequent Access) | Long-lived, less frequently accessed data | 3+                    | 99.99%       | 30 days                | Measured per GB            |
| Intelligent-Tiering             | Unknown access patterns                   |                       |              | 30 days                | None                       |
| One Zone-IA                     | Long-lived, less frequently accessed data | 1                     | 99.95%       | 30 days                | Measured per GB (probably) |
| [[S3 Glacier]]                  | Low-cost long term storage                | 3+                    | 99.99%       | 90 days                | High                       |
| Glacier Deep Archive            | Low-cost long term storage                |                       |              |                        |                            |

# Standard
- Most expensive
- Durable, high available, high performance
- Good for:
	- Static website
	- Temporary storage (24 hour storage)
# Standard-IA
- Rapidly retrieve stored infrequently accessed files 
- Good for:
	- Data backup
	- Data store for [[Disaster Recovery]]
# One Zone-IA
- Cheaper than Standard-IA
- Good for:
	- Cost effective option for ==SECONDARY== data backup
	- Storing easily recreatable data
# Intelligent-Tiering
- Automatically moves object between different access tiers
- Stores in:
	- 2 low-latency access tiers
	- 2 optional archive access tiers
- Good for:
	- Storage with no management overhead
	- Avoid lifecycle policies that are not consistently implemented
# Glacier
- Low cost
- Has its own management console
- Has a custom resource called a [[Vault]]
	- Only available in Glacier console
	- Must provide [[Vault]] name and corresponding [[Region]]
- Good for:
	- Data archiving
# MUST FINISH LATER

|     |     |
| --- | --- |
|     |     |
