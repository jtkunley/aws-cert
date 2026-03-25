# Amazon Elastic File System (EFS)

## What it is
Managed **NFS** file storage that **scales elastically**, shared across **many** Linux instances/AZ; POSIX file API.

## Personal notes / memory hooks
**Linux + NFS** → EFS. **Windows + SMB** → FSx for Windows.

## When to use it
Linux web/content tiers, containers needing shared file state, CI artifacts, **high concurrency** readers/writers with NFS.

## When NOT to use it
Primary **Windows SMB / AD-integrated file server** replacement—exam usually prefers **FSx for Windows**; strict **Windows ACL** semantics as the main story.

## Exam clues
“NFS,” “Linux,” “thousands of connections,” “elastic file,” “mount targets in subnets.”

## Common distractors
- Picking **EFS** when the stem screams **Windows file server** and **SMB**—wrong workload fit.
- **Practice (Windows file server Q):** **EFS + DataSync + mount on Windows**—exam trap; **NFS/Linux-leaning** vs **FSx for Windows** for SMB semantics.

## Architecture patterns
- EFS mount targets per AZ; ECS/EKS persistent shared storage; hybrid copy via **DataSync** to EFS.

## Comparison with nearby services
**EFS** (NFS, Linux-leaning) vs **FSx for Windows** (SMB) vs **FSx ONTAP** (multi-protocol enterprise).

## Example scenarios
Auto-scaling Linux fleet sharing `/mnt/content`; **not** the best answer for classic Windows shares.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
