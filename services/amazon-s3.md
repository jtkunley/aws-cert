# Amazon S3

## What it is
Object storage: buckets, keys, virtually unlimited scale, **11 nines** durability (standard tier), lifecycle, versioning, and many analytics/ML integrations.

## Personal notes / memory hooks
**File system vs bucket**—read the stem literally.

## When to use it
Backups, data lakes, static assets, **Transfer Family** landing zone, **Storage Gateway** backing store, cross-region replication.

## When NOT to use it
When the stem requires a **POSIX/SMB file system** semantics for legacy Windows apps—not **S3** as “the file server” without an overlay (FSx, File Gateway caching story, etc.).

## Exam clues
“Object storage,” “bucket,” “DataSync to S3,” “static website,” “Glacier transition,” “Transfer Family” targets.

## Common distractors
- Treating **S3** as a drop-in replacement for **NTFS/SMB application storage** without clarifying access pattern.
- **Practice (Windows file server Q):** **DataSync to S3 + Transfer Family** does not satisfy **general Windows file system in VPC** for app servers like **FSx** does.

## Architecture patterns
- Data lake on S3; **DataSync** → S3; **File Gateway** SMB → S3 objects; event notifications to Lambda/SQS.

## Comparison with nearby services
**S3** (object) vs **EBS** (block, single AZ attach) vs **FSx/EFS** (file).

## Example scenarios
Archive and analytics landing zone; **not** the primary answer for “Windows file system for apps in VPC” when FSx fits.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
