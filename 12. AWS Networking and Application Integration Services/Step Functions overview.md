[[Step Functions]]
Defined using [[Amazon States Language]]
- Similar to [[JSON]]


| Type     | Use                                  |
| -------- | ------------------------------------ |
| Task     | Single unit of work                  |
| Choice   | Add if-them-else logic               |
| Parallel | Begin parallel branches of execution |
| Wait     | Delays for a specified time          |
| Fail     | Stop execution and marks as failure  |
| Succeed  | Stop execution and marks as success  |
| Pass     | Passes input to its output           |
| Map      | Adds a for-each loop                 |
Built in error condition handling capabilities