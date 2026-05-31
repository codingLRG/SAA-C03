Steps to validate a request:
1. Authentication: may not be required if allowed anonymous request
2. Process request context
3. Evaluate all policies within single account
All requests are implicitly denied... except for root
Explicit Deny > Explicit Allow
[[Permissions Boundaries]], and [[SCP]]s