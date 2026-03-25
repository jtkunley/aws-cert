# Amazon Elastic File System (EFS)

## What it is
- **Amazon Elastic File System (EFS)** provides a **managed NFS file system** that **grows and shrinks** automatically.
- Many **Linux instances** (and containers) can mount it at once across **Availability Zones** using a standard **POSIX** file interface.

## Personal notes / memory hooks
- **Linux** workloads that need **shared file storage** over **NFS** → **EFS** is a natural fit.
- **Windows file shares** that need **SMB** semantics → look at **Amazon FSx for Windows File Server**, not EFS as the primary answer.
- **Practice (Windows file server question):** An option that pairs **EFS**, **DataSync**, and “mount on **Windows** servers” is often a **trap** because **EFS** is **NFS-oriented** and the exam usually wants **FSx for Windows** for classic **Windows file server** language.

## When to use it
- **Linux** web or content tiers that share files.
- **Containers** on **Amazon ECS** or **EKS** that need a **shared volume**.
- **CI** artifacts or other **POSIX** workloads with **many concurrent** readers and writers.

## When NOT to use it
- The scenario centers on a **Windows file server**, **SMB**, and **Active Directory** file semantics—**FSx for Windows** is usually correct.
- The requirement is **object storage** or **HTTP API** access to blobs—**Amazon S3** fits that model.

## Exam clues
- **NFS**, **Linux**, **mount targets** in subnets, **elastic file**, **thousands of connections**.

## Common distractors
- Picking **EFS** when the stem clearly describes **Windows** and **SMB** as the main requirement.
- **Practice (Windows file server question):** **EFS plus DataSync** is the right **engine** class but the **wrong destination** for **Windows SMB** compared with **FSx for Windows**.

## Architecture patterns
- One **mount target per Availability Zone** in the **VPC**.
- **ECS** or **EKS** tasks mount **EFS** for shared state.
- **DataSync** can copy from on-premises **NFS** into **EFS** for migration.

## Comparison with nearby services
- **EFS:** **NFS**, strong **Linux** story.
- **FSx for Windows File Server:** **SMB** for **Windows**.
- **FSx for NetApp ONTAP / OpenZFS:** other **enterprise file** patterns.

## Example scenarios
- An **Auto Scaling** group of **Linux** web servers sharing content under a common mount point.
- **Not** the first choice for **traditional corporate Windows shares** in exam wording.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)
