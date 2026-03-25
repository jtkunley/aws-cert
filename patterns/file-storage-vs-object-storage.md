# File storage vs object storage

## What it is
**File** (NFS/SMB, folders, POSIX/Windows semantics) vs **object** (flat namespace, keys, HTTP API, different consistency model)—**EFS/FSx** vs **S3**.

## When to use it
Disambiguate exam answers: apps need **mountable file paths** vs **PUT/GET objects** and analytics.

## When NOT to use it
N/A—this is a lens, not a deployment choice by itself.

## Exam clues
“File system for servers,” “SMB,” “NFS,” vs “bucket,” “object,” “S3.”

## Common distractors
**DataSync to S3 + Transfer** presented as equivalent to **FSx** for Windows app storage—usually wrong when stem demands **file system** semantics in VPC.

## Related AWS services
S3, EFS, FSx (Windows/ONTAP/OpenZFS), EBS.

## Comparison with nearby patterns
**Block (EBS)** is third axis: attach volume to **one** instance (mostly).

## Example scenarios
Windows apps in AWS need drive-letter style access → **file** tier, not raw S3 objects.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
Read “file system” literally—**S3 is not NTFS**.
