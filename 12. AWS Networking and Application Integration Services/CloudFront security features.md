Content can be static or dynamic ([[API]]s)
- Dynamic is stored in JSON or XML for a few minutes/hours only

Origins:
- [[S3]]
- [[ELB]]
- [[EC2]]

# Protocol Policy
Origin and viewer
Configure to use HTTP, HTTPS or both
- Origin: HTTP Only, HTTPS Only, Match Viewer
- Viewer: HTTPS Only, Redirect HTTP to HTTPS, HTTP and HTTPS

# [[Origin Access Identity]]
Works like [[IAM]]

# Field-Level Encryption
Encrypt specific data fields
- Credit cards
- [[Personal Health Information]]
- [[Personal Identifiable Information]]

Public and private key encryption

# Signed URLs and Signed Cookies
Distributing private content over the internet
Signed URL made by [[SDK]]
Signed Cookies automatically deleted upon browser closing or clearing cache

# Geo-Restriction
Self explanitory

# Alternate Domain Name and SSL Certificate
[[CNAME]]
[[Custom SSL]] can be made via [[ACM|Certificate Manager]]
# Integration with other [[AWS]] Services
[[WAF]]
[[Shield]]
- Advanced required
- Different from Origin Shield
