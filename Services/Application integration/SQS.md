---
aliases:
  - Simple Queue Service
---
> Simple Queue Service

Queuing system for messages to be processed by:
- [[EC2]]
- [[Lambda]]
- [[ECS]]
Replace message-oriented middleware without managing servers or resources

| Types               | Delivery      | Ordering    | Throughput |
| ------------------- | ------------- | ----------- | ---------- |
| Standard            | At least once | Best effort | High       |
| First in, First out | Exactly once  | Exact order | Limited    |
For standard queue, you can change message visibility timeout to assist with redundant delivery (won't guarantee no redundant delivery)

Autoscaling dependent on:
- Age of oldest message (can have target tracking policy)
- Queue depth
- Number of messages

Can work with [[SNS]] when receive notification and [[ECS]] when trying to send data between tasks