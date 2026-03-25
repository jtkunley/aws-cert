# File storage vs object storage

## What it is
- **File** storage speaks **NFS** or **SMB**, uses **folders** and paths, and follows **POSIX** or **Windows** semantics on a **mountable** share.
- **Object** storage (for example **Amazon S3**) uses **buckets** and **keys**, **REST**-style access, and a different **consistency** and **locking** model than a traditional **file server**.
- **EFS** and **FSx** sit on the **file** side; **S3** sits on the **object** side.

## When to use it
- Use this lens to **disambiguate** answers when the stem says **file system** versus **bucket** or **object**.
- Applications need either **mountable paths** or **PUT and GET** style **object** workflows and **analytics** on **S3**.

## When NOT to use it
- This section is a **mental model**, not a deployment choice by itself.

## Exam clues
- Contrast **file system for servers**, **SMB**, and **NFS** with **bucket**, **object**, and **S3**.

## Common distractors
- **DataSync into S3** plus **Transfer Family** is presented as equal to **FSx** for **Windows application** storage; that is usually wrong when the stem insists on a **file system** in the **VPC** for **Windows** servers.

## Related AWS services
- **Amazon S3**, **Amazon EFS**, **Amazon FSx** (Windows, ONTAP, OpenZFS), **Amazon EBS**.

## Comparison with nearby patterns
- Add **block** storage (**EBS**) as a third axis: volumes **attach** to an instance and are not a **shared SMB** story for many workloads.

## Example scenarios
- **Windows** applications in **AWS** expect **drive-letter** style access—choose the **file** tier, not raw **S3** objects, unless another service bridges the gap.

## Links to related questions
- [Windows File Server, DataSync, and FSx](../questions/windows-file-server-datasync-fsx.md)

## Personal notes / memory hooks
- Read **file system** literally: **S3 is not NTFS**.
- **Practice (Windows file server question):** **DataSync to S3** still lands **objects**; it does not satisfy **SMB share** semantics for typical **Windows** apps in the **VPC** by itself.
