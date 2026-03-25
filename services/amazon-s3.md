# Amazon S3

## What it is
- **Object** storage: buckets, keys, versioning, lifecycle, events.

## Personal notes / memory hooks
- File system vs bucket—read stem literally.
- **Practice (Windows file Q):** DataSync→S3 + Transfer Family ≠ VPC **Windows file system** for app servers.

## When to use it
- Data lake, backup target, static assets, Transfer Family landing, Gateway backing store.

## When NOT to use it
- Stem requires **SMB/NTFS app semantics** without FSx/Gateway overlay.

## Exam clues
- Bucket, object, DataSync to S3, Glacier lifecycle.

## Common distractors
- S3 sold as drop-in **Windows app file share**.

## Architecture patterns
- Lake; DataSync→S3; File Gateway SMB→objects; S3→Lambda/SQS events.

## Comparison with nearby services
- **S3:** object.
- **EBS:** block, one instance (mostly).
- **EFS/FSx:** file.

## Example scenarios
- Landing zone for analytics; static site.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
