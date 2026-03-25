# Storage Gateway hybrid access

## What it is
**On-premises** or edge **gateway** presenting **SMB/NFS or iSCSI** while backing to **S3** (File/Volume/Tape modes)—**low-latency local** with cloud durability.

## When to use it
Branch offices, cached reads, extending legacy apps to cloud storage **without rewriting** to S3 API.

## When NOT to use it
When the exam wants **managed file system ENIs in VPC** for **instances in AWS**—compare carefully to **FSx**; gateway is often **on-prem centric**.

## Exam clues
“Storage Gateway,” “File Gateway,” “on-premises SMB,” “cache,” “tape backup.”

## Common distractors
Picking **File Gateway** when the answer should be **FSx in AWS** for migrated Windows compute **in the VPC**.

## Related AWS services
Storage Gateway, S3, Direct Connect, DataSync.

## Comparison with nearby patterns
**Gateway hybrid** vs **DataSync migration** vs **FSx native cloud file**.

## Example scenarios
Office workers use SMB share that lands in S3; different from “AWS servers need FSx share.”

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Ask **where** the primary consumer lives: **on-prem users** vs **instances in VPC**.
- **Practice (Windows file server Q):** distractor **replaces on-prem file server with File Gateway**—consumer story stays **on-prem–centric** vs **AWS servers** needing **FSx**.
