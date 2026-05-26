---
aliases:
  - Elastic Load Balancing
---
> Elastic Load Balancing

Auto distributes incoming traffic across multiple targets
- [[EC2 instance]]
- [[ECS task]]
- [[Fargate task]]
- [[Lambda Function]]
Routes to healthy server in case of unhealthy server

| Name     | Protocol Listeners    | Use Cases                                                                   |
| -------- | --------------------- | --------------------------------------------------------------------------- |
| [[ALB]]  | HTTP(S), gRPC         | Web apps, microservices and containers                                      |
| [[NLB]]  | TCP, UDP, TLS         | Millions of request with low latency                                        |
| [[GWLB]] | IP                    | Running 3rd party virtual appliances                                        |
| [[CLB]]  | HTTP(S), TCP, SSL/TLS | Legacy apps in [[AWS]], custom security policies and TCP passthrough config |
