---
aliases:
  - Simple Storage Service Glacier
---
> Simple Storage Service Glacier

Has its own web management console
Long-term storage

| Type                 | Cost   | Minimum Storage Duration (Days) |
| -------------------- | ------ | ------------------------------- |
| Glacier              | Low    | 90                              |
| Glacier Deep Archive | Lowest | 180                             |
Data deleted prior to minimum duration will still be charged the entire minimum duration

Retrieval Options

| Type         | Expedited     | Standard        | Bulk            |
| ------------ | ------------- | --------------- | --------------- |
| Glacier      | 1 - 5 minutes | 3 - 5 hours     | 5 - 12 hours    |
| Deep Archive | Not available | Within 12 hours | Within 48 hours |
