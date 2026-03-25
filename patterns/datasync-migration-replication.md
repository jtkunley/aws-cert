# DataSync migration and replication

## What it is
Using **AWS DataSync** for **scheduled or one-time** transfers with verification, throttling, and incremental sync from on-premises **NFS/SMB** (and other sources) to **S3, EFS, FSx**.

## When to use it
**Daily churn**, migration cutover prep, **incremental** updates after initial bulk, exam wording like “schedule a daily task to replicate.”

## When NOT to use it
Pure **SFTP partner ingest**—**Transfer Family**; database ongoing replication—**DMS**; offline truck—**Snowball**.

## Exam clues
“DataSync,” “agent,” “scheduled replication,” “on-premises to FSx/S3/EFS,” bandwidth limits.

## Common distractors
Pairing DataSync correctly but choosing the **wrong destination** (EFS vs FSx for Windows).

## Related AWS services
DataSync, Direct Connect, FSx, EFS, S3.

## Comparison with nearby patterns
**DataSync** (copy engine) vs **Storage Gateway** (continuous hybrid presentation) vs **Transfer Family** (protocol endpoints).

## Example scenarios
Nightly sync of 5 GB/day from file server to FSx.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- **Schedule + replicate + on-prem agent** → DataSync.
- **Practice (Windows file server Q):** **daily task** language + on-prem **Windows SMB** → **DataSync** destination must match workload (**FSx for Windows**, not EFS/S3 for this stem).
