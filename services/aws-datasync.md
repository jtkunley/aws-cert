# AWS DataSync

## What it is
Managed **online data transfer** between on-premises storage (NFS, SMB, HDFS) and AWS (**S3**, **EFS**, **FSx** families), with scheduling, bandwidth limits, encryption, and data verification.

## When to use it
**Recurring or one-time migration**, **incremental sync**, hybrid copies over **Direct Connect** or VPN; when the exam mentions **scheduled tasks** copying large datasets to AWS.

## When NOT to use it
One-off **offline** petabyte seed where **Snow Family** wins; database **logical** migration—use **DMS**; ultra-custom protocol needs beyond supported agents/endpoints.

## Exam clues
- “Schedule a daily task,” “replicate/sync to S3/EFS/FSx,” “on-premises to AWS,” “verify transferred data,” agent on-prem.
- **Practice (Windows file server Q):** **daily scheduled** replication between **on-prem Windows file server** and **FSx** (keyed answer).

## Common distractors
- Confusing with **Transfer Family** (managed file transfer *protocols* into S3, not the same as DataSync’s copy engine story).

## Architecture patterns
- DataSync agent on-prem → **Direct Connect** → FSx/S3/EFS; initial bulk + **incremental** for daily **GB** churn.

## Comparison with nearby services
- **DataSync** (copy/sync jobs) vs **Storage Gateway** (hybrid local caching/gateway modes) vs **Snowball** (offline) vs **Transfer Family** (SFTP/FTP/FTPS to S3).

## Example scenarios
- 5 GB/day new data from Windows file server to **FSx** with nightly task.
- **Practice (Windows file server Q):** same volume/churn numbers justify **incremental** sync after initial bulk over **Direct Connect**.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Stem pairs **on-prem share + AWS filesystem/bucket + schedule** → **DataSync** is the default hammer.
