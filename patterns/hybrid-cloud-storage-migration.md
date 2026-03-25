# Hybrid cloud storage migration

## What it is
Keeping **on-premises** systems while moving or mirroring data into AWS over **private or VPN** links (**Direct Connect**, Site-to-Site VPN), often during **phased** application migration.

## When to use it
Partial workload already in cloud, **ongoing sync**, regulated networks, large datasets that need **predictable** pipe to VPC.

## When NOT to use it
Greenfield all-in-cloud with no on-prem source; **offline** seed only—consider **Snow** for first load.

## Exam clues
“On-premises,” “Direct Connect to VPC,” “half migrated,” “hybrid,” “Windows server still on-prem.”

## Common distractors
Picking **only** connectivity (DX) without a **transfer or file** service; confusing **hybrid access** (gateway on-prem) with **cloud-native file** (FSx in VPC).

## Related AWS services
Direct Connect, VPN, DataSync, Storage Gateway, FSx, S3, Snow Family.

## Comparison with nearby patterns
**Hybrid migration** vs **lift-and-shift all to EC2**; vs **cloud-only** greenfield.

## Example scenarios
- 1 TB Windows share on-prem; Windows instances in VPC need the same data—**FSx + DataSync** over DX.
- **Practice (Windows file server Q):** **~half** Windows workload migrated; **1 TB** + **5 GB/day**; **Direct Connect** already provisioned—still add **DataSync** + **FSx** for cloud-side file system.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
**DX in the stem** → you still need **what moves the data** and **where it lands**.
