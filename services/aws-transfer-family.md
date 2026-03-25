# AWS Transfer Family

## What it is
- Managed **SFTP, FTP, FTPS** into **S3** (EFS supported in some flows).

## Personal notes / memory hooks
- Protocol servers for partners—not SMB corporate file server in VPC.
- **Practice (Windows file Q):** paired with S3 in distractor; **FTP/SFTP** ≠ **Windows share** for general app access.

## When to use it
- B2B file drops to S3; retire self-hosted FTP EC2.

## When NOT to use it
- Stem: SMB **Windows file system** for instances—**FSx + DataSync**.

## Exam clues
- SFTP, FTP, partner ingest, managed transfer.

## Common distractors
- Transfer Family as **Windows file server** replacement.

## Architecture patterns
- Transfer endpoint → S3; IAM home directory mapping; Lambda post-process.

## Comparison with nearby services
- **Transfer:** protocol front door.
- **DataSync:** agent sync engine.
- **Gateway:** hybrid presentation.

## Example scenarios
- Vendor CSV via SFTP to landing bucket.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
