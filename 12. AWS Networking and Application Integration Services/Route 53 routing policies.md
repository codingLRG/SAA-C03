[[Route 53]]
# Simple
Routes to a single resource
No health check
One-to-one relationship

# Failover
Used to set up active-passive failover ([[Route 53 overview]])
Consists of:
- Primary records
- Secondary records

Useful for setting up static [[S3]] as failover site

# Geolocation
Leverages geolocation to serves traffic
Single geolocation record is only mapped to one continent or to a specific country
Maps via [[EDNS0]]
Enables localize content and content restriction
- Good for legal distribution rights of digital content

Not fully capable of providing low-latency, use [[CloudFront]] instead
Cannot dynamically shift traffic from one [[Region]] to another, use Geoproximity routing instead

# Geoproximity
Keep track of all relationships among the records
Similar to Geolocation:
- Geolocation leveraged
- Uses [[Traffic Flow]]
- Uses a bias in shifting traffic
	- Provides option to shift more or less traffic based on numeric value of bias and specific geo coordinates
		- coordinates are lat and long of endpoint location
		- bias depends on number of [[AWS]] resources that you currently have

Not fully capable of reducing Internet latency, use latency-based routing instead
- If app is expecting millions of users, use [[CloudFront]] or [[Global Accelerator]]
 
# Latency-Based
Suitable if resources are in multiple [[Region]]s
Based on traffic between users and [[AWS]] Data centers
Cannot shift traffic using bias

# Multivalue Answer
Configure single record to multiple values
One-to-many
Good for active-active failover ([[Route 53 overview]])
Health check to ensure [[Route 53]] will route live traffic to live resource
Like load balancer, not as powerful

# Weighted
Weight is measured between 0 and 255
- 0 = stop responding

Good for migration activities