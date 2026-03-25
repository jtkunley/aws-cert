# AWS Direct Connect

## What it is
Dedicated or hosted **private network connectivity** from on-premises to AWS, bypassing the public internet for **stable bandwidth and lower latency** into **VPC** (and many AWS services via **public/private VIFs**).

## Personal notes / memory hooks
- DX = **pipe**; look for another service that **moves or serves** the bits.

## When to use it
Hybrid workloads, **large ongoing data movement**, predictable throughput, compliance-sensitive paths; pairs with **DataSync**, **Storage Gateway**, hybrid AD, etc.

## When NOT to use it
Small sporadic transfers where **Site-to-Site VPN** is enough; need instant zero-commit connectivity without provisioning lead time.

## Exam clues
- “Direct Connect to the VPC,” “private connection from on-premises,” “consistent network for migration,” hybrid diagrams.
- **Practice (Windows file server Q):** DX already in place from on-prem to **VPC**—pair with **DataSync** + **FSx**, not DX as sole solution.

## Common distractors
- Assuming **Direct Connect alone** migrates data—it **provides the path**; you still pick **DataSync/SGW/DMS** for the workload.

## Architecture patterns
- DX + **private VIF** to VPC; redundant connections; integration with **transit gateway** (advanced).

## Comparison with nearby services
- **Direct Connect** vs **VPN** (quick, encrypted internet) vs **VPC peering** (cloud-cloud, not on-prem).

## Example scenarios
- Windows file server replication to **FSx** over DX instead of flaky internet uplink.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
