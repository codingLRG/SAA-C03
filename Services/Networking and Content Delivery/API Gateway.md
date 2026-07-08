Allow to publish, maintain, monitor and secure [[RESTful]] APIs
Supports [[WebSockets]] for real-time message communication
Front door for back-end services:
- [[EC2]]
- [[ECS]]
- [[Fargate]]
- [[Lambda]]
- [[Elastic Beanstalk]]
Web proxy service
Utilize mapping templates to modernize legacy apps
> Convert an incoming JSON to now utilized XML before leaving the gateway

API types:
- REST API
	- full access to [[API Gateway]] features
- HTTP API
	- cheap and designed for low latency
- WebSocket API
	- real-time applications (chat rooms)

Endpoint Types:
- Edge-optimized
	- Routed to nearest [[CloudFront]] [[Point of Presence]]
- [[Region]]al
	- routed in same [[Region]]
- Private
	- only accessed from [[VPC]]