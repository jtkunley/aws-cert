# Amazon VPC

## What it is
- Regional isolated network: subnets, routes, IGW/NAT, **security groups**, NACLs, hybrid attach (DX, VPN, TGW).

## Personal notes / memory hooks
- “In the VPC” = ENI services (FSx, RDS, etc.) live here.
- **Practice (Windows file Q):** **servers in AWS** need share **in VPC**—not only on-prem Gateway SMB.

## When to use it
- Every regional workload; private subnets; endpoints.

## When NOT to use it
- Overbuild: stem may need endpoints only, not full redesign.

## Exam clues
- Subnets, endpoints, peering, DX to VPC, FSx in VPC.

## Common distractors
- VPC confused with **storage**—VPC is network shell.

## Architecture patterns
- Multi-AZ subnets; DX/VPN → VPC; interface endpoints.

## Comparison with nearby services
- **VPC:** regional network.
- **CloudFront:** edge cache (different layer).

## Example scenarios
- DX terminates in VPC; instances mount FSx DNS in same VPC.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
