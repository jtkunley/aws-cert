# File storage vs object storage

## What it is
- **File:** NFS/SMB, paths, POSIX/Windows API.
- **Object:** bucket/key, HTTP API, different consistency model.

## When to use it
- Disambiguate stem: mountable FS vs PUT/GET objects.

## When NOT to use it
- N/A—this is a decision lens.

## Exam clues
- “File system for servers,” SMB/NFS vs bucket/object/S3.

## Common distractors
- DataSync→S3 + Transfer sold as **Windows FS** in VPC.

## Related AWS services
- S3, EFS, FSx (Windows/ONTAP/OpenZFS), EBS.

## Comparison with nearby patterns
- Add **block (EBS):** one instance attach (typical).

## Example scenarios
- Windows apps need drive-style access → **file** tier, not raw S3.
- **Practice (Windows file Q):** S3 remains **object**; FSx is **file**.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Read **file system** in stem literally—S3 ≠ NTFS.
