# Windows managed file storage (SMB)

## What it is
- Cloud **SMB** shares with Windows semantics—**FSx for Windows File Server** flagship.

## When to use it
- Windows file server migration; SQL backup to share; Office/DFS.

## When NOT to use it
- Linux NFS scale-out—**EFS**.
- Object lake—**S3**.

## Exam clues
- Windows file server, SMB, AD-joined share, NTFS ACL.

## Common distractors
- **EFS** “because elastic file.”

## Related AWS services
- FSx for Windows, Directory Service, DataSync.

## Comparison with nearby patterns
- **SMB Windows** vs **NFS Linux** vs **S3 object**.

## Example scenarios
- 1 TB on-prem SMB → FSx for instances in VPC.
- **Practice (Windows file Q):** **“file system for servers in AWS”** → FSx, not Gateway-on-prem-only.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- First line says **Windows file server** → FSx for Windows until disproven.
