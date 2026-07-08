[[ELB]]
[[Route 53 routing policies]] are good for small demand
- Multivalue Answer may result in underutilization/overutilization

Works with Multi-[[Availability Zone]] to avoid outages
[[Region]]al only
- [[Route 53]] can get past this restriction as it can route to specific regions with [[ELB]]s
- If you want a [[ELB]] to route to multiple [[Region]]s, [[Global Accelerator]] is the answer instead

# [[ELB Types]]

| Type                               | Routing Algorithm                                  | Protocol Listeners       | Use Cases                                      |
| ---------------------------------- | -------------------------------------------------- | ------------------------ | ---------------------------------------------- |
| [[ALB\|Application Load Balancer]] | Round Robin, [[Least Outstanding Requests]]        | HTTP/HTTPS, [[gRPC]]     | Web apps and containers                        |
| [[NLB\|Network Load Balancer]]     | Flow Hash                                          | TCP/UDP, TLS             | Ultra-low latency requests                     |
| [[GWLB\|Gateway Load Balancer]]    | IP Listener Routing leveraging [[GENEVE]] protocol | IP                       | Virtual apps from 3rd parties                  |
| [[CLB\|Classic Load Balancer]]     | Round Robin, [[Least Outstanding Requests]]        | HTTP/HTTPS, TCP, SSL/TLS | Legacy application, recommended to use [[ALB]] |
# Listener and Target
Incoming requests are processed through a listener that accepts certain port requests
Target group is group of resources the listener can route the viewer to
Target group has [[Health Check]]

# Autoscaling
Can be integrated with [[EC2 auto scaling]]
[[ELB]] RequestCountPerTarget metric to scale in [[EC2 auto scaling]] group