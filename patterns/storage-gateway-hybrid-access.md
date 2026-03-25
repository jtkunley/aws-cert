# Storage Gateway hybrid access

## What it is
- On-prem **gateway**: SMB/NFS or iSCSI front; **S3** (or tape) back; local cache.

## When to use it
- Branch low-latency reads; legacy iSCSI; tape-to-S3.

## When NOT to use it
- Primary ask: **ENI file service in VPC** for cloud instances—compare **FSx**.

## Exam clues
- Storage Gateway, File Gateway, on-prem SMB, cache, tape VTL.

## Common distractors
- File Gateway “replace file server” when **AWS servers** need **FSx**.

## Related AWS services
- Storage Gateway, S3, Direct Connect, DataSync.

## Comparison with nearby patterns
- **Gateway:** edge hybrid.
- **DataSync:** bulk sync.
- **FSx:** cloud-native file.

## Example scenarios
- Office SMB → S3 objects behind cache.
- **Practice (Windows file Q):** distractor shifts share to **on-prem Gateway**; stem wants **cloud** Windows FS.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Who consumes: **on-prem users** vs **instances in VPC**.
