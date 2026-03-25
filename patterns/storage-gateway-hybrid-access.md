# Storage Gateway hybrid access

## What it is
- **AWS Storage Gateway** runs as an **appliance** or **virtual machine** **on premises** or at the **edge** and presents **SMB**, **NFS**, or **iSCSI** while backing data to **Amazon S3** or related **AWS** storage (depending on mode).
- **File Gateway**, **Volume Gateway**, and **Tape Gateway** each target different **legacy** and **backup** patterns with **low-latency local** access and **durable** cloud backing.

## When to use it
- **Branch offices** need **cached** reads, or you extend **legacy** applications to **cloud** storage **without** rewriting them to the **S3 API** first.

## When NOT to use it
- The exam wants a **managed file system** with **ENIs in the VPC** for **instances already in AWS**—compare carefully to **FSx**; the gateway story is often **on-premises-centric**.

## Exam clues
- **Storage Gateway**, **File Gateway**, **on-premises SMB**, **cache**, and **tape backup** language.

## Common distractors
- Choosing **File Gateway** when the correct answer is **FSx** for **Windows** workloads running **in the VPC**.

## Related AWS services
- **Storage Gateway**, **Amazon S3**, **Direct Connect**, **DataSync**.

## Comparison with nearby patterns
- **Gateway hybrid** access differs from **DataSync migration** jobs and from **FSx** as **native cloud file**.

## Example scenarios
- Office workers use an **SMB** share that lands in **S3**; that is a different shape from **AWS servers** that need an **FSx** share **in-Region**.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- Ask **where** the **primary consumers** live: **on-premises users** versus **instances in the VPC**.
- **Practice (Windows file server question):** The distractor **replaces the on-premises file server with File Gateway** keeps the story at the **edge** instead of giving **AWS-resident** servers a **VPC** **FSx** share.
