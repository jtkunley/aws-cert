# Amazon VPC

## What it is
Your **isolated network** in AWS: subnets, route tables, internet and NAT gateways, **security groups**, NACLs, and attachment points for hybrid connectivity (**Direct Connect**, **VPN**, **Transit Gateway**).

## When to use it
Every regional deployment; private subnets for workloads; **ENIs** for managed services (FSx, RDS, etc.) that live in the VPC.

## When NOT to use it
N/A in AWS—VPC is foundational; avoid over-building (exam may prefer **VPC endpoints** vs full hybrid).

## Exam clues
- “Private subnets,” “VPC endpoints,” “peering,” “Direct Connect to the VPC,” “FSx in the VPC.”
- **Practice (Windows file server Q):** **servers in AWS** live in **VPC**; file share must be reachable there (**FSx**), not only on-prem gateway SMB.

## Common distractors
- Confusing **VPC** (network container) with **FSx/S3** (storage)—the stem may mention VPC only as the **destination network** for hybrid links.

## Architecture patterns
Multi-AZ subnets; hybrid: DX/VPN → VPC; interface endpoints for S3/DynamoDB.

## Comparison with nearby services
**VPC** vs **global** edge (CloudFront) vs **account boundary**—VPC is regional isolation.

## Example scenarios
Direct Connect terminates into VPC; Windows instances mount **FSx** DNS name in same VPC/DNS setup.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
**“In the VPC”** = private network home for ENI-based services like FSx.
