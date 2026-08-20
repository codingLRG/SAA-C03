# High availability
## [[EC2 auto scaling]]
> [[Auto Scaling Groups]] are able to be assigned to multiple [[Availability Zone]]s to provide redundancy, allowing for high availability without modifying the application code
- Creating separate [[Auto Scaling Groups]] in different [[Availability Zone]]s does not provide high availability without modifying the application code, as now the traffic will have to be shifted
- Using [[Lambda]] to automatically switch does not provide real-time high availability and would also require changes to the code to work

# Networking
## [[Route 53]]
> Utilizing [[Route 53 routing policies#Geolocation|Geolocation]] can eliminate connecting to the wrong continental environment to resolve language barrier
## [[Amazon EC2 networking]]
> [[Elastic IP address]]es remain associated with the instance, even after shutdown

> [[NAT Gateway]]s allow connecting your public subnet your private subnet with high availability, keeping your private subnet private, while enabling internet connectivity
- [[Internet Gateway]] will make the private subnet public, this should be connected to your public subnet
- [[NAT Instance]] will not allow for high availability unless you utilize multiple, however this can add up
- [[VPC Endpoint]] allows private connectivity from an [[AWS]] service, not the internet 