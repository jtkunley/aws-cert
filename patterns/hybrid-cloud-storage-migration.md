# Hybrid cloud storage migration

## What it is
- You keep **on-premises** systems running while you **move** or **mirror** data into **AWS** over **private** or **VPN** links such as **AWS Direct Connect** or **Site-to-Site VPN**.
- Migrations are often **phased**: part of the workload is already in the cloud, and data must stay **consistent** across both sides for a while.

## When to use it
- Part of the workload is **already in AWS**, but **source systems** or **users** remain on premises.
- You need **ongoing sync**, **regulated** network paths, or **large** datasets that benefit from a **predictable** pipe into a **VPC**.

## When NOT to use it
- The project is **greenfield** and **fully in the cloud** with no on-premises source.
- The first load is **offline-only**—**Snow Family** may headline the **initial seed** story.

## Exam clues
- Look for **on-premises**, **Direct Connect to the VPC**, **half migrated**, **hybrid**, and **Windows server still on premises**.

## Common distractors
- Choosing **only** **Direct Connect** without naming **how** data moves (**DataSync**, **Storage Gateway**, and so on) or **where** it lands (**FSx**, **S3**).
- Mixing up **hybrid access** through a **gateway on premises** with a **cloud-native file system** (**FSx** **ENIs** in the **VPC**).

## Related AWS services
- **Direct Connect**, **VPN**, **DataSync**, **Storage Gateway**, **Amazon FSx**, **Amazon S3**, **AWS Snow Family**.

## Comparison with nearby patterns
- **Hybrid migration** differs from **lift-and-shift everything to EC2** and from a **cloud-only** greenfield design.

## Example scenarios
- About **1 TB** on a **Windows** share on premises; **Windows** instances in a **VPC** need that data on a **file system in AWS**—often **FSx** plus **DataSync** over **Direct Connect**.
- **Practice (Windows file server question):** About **half** of **Windows** workloads migrated, **1 TB** plus **5 GB per day**, **Direct Connect** already there—you still add **DataSync** and **FSx** so **AWS** servers get a **proper share**.

## Links to related questions
- [Windows File Server, DataSync, and FSx](../questions/windows-file-server-datasync-fsx.md)

## Personal notes / memory hooks
- **Direct Connect** in the stem means you already have a **path**; you still choose **what moves the bits** and **where they live**.
