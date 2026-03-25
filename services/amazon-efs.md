# Amazon Elastic File System (EFS)

## What it is
- **NFS** file storage; elastic; many Linux instances; POSIX.

## Personal notes / memory hooks
- Linux + NFS → EFS. Windows SMB → **FSx for Windows**.
- **Practice (Windows file Q):** EFS+DataSync+mount on Windows → trap; pick **FSx for Windows**.

## When to use it
- Linux web/content; shared container storage; CI artifacts; high NFS concurrency.

## When NOT to use it
- Primary **Windows file server / SMB** story—**FSx for Windows**.

## Exam clues
- NFS, Linux, mount targets, thousands of connections.

## Common distractors
- EFS chosen when stem says **Windows file server**.

## Architecture patterns
- Mount target per AZ; ECS/EKS shared volumes; DataSync → EFS.

## Comparison with nearby services
- **EFS:** NFS.
- **FSx Windows:** SMB.
- **FSx ONTAP:** multi-protocol enterprise.

## Example scenarios
- ASG Linux fleet shares `/mnt/content`.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
