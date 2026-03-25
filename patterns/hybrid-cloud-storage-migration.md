# Hybrid cloud storage migration

## What it is
- On-prem + AWS over **DX/VPN**; phased copy while apps split across locations.

## When to use it
- Partial migration done; large ongoing sync; private pipe to **VPC**.

## When NOT to use it
- All-cloud greenfield; **Snow**-only offline seed with no hybrid steady state.

## Exam clues
- On-premises, Direct Connect to VPC, half migrated, hybrid file/DB moves.

## Common distractors
- **DX only**—no DataSync/SGW/FSx picked.
- Gateway-on-prem confused with **cloud FSx** for **instances in VPC**.

## Related AWS services
- Direct Connect, VPN, DataSync, Storage Gateway, FSx, S3, Snow.

## Comparison with nearby patterns
- **Hybrid migration** vs **all-in EC2 lift** vs **cloud-native only**.

## Example scenarios
- 1 TB on-prem share; instances in VPC need same files—**FSx + DataSync + DX**.
- **Practice (Windows file Q):** **half** Windows in cloud; **1 TB + 5 GB/day**; DX present.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- DX in stem → still pick **mover** + **landing** service.
