[[Aurora]]
Less than 1 second of read replication latency
Group individual DB instances to a particular endpoint:
- Cluster endpoint
- Reader endpoint
- Custom endpoint
- Instance endpoint

Supports [[Serverless]]:
- recommended for sporadic workloads and infrequent access patterns

Supports Global DBs:
- Spans multiple [[Region]]s
	- Spans at least across 2 [[Region]]s
- Needs only one RW DB in one [[Availability Zone]], the rest can be Read only
- Can have up to 5 secondary [[Region]]s

[[Recovery Point Objective]] = 1 second
[[Recovery Time Objective]] = 1 minute