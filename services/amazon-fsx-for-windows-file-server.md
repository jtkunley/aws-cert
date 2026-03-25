# Amazon FSx for Windows File Server

## What it is
Fully managed **Windows file shares** (SMB) in AWS, built on Windows Server, with **Active Directory** integration, **DFS**, shadow copies, and native Windows file semantics.

## When to use it
Lift-and-shift or hybrid **Windows** apps needing **SMB**, ACLs, and Office/legacy file workflows; users or instances in the VPC need a **real file server** without self-managing Windows EC2 file servers.

## When NOT to use it
Primarily **Linux** scale-out with NFS and POSIX-heavy patterns—consider **EFS**; **read-heavy analytics** on objects—**S3**; if the stem only needs **FTP to a bucket**—not FSx.

## Exam clues
“Windows file server,” “SMB,” “migrate on-premises Windows shares,” “AD domain,” “SQL Server file share backups,” pair with **DataSync** from on-prem.

## Common distractors
Choosing **EFS** for the same Windows file-server story; choosing **S3** when the requirement is a **file system** for Windows apps.

## Architecture patterns
FSx in VPC + **Direct Connect**/VPN; **DataSync** from on-premises SMB to FSx; multi-AZ file systems; DFS namespaces.

## Comparison with nearby services
**FSx for Windows** (SMB/Windows) vs **FSx for NetApp ONTAP / OpenZFS** (multi-protocol, different use cases) vs **EFS** (NFS, Linux-leaning) vs **S3** (object).

## Example scenarios
1 TB on-prem Windows share; daily deltas; workloads already in AWS need the same share semantics.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
**Windows + SMB + “file system in AWS”** → FSx for Windows first.
