---
aliases:
  - Instance Family
---
> Also known as [[EC2 Instance Type|Instance Family]]

CPU Options:
- Intel
- AMD
- AWS Graviton (best price performance for cloud
 
Newer [[EC2]] are more cost-efficient


| Categories            | Family/Type          |
| --------------------- | -------------------- |
| General Purpose       | Mac, T\*, M\*, A\*   |
| Compute Optimized     | C\*                  |
| Memory Optimized      | R\*, X\*, Z\*, U\*   |
| Storage Optimized     | I\*, D\*, H\*        |
| Accelerated Computing | P\*, Inf\*, G\*, F\* |
# Naming Convention
> Type & Gen . Size

Example: m6.metal (metal means non-virtualized)

\*\*a. = AMD CPU
\*\*g. = [[AWS]] Graviton
If non of the above = Intel
\*\*\*d = local NVMe-based SSD
- If not, then it can only support [[EBS]]

\*\*\*n = enhanced networking capabilities
T\* = burstable CPU performance
- Governed by CPU Credits earned while idle
	- One credit = One core for one minute
- Sort of 'vertical scaling' as it temporarily provides higher CPU performance

.metal = direct access to CPU and memory
- Enables ability to run custom hypervisor
- Can still be integrated with [[EBS]], [[ELB]]
- Highest attributes across all other types