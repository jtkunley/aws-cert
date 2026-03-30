# AWS Direct Connect

## What it is
- **AWS Direct Connect** provides **dedicated or hosted private network connectivity** from your **on-premises** environment into **AWS**.
- Traffic does not ride the **public internet** the way a typical **VPN over the internet** path does, which helps with **predictable throughput**, **lower and steadier latency**, and **consistent** hybrid networking.
- You connect into **Amazon Virtual Private Cloud (VPC)** using **virtual interfaces (VIFs)** and can reach many **AWS public services** through the appropriate **public or private** interface patterns.

## Personal notes / memory hooks
- Treat **Direct Connect** as the **network pipe**. The exam still expects you to pick the service that **moves or serves** the data (**DataSync**, **Storage Gateway**, **FSx**, and so on).
- **Practice (Windows file server question):** When the stem says **Direct Connect** is already in place into the **VPC**, pair it with **DataSync** and **FSx for Windows** rather than naming **Direct Connect** as if it alone **migrated** the files.

## When to use it
- **Hybrid** architectures with **steady, large** data movement or **low-latency** needs between the data center and **AWS**.
- Compliance or operations teams want a **private** path instead of routing everything over the **public internet**.

## When NOT to use it
- **Small** or **sporadic** transfers where **Site-to-Site VPN** is enough and you want **faster** setup without **physical** or **hosted** connectivity lead time.

## Exam clues
- Wording like **Direct Connect to the VPC**, **private connection from on-premises**, **consistent network for migration**, and hybrid diagrams that show a **private link** into **AWS**.

## Common distractors
- Choosing **Direct Connect** as the **only** answer when the question is really about **where files land** (**FSx**, **S3**) and **how** they are copied (**DataSync**). **Direct Connect** does not replace those services.

## Architecture patterns
- **Private VIF** into a **VPC**; **redundant** connections for resilience; advanced designs may use **AWS Transit Gateway** with **Direct Connect**.

## Comparison with nearby services
- **Direct Connect** versus **Site-to-Site VPN**: VPN is often **quicker** to stand up and runs over the **internet**; **Direct Connect** is a **private** circuit story with a different **provisioning** profile.
- **VPC peering** connects **VPC to VPC** in the cloud; it is **not** the on-premises link.

## Example scenarios
- Replicating a **Windows file server** into **FSx** over **Direct Connect** so **nightly sync** jobs are **reliable** and **fast** compared with a **variable** internet uplink.

## Links to related questions
- [2. Windows File Server, DataSync, and FSx](../questions/2-windows-file-server-datasync-fsx.md)
