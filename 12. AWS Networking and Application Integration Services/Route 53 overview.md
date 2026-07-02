[[Route 53]]
[[Hosted Zone]]
[[DNSSEC]]

| Public [[Hosted Zone]]              | Private [[Hosted Zone]]                 |
| ----------------------------------- | --------------------------------------- |
| How traffic is navigated on the web | How traffic is navigated on the [[VPC]] |
Creates [[Name Server]] and [[Start of Authority]]
[[Query Logging]]

Has [[Alias Record]] and [[Non-Alias Record]]

Most companies use [[BIND]] as internal DNS service
- [[BIND]] has a DNS forwarder that allows you to resolve private [[Hosted Zone]] in [[AWS]] from on-premises network
- Can be migrated to [[Route 53]] via [[BIND]] zone file

| Active               | Passive                 |
| -------------------- | ----------------------- |
| Accepts live traffic | On standby for failover |
