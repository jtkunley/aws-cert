# DataSync migration and replication

## What it is
- **DataSync** scheduled/one-time transfers with verify/throttle; on-prem NFS/SMB → S3/EFS/FSx.

## When to use it
- Daily deltas; cutover prep; incremental after bulk load.

## When NOT to use it
- SFTP partner ingest—**Transfer Family**.
- DB replication—**DMS**.
- Offline truck—**Snowball**.

## Exam clues
- DataSync agent, daily task, replicate, bandwidth limits.

## Common distractors
- Right engine, **wrong target** (EFS vs FSx for Windows).

## Related AWS services
- DataSync, Direct Connect, FSx, EFS, S3.

## Comparison with nearby patterns
- **DataSync:** copy jobs.
- **Gateway:** ongoing hybrid mount.
- **Transfer:** SFTP/FTP door.

## Example scenarios
- Nightly 5 GB/day file server → FSx.
- **Practice (Windows file Q):** **daily DataSync** on-prem → **FSx** = keyed path.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Schedule + replicate + agent → DataSync.
