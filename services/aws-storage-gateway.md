# AWS Storage Gateway

## What it is
- Hybrid appliance: **File** (SMB/NFS→S3), **Volume** (iSCSI), **Tape** (VTL).

## Personal notes / memory hooks
- Edge bridge to S3—not the same as **FSx ENI in VPC** for cloud Windows compute.
- **Practice (Windows file Q):** replace on-prem server with **File Gateway SMB** → consumer stays **on-prem–centric**; stem wants **AWS servers** + **FSx**.

## When to use it
- Branch cache; tape backup to S3/Glacier; iSCSI lift.

## When NOT to use it
- Stem: managed **Windows file system inside VPC** for migrated instances → **FSx** primary.

## Exam clues
- File Gateway, cache, on-premises appliance, iSCSI, tape.

## Common distractors
- File Gateway “replace file server” when answer is **FSx for AWS-side** workloads.

## Architecture patterns
- SMB on-prem → S3 objects; volume snapshots; tape → Glacier.

## Comparison with nearby services
- **Gateway:** hybrid edge.
- **DataSync:** bulk migration.
- **FSx:** cloud file service.

## Example scenarios
- Office SMB with local cache; not primary for “instances in VPC need Windows FS.”

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
