---
aliases:
  - GSI
---
Search can span all items in a [[DynamoDB]] base table, across all partitions
Table can have up to 20 [[Global Secondary Index|GSI]]
Primary keys are always projected
Secondary Index [[RCU]] and [[WCU]] are separate from the base table
- Always a good idea to increase [[WCU]] to be above Base table to prevent throttling
All updates done to base table are applied to all [[Global Secondary Index|GSI]]s 