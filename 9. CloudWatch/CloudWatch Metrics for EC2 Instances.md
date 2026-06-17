Basic Monitoring
- Free
- 5 minutes collection interval

Detailed
- Not free
- 1 minute interval

Custom metrics (all not free)
- Basic Resolution
	- 1 minute
- High Resolution
	- Up to 1 second
- Must have appropriate [[IAM Role]] to allow instance to send metric data to [[CloudWatch]]

CPU related metrics:
- CPU Utilization
- CPU Credit Usage and Balance (for burst-able instances)

Network related metrics:
- NetworkIn (bytes received)
- NetworkOut (bytes sent)

Disk related metrics (instances backed by instance store):
- DiskReadOps
- DiskWriteOps
- DiskReadBytes
- DiskWriteBytes

Status Check metrics:
- Instance Status
	- Checks health of VM
- System Status
	- Checks health of underlying hardware
- Status Check Failed
	- Verifies both instance and system status is healthy

RAM is not a metric
- Must install [[CloudWatch]] Agent on [[EC2]] and push to [[CloudWatch]] to view