The data or set of commands that will be run by the [[EC2]] instance once it's launch
Automates launch process
Good for [[EFS]] mapping or [[EC2 auto scaling]] grouping
Good if audited
Base64-encoded format
16KB only when raw
Access Instance Metadata: [[Instance Data Service]]
Only run once so modifying the User Data and restarting the instance won't affect the initial UserData