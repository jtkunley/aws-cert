# Amazon VPC

## What it is
- **Amazon Virtual Private Cloud (VPC)** is your **isolated network** inside an **AWS Region**.
- You define **subnets**, **route tables**, **internet gateways**, **NAT gateways**, **security groups**, and **network ACLs**, and you attach **hybrid** connectivity such as **Direct Connect**, **Site-to-Site VPN**, or **AWS Transit Gateway**.
- Many **managed services** expose **elastic network interfaces (ENIs)** inside your **VPC** so instances and other resources can reach them on **private IP** addresses.

## Personal notes / memory hooks
- When the stem says workloads or file shares are **in the VPC**, think about **private subnets**, **DNS**, and **ENI-based** services such as **Amazon FSx for Windows File Server**.
- **Practice (Windows file server question):** **Windows** instances in **AWS** need a **share they can mount in the VPC**. **FSx** provides that; a design that leaves files **only** in **S3** or **only** behind an **on-premises** gateway often misses the **in-VPC file system** requirement.

## When to use it
- Essentially **every** regional deployment: you place **compute**, **databases**, and **file systems** into **subnets** with the right **routing** and **security** controls.

## When NOT to use it
- You rarely **skip** a **VPC** for normal **regional** workloads. Watch for **over-building**: some questions prefer **VPC endpoints** for **private** access to **AWS services** instead of sending traffic through **NAT** or the **public internet** when that is the point being tested.

## Exam clues
- **Private subnets**, **VPC endpoints**, **peering**, **Direct Connect into the VPC**, and **FSx** or **RDS** **in the VPC**.
- **Practice (SQL Server to MySQL migration question):** A VPN-to-VPC setup can be part of connectivity, but connectivity alone does not replace database migration services like SCT and DMS.

## Common distractors
- Mixing up **VPC** (the **network container**) with **FSx** or **S3** (the **storage**). The stem may mention **VPC** only as the **destination network** for **hybrid** links while the **correct storage** service is still **FSx** or another file or object store.

## Architecture patterns
- **Multi-AZ** subnets for resilience; **hybrid** entry via **Direct Connect** or **VPN** into the **VPC**; **interface endpoints** for services such as **Amazon S3** or **Amazon DynamoDB** when you want **private** access without **internet** egress.

## Comparison with nearby services
- **VPC** is **regional** isolation and routing. **Amazon CloudFront** is **edge** delivery. **Accounts** and **Organizations** define **billing and policy** boundaries separate from **VPC** design.

## Example scenarios
- **Direct Connect** terminates into the **VPC**; **Windows** instances resolve the **FSx** **DNS** name and mount **SMB** shares in the same **VPC** (or connected network).

## Links to related questions
- [Windows File Server, DataSync, and FSx](../questions/windows-file-server-datasync-fsx.md)
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
