# Amazon FSx for Windows File Server

## What it is
- **Amazon FSx for Windows File Server** is a **fully managed Windows file server** in AWS.
- It speaks **SMB**, integrates with **Microsoft Active Directory**, supports features such as **Distributed File System (DFS)**, **shadow copies**, and **NTFS-style** permissions familiar to Windows administrators.

## Personal notes / memory hooks
- When the question mentions a **Windows file server**, **SMB**, and needing a **real share in the VPC**, **FSx for Windows** is usually the first service to check.
- **Practice (Windows file server question):** The correct pattern is often **create an FSx file system**, then run **AWS DataSync** on a **schedule** from the **on-premises Windows server** over **AWS Direct Connect**.

## When to use it
- You are moving or extending **Windows** applications that expect **SMB file shares**, **ACLs**, and **Office-style** workflows.
- **Amazon EC2** instances in a **VPC** need the same kind of **file share** they had on premises, **without** you building a **Windows EC2 file server** yourself.

## When NOT to use it
- The workload is mostly **Linux** with **NFS**—**Amazon EFS** is usually a better fit.
- The requirement is only **FTP into a bucket** or **object analytics**—**S3** and **Transfer Family** may be enough, but that is a different shape than **SMB in the VPC**.

## Exam clues
- **Windows file server**, **SMB**, **migrate shares**, **Active Directory**, **SQL Server** backups to a share, **DataSync** from on-premises **SMB**.

## Common distractors
- Choosing **EFS** for the same **Windows SMB** story.
- Choosing **S3** when the stem clearly wants a **file system** for **Windows apps** in the **VPC**.

## Architecture patterns
- **FSx** lives in the **VPC** with **elastic network interfaces**. Users or instances connect over **SMB**.
- **Hybrid** access over **Direct Connect** or **VPN**, plus **DataSync** for **initial load** and **incremental** updates.
- **Multi-AZ** file systems and **DFS** namespaces where the design calls for them.

## Comparison with nearby services
- **FSx for Windows:** **SMB** for **Windows**.
- **EFS:** **NFS** for **Linux-leaning** workloads.
- **S3:** **object** storage, different access model.
- **FSx for NetApp ONTAP / FSx for OpenZFS:** other **FSx** engines for different **protocol** and **enterprise** needs.

## Example scenarios
- Roughly **1 TB** on a **Windows file server** on premises, **about 5 GB per day** of new data, **Direct Connect** already in place, and **half** of **Windows** workloads already in AWS—the exam wants **FSx** as the **authoritative share in the VPC** for instances there.
- **Practice (Windows file server question):** Matches the **daily DataSync** and **FSx** keyed answer.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
