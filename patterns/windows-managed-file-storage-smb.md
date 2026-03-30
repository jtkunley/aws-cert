# Windows managed file storage (SMB)

## What it is
- This pattern covers **cloud file shares** that match **Windows** expectations: **SMB**, familiar **permissions**, legacy applications, and often **Microsoft Active Directory** integration.
- **Amazon FSx for Windows File Server** is the flagship **managed** service for this story on **AWS**.

## When to use it
- You are migrating a **Windows file server**, need **SMB** targets for **SQL Server** backups, **Office** style shares, or **Distributed File System (DFS)** namespaces.

## When NOT to use it
- The estate is mostly **Linux** with **NFS** at scale—**Amazon EFS** is usually a better fit.
- The workload is an **analytics lake** or **object** workflow—**Amazon S3** fits that model.

## Exam clues
- Phrases like **Windows file server**, **SMB**, **NTFS-style ACLs**, and **Active Directory**-joined file systems.

## Common distractors
- Picking **EFS** because the word **elastic file** appears, even when the stem is clearly **Windows** and **SMB**.

## Related AWS services
- **FSx for Windows File Server**, **AWS Directory Service**, **DataSync**, **Amazon EC2** (self-managed file server—usually disfavored versus **FSx** in exam answers).

## Comparison with nearby patterns
- Contrast **SMB Windows** file shares with **NFS Linux** patterns and with **object storage** on **S3**.

## Example scenarios
- Replace an on-premises **1 TB** share with **FSx** in the **VPC** so instances in **AWS** mount the same style of share.

## Links to related questions
- [2. Windows File Server, DataSync, and FSx](../questions/2-windows-file-server-datasync-fsx.md)

## Personal notes / memory hooks
- When **Windows** appears in the **first** sentence of the stem, assume **FSx for Windows** until another requirement clearly overrides it.
- **Practice (Windows file server question):** The phrase **file system for the servers in AWS** points to **FSx in the VPC**, not **File Gateway SMB on premises** or **S3 plus Transfer Family** alone.
