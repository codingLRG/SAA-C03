[[ELB]]

| Type                               | Routing Algorithm                                  | Protocol Listeners       | Use Cases                                      |
| ---------------------------------- | -------------------------------------------------- | ------------------------ | ---------------------------------------------- |
| [[ALB\|Application Load Balancer]] | Round Robin, [[Least Outstanding Requests]]        | HTTP/HTTPS, [[gRPC]]     | Web apps and containers                        |
| [[NLB\|Network Load Balancer]]     | Flow Hash                                          | TCP/UDP, TLS             | Ultra-low latency requests                     |
| [[GWLB\|Gateway Load Balancer]]    | IP Listener Routing leveraging [[GENEVE]] protocol | IP                       | Virtual apps from 3rd parties                  |
| [[CLB\|Classic Load Balancer]]     | Round Robin, [[Least Outstanding Requests]]        | HTTP/HTTPS, TCP, SSL/TLS | Legacy application, recommended to use [[ALB]] |

# [[ALB]]
Layer 7 of OSI
Notable Features:
- Routing via listener rule condition types
- Connection draining
- Idle connection timeout
- Cross-zone load balancing
- Preserving Source IP address
- Slow Start

Security Features:
- SSL Offloading
- Server Name Indication
- Back-end Server Encryption
- User Authentication
- Application-Layer Protocol Negotiation
- Integration with [[Security Group]]s and [[WAF]]

Listener Rule Condition Types:
- Host condition (subdomains)
- HTTP Header
- HTTP Request Method
- URL Path
- Query String
- Source IP

# [[NLB]]
Layer 4 of OSI
Can be directly associated with [[Elastic IP address]]
Notable features:
- Connection Draining
- Cross-zone Load Balancing
- Preserving Source IP address
- WebSockets support
- Long-lived TCP connection

Security features:
- SSL Offloading
- Server Name Indication
- Back-end Server Encryption
- Application-Layer Protocol Negotiation
- Integration with [[Global Accelerator]]

# [[GWLB]]
Layer 3 and 4 of OSI
Configured using route tables of your [[VPC]] instead of virtual IP

# [[CLB]]
Don't use it