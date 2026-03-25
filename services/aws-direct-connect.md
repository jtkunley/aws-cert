# AWS Direct Connect

## What it is
- **Private** circuit on-prem ↔ AWS; predictable bandwidth into **VPC** (VIFs).

## Personal notes / memory hooks
- DX is the **pipe**—still need DataSync/FSx/SGW/DMS for the workload.
- **Practice (Windows file Q):** DX exists; add **DataSync + FSx**, not “DX alone.”

## When to use it
- Steady large hybrid traffic; compliance; low jitter vs internet.

## When NOT to use it
- Sporadic small traffic—**Site-to-Site VPN** enough.

## Exam clues
- Direct Connect to VPC, private link, hybrid migration diagrams.

## Common distractors
- DX alone “migrates” data—false; needs a **data service**.

## Architecture patterns
- Private VIF → VPC; redundant DX; TGW (advanced).

## Comparison with nearby services
- **DX:** private circuit.
- **VPN:** IPsec over internet.
- **Peering:** cloud-to-cloud.

## Example scenarios
- Replicate file data to FSx over stable pipe vs flaky internet.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
