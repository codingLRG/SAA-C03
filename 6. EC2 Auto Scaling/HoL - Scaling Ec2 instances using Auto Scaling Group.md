Create Launch Template instead of Launch Instance
- EC2 > Launch templates > Create launch template
	- Enable Auto Scaling guidance
- Enable [[CloudWatch]] monitoring in advanced details
This Template is what the [[EC2 auto scaling]] will reference

1. Choose launch template
	- As name implies, needs template
2. Choose launch options
	- Choose [[VPC]] and [[Availability Zone]]s
3. Integrate with other services
	- Not gone over in this session
4. Configure group size and scaling
	- Desired capacity, min capacity and max capacity set, nothing else changed
5. Add notifications
	- Not gone over in this session
6. Add tags
	- Not gone over in this session
7. Review

Now to create Scale Out and In policies
- Create [[CloudWatch]] Alarm
	- Metric: EC2 > By Auto Scaling Group > Autoscaling Group CPUUtilization
	- Note: Need to wait for autoscaling group to be At desired capacity