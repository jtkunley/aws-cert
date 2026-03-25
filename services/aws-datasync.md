# AWS DataSync

## What it is
- Managed **copy/sync** from on-prem NFS/SMB/HDFS to **S3, EFS, FSx**; schedule, throttle, verify.

## Personal notes / memory hooks
- On-prem share + AWS destination + **schedule** → DataSync default.
- **Practice (Windows file Q):** **daily** job on-prem Windows server → **FSx**; incremental after **1 TB** bulk over **DX**.

## When to use it
- One-time or recurring migration; incremental deltas; DX/VPN path.

## When NOT to use it
- Offline PB seed—**Snow**.
- DB ongoing replication—**DMS**.
- SFTP partner ingest—**Transfer Family**.

## Exam clues
- Daily task, replicate, agent, on-premises to FSx/S3/EFS.

## Common distractors
- Confused with **Transfer Family** (protocol endpoints, not bulk sync engine).

## Architecture patterns
- Agent on-prem → DX → FSx/S3/EFS; bulk then incremental.

## Comparison with nearby services
- **DataSync:** migration/sync jobs.
- **Storage Gateway:** hybrid cache/presentation.
- **Transfer Family:** SFTP/FTP to S3.

## Example scenarios
- Nightly 5 GB/day Windows share → FSx.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
