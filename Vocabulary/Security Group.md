Works at the instance level
Only specify allow rules in group
Can be not needed if traffic is stopped by [[Network ACL]]
[[Statefull]]

Tracks all status of incoming request
If traffic is a response to a request, then it will be allowed automatically regardless of outbound rules
It is aware if outgoing traffic is:
- Initiated from [[EC2]]
- Response to request that was initialized externally

Outbound Rule can filter:
- [[API]] call initiated by application hosted in [[EC2]]
- Scheduled OS Patch that is initiated by [[EC2]]

Does not use [[Ephemeral ports]]