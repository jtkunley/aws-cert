# AWS Transfer Family

## What it is
Managed **FTP, SFTP, FTPS** endpoints that integrate with **S3** (and **EFS** in supported patterns), for partners and legacy transfer clients.

## When to use it
B2B file exchange via **SFTP/FTP**, replacing self-hosted transfer servers; ingest to **S3** without custom EC2 FTP.

## When NOT to use it
When the requirement is **SMB Windows shares** in VPC for general corporate file serving—**FSx** + **DataSync** beats “Transfer + S3” as the Windows file story.

## Exam clues
“SFTP/FTP,” “third-party upload to S3,” “managed file transfer,” B2B ingest.

## Common distractors
- Confusing with **DataSync** (agent-based copy/sync) or using Transfer as a **Windows file server** substitute.
- **Practice (Windows file server Q):** bundled with **S3** in a distractor—**FTP/SFTP/FTPS** access pattern ≠ **SMB file share** for migrated Windows apps in VPC.

## Architecture patterns
- Transfer Family → S3 bucket; IAM mapping; optional PGP/decryption workflows with Lambda.

## Comparison with nearby services
**Transfer Family** (protocol servers) vs **DataSync** (migration/sync engine) vs **Storage Gateway** (hybrid).

## Example scenarios
Vendor drops CSV via SFTP into a landing bucket.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
**Protocols (SFTP/FTP)** → Transfer Family. **Copy/sync jobs** → DataSync.
