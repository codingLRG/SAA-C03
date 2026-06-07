Gives control over placement of instances to meet specific needs
Can be a cluster, spread or partition table type that minimize correlated failures, lower network latency, and achieve high throughput
# Cluster
Achieves low-latency by packing instances closely within [[Availability Zone]]
Used for high compute and workloads with fast data exchanges
High risk of correlated hardware failure
# Partition
Distributes instances across logical partitions
Used for large distributed and replicated apps (ie data warehouse)
Each partition can contain multiple instances
# Spread
Strictly places small group across distinct underlying hardware
Maximizes availability by not sharing the same physical hardware, useful for crucial hardware
Can be used across [[Availability Zone]]