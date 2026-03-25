# AWS Storage Gateway

## What it is
Hybrid storage service: on-premises appliance/vm connects to AWS. Modes include **File Gateway** (SMB/NFS → **S3** objects), **Volume Gateway** (iSCSI block volumes), **Tape Gateway** (VTL).

## When to use it
Extend cloud storage to the data center with **low-latency local cache**, backup/archive to S3/Glacier, or legacy **iSCSI** apps.

## When NOT to use it
When the stem asks for a **fully managed Windows file system inside AWS VPC** for migrated **EC2/Windows** workloads—**FSx for Windows** is usually cleaner than “SMB at the office backed by S3” as the *primary* answer.

## Exam clues
“On-premises gateway,” “File Gateway,” “cache,” “iSCSI,” “tape backup to S3,” hybrid SMB.

## Common distractors
Choosing **File Gateway** to “replace file server” when the exam wants **native FSx** for **servers in AWS** consuming shares **in-region**.

## Architecture patterns
File Gateway SMB share on-prem → S3; Volume Gateway snapshots to EBS/S3; Tape Gateway to Glacier.

## Comparison with nearby services
**Storage Gateway** (hybrid edge) vs **DataSync** (bulk migration) vs **FSx** (cloud file server).

## Example scenarios
Branch office access with local cache; not the best fit when AWS-side Windows instances need FS in the VPC.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
Gateway = **bridge at the edge**; FSx = **file service in the cloud**.
