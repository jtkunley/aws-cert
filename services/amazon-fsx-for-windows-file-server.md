# Amazon FSx for Windows File Server

## What it is
- Managed **SMB** / Windows Server file shares; AD, DFS, shadow copies, NTFS-style ACLs.

## Personal notes / memory hooks
- Windows + SMB + “file system in AWS” → FSx for Windows first.
- **Practice (Windows file Q):** FSx share + **daily DataSync** from on-prem SMB; **~1 TB** + **5 GB/day**; **half** workload already in cloud.

## When to use it
- Windows apps need real shares in **VPC**; no self-managed Windows file EC2.

## When NOT to use it
- Linux NFS primary—**EFS**.
- FTP-only to bucket—wrong tool.

## Exam clues
- Windows file server, SMB, migrate shares, AD, SQL backup share, DataSync source/target.

## Common distractors
- EFS or S3 for same Windows SMB story.

## Architecture patterns
- FSx in VPC + DX/VPN; DataSync on-prem SMB → FSx; multi-AZ; DFS.

## Comparison with nearby services
- **FSx Windows:** SMB.
- **EFS:** NFS.
- **S3:** object.
- **FSx ONTAP/OpenZFS:** other protocols/use cases.

## Example scenarios
- On-prem 1 TB share; AWS Windows instances need identical semantics.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
