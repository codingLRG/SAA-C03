---
aliases:
  - Amazon Machine Image
---
Launch preconfigured [[EC2]] instance

| Block Store Type       | Volume Snapshots             | Block Device Mapping    |
| ---------------------- | ---------------------------- | ----------------------- |
| [[EBS]]                | [[EBS]] Snapshots            | [[EBS]] Volumes mapping |
| [[ec2 instance store]] | Template for the root volume | N/A                     |


| Launch Permissions | Meaning                                       |
| ------------------ | --------------------------------------------- |
| Public             | Grant launch permissions to all accounts      |
| Explicit           | Grant launch permissions to specific accounts |
| Implicit           | Default permission of the owner to launch     |

[[Region]]al in scope
Copiable to other [[Region]] via [[CLI]], [[SDK]], or [[API]]
Copiable to other [[AWS]] account
Sharable/Sellable on [[AWS]] Marketplace

Virtualization Type:
- [[PV]]
- [[HVM]] (Possible to run [[PV]] drivers on top of [[HVM]])
- Irrelivant if launching or changing [[5. EC2/AMI|AMI]] to different [[EC2 Instance Type]]

Heavily used in [[EC2 auto scaling]]
- [[SQS]] to increase or decrease instances in group
- Perfect for [[stateless]] application