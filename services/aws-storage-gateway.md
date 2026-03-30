# AWS Storage Gateway

## What it is
- **AWS Storage Gateway** is a **hybrid storage** service. You run a **virtual or hardware appliance** on premises that connects to **AWS**.
- Common modes include **File Gateway** (**SMB** or **NFS** front end with **Amazon S3** as the backing store), **Volume Gateway** (**iSCSI** block volumes with **Amazon Elastic Block Store (EBS)** snapshot integration), and **Tape Gateway** (**virtual tape library** style backups toward **S3** and **Amazon S3 Glacier** tiers).

## Personal notes / memory hooks
- Think of the gateway as a **bridge at the edge** of your data center. **Amazon FSx for Windows File Server** is a **fully managed file system inside the VPC** for **Windows** workloads already running in **AWS**.
- **Practice (Windows file server question):** An answer that keeps **SMB** on premises via **File Gateway** and tells you to **point shares at the gateway** keeps the emphasis at the **edge**. When the stem wants **servers in AWS** to use a **native Windows file share in the Region**, **FSx** is usually the cleaner primary choice.

## When to use it
- You need **low-latency local access** with **cloud** backing, **backup** or **archive** to **S3** or **Glacier**, or legacy **iSCSI** applications that snapshot to **AWS**.

## When NOT to use it
- The question asks for a **fully managed Windows file system in the VPC** for **EC2** instances that migrated into **AWS**. **FSx for Windows** often wins over “**SMB at the office backed by S3**” as the **main** answer for that **in-cloud** consumption pattern.

## Exam clues
- **On-premises gateway**, **File Gateway**, **cache**, **iSCSI**, **tape backup to S3**, and hybrid **SMB** language.

## Common distractors
- Choosing **File Gateway** to **replace** a corporate file server when the exam really wants **FSx** so **AWS-resident Windows** instances mount shares **in-Region** on **ENIs** in the **VPC**.

## Architecture patterns
- **File Gateway** **SMB** share on premises with objects landing in **S3**; **Volume Gateway** with **iSCSI** and **EBS** snapshots; **Tape Gateway** toward **S3** and **Glacier** for **VTL** workflows.

## Comparison with nearby services
- **Storage Gateway:** **hybrid edge** appliance story.
- **DataSync:** **bulk migration and sync** jobs.
- **FSx:** **managed file server** in **AWS** (for example **SMB** with **Windows** integration).

## Example scenarios
- Branch offices that need **local cache** with **cloud** durability; **not** the best primary fit when **Windows** instances in a **VPC** need a **first-class SMB file system** in **AWS**.

## Links to related questions
- [2. Windows File Server, DataSync, and FSx](../questions/2-windows-file-server-datasync-fsx.md)
