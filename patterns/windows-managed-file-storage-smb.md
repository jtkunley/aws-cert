# Windows managed file storage (SMB)

## What it is
Cloud **file shares** that preserve **Windows/SMB** expectations: permissions, legacy apps, often **Active Directory** integration—**Amazon FSx for Windows File Server** is the flagship.

## When to use it
Windows file server migration, SQL backup targets needing SMB, Office shares, DFS.

## When NOT to use it
Linux-heavy **NFS** scale-out—**EFS**; object analytics lake—**S3**.

## Exam clues
“Windows file server,” “SMB,” “NTFS/ACL,” “AD joined file system.”

## Common distractors
**EFS** “because it’s elastic file”—wrong protocol/workload fit for classic Windows shares.

## Related AWS services
FSx for Windows, Directory Service, DataSync, EC2 (self-managed file server—usually disfavored vs FSx).

## Comparison with nearby patterns
**SMB Windows** vs **NFS Linux** vs **object (S3)**.

## Example scenarios
Replace on-prem 1 TB share with FSx in VPC for instances in AWS.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- **Windows** in the first sentence of the stem → **FSx for Windows** until proven otherwise.
- **Practice (Windows file server Q):** requirement **“file system for the servers in AWS”** → **FSx in VPC**, not **File Gateway SMB on-prem** or **S3 + Transfer**.
