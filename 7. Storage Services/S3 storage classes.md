[[S3]]

| Type                            | Use Case                                  | [[Availability Zone]] | Availability | Minimum Storage Charge | Data Retrieval Fee |
| ------------------------------- | ----------------------------------------- | --------------------- | ------------ | ---------------------- | ------------------ |
| Standard                        | Frequent accessed                         | 3+                    | 99.99%       | 0 days                 | None               |
| Standard-IA (Infrequent Access) | Long-lived, less frequently accessed data | 3+                    | 99.99%       | 30 days                | Measured per GB    |
| Intelligent-Tiering             | Unknown access patterns                   | 3+                    | 99.9%        | 30 days                | None               |
| One Zone-IA                     | Long-lived, less frequently accessed data | 1                     | 99.95%       | 30 days                | Measured per GB    |
| [[S3 Glacier]]                  | Low-cost long term storage                | 3+                    | 99.99%       | 90 days                | Measured per GB    |
| Glacier Deep Archive            | Low-cost long term storage                | 3+                    | 99.99%       | 180                    | Measured per GB    |

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
- Retrieval options:

| Expedited                                                | Standard       | Bulk        |
| -------------------------------------------------------- | -------------- | ----------- |
| Subset data (no more than 250MB files) archive retrieval | Default option | Lowest-cost |
| 1-5 minutes                                              | 3-5 hours      | 5-12 hours  |
Expedited can be ensured by purchasing provisioned capacity
# Glacier Deep Archive
- Lowest cost
- 7 - 10 years or longer 
- Retrieval options:

| Standard | Bulk       |
| -------- | ---------- |
| Default  | Lower cost |
| 12 hours | 48 hours   |
