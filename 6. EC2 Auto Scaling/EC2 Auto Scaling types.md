# Simple Scaling
- Increases or decreases current capacity of [[EC2 auto scaling]] group based on single scaling adjustment
- Can utilize [[CloudWatch]] alarm for threshold of hardware utilization to scale in or out
	- [[Cool Down]] can be invoked to pause scaling event if previous event is not completed
# Step Scaling
- Increases or decreases current capacity based on a set of scaling adjustments
- Like Simple Scaling
	- Utilizes [[CloudWatch]] for high and low threshold alarms
	- Exact size or fix capacity unit
- Unlike Simple Scaling
	- Continue to respond to additional alarms even current scaling activity is in progress
	- Simultaneous evaluation of alarms 
# Target Tracking
- Automatically increases or decreases based on target value for specific metric
- Works like a thermostat
- Works for determined optimal performance
	- CPU utilization
	- Network in or out
	- Request count per target
# Scheduled Scaling
- Scaling based on set schedule
- Good way to bypass [[Instance warmup]] and [[Cool Down]] during expected spikes and downtime