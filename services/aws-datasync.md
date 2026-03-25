# AWS DataSync

## What it is
- **AWS DataSync** is a **managed online data transfer** service that copies or synchronizes data between **on-premises** storage and **AWS** (or between AWS locations in supported patterns).
- It supports sources such as **NFS**, **SMB**, and **HDFS**, and destinations such as **Amazon S3**, **Amazon EFS**, and **Amazon FSx** (including **FSx for Windows File Server** where applicable).
- You can **schedule** jobs, **throttle** bandwidth, use **encryption**, and **verify** that data arrived intact.

## Personal notes / memory hooks
- When a stem pairs **on-premises shares** with **AWS file systems or buckets** and mentions a **schedule** or **incremental** updates, **DataSync** is often the right migration and sync engine.
- **Practice (Windows file server question):** A **daily scheduled** copy from an **on-premises Windows file server** into **FSx for Windows** over **Direct Connect** matches the keyed answer pattern.

## When to use it
- You need **one-time migration** or **ongoing replication** with **incremental** changes after an initial bulk load.
- You are moving large file datasets over **AWS Direct Connect** or **VPN** and want a **managed** workflow instead of custom scripts.

## When NOT to use it
- You need **offline** seeding of **very large** datasets where **AWS Snow Family** is the better story.
- You are doing **logical database** migration between engines—**AWS Database Migration Service (DMS)** is usually the right tool.
- The requirement is only **SFTP or FTP** ingestion for partners—**AWS Transfer Family** addresses **protocol servers**, not the same copy job model as DataSync.

## Exam clues
- Phrases like **schedule a daily task**, **sync or replicate to S3, EFS, or FSx**, **on-premises to AWS**, **verify transferred data**, and **DataSync agent** on premises.

## Common distractors
- Confusing **DataSync** with **Transfer Family**. Transfer Family exposes **FTP, SFTP, or FTPS** endpoints into **S3**; DataSync is built for **agent-based copy and sync** jobs you define and schedule.

## Architecture patterns
- Install a **DataSync agent** on premises, connect over **Direct Connect** or **VPN**, run an **initial full** transfer, then **incremental** jobs for daily churn (for example **a few gigabytes per day**).

## Comparison with nearby services
- **DataSync:** **copy and sync** jobs between supported endpoints.
- **Storage Gateway:** **hybrid** appliance modes such as **File Gateway** (local cache with **S3** backing).
- **Snow Family:** **physical** shipment for **offline** bulk movement.
- **Transfer Family:** **managed protocol** endpoints for uploads into **S3**.

## Example scenarios
- Roughly **1 TB** on a **Windows file server** with **about 5 GB** of new data per day: **bulk** load first, then **nightly incremental** sync into **FSx** over **Direct Connect**.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
