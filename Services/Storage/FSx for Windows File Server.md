Uses [[SMB]] protocol
Integrated to existing AD (Microsoft or AWS)
Shared file storage for [[SharePoint]], SQL Server or other Microsoft [[Container]]s
Works with:
- Windows
- Mac
- Linux
- [[EC2]]
- VMWare
- [[ECS]]
- [[EKS]]
- [[Lambda]]
Can only increase storage, not decrease

| AZ Type     | HDD Option | SSD Option | Microsoft [[Distributed File System Replication]] | High-Availability                                                                                  |
| ----------- | ---------- | ---------- | ------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Single-AZ 1 | No         | Yes        | Yes                                               | Yes, provision 2 Single-AZ 1 in separate AZ and sync using [[Distributed File System Replication]] |
| Single-AZ 2 | Yes        | Yes        | No                                                | No                                                                                                 |
| Multi-AZ    | Yes        | Yes        | No                                                | Yes                                                                                                |
Takes native backups
Create backups with [[Backup]]
Take shadow copies to undo file changes