Analyzes [[Resource-based Policy]] for users outside of organization
Allows to analyze access for resources that belong to your organization, even if another [[AWS]] account owns the resource
Can send an event to [[EventBridge]], must create event rule to receive notification, connect to [[SNS]] to receive messages from [[EventBridge]]
- Each gen finding
- change to the status
- finding is deleted