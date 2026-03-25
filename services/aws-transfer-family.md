# AWS Transfer Family

## What it is
- **AWS Transfer Family** provides **managed file transfer protocol** endpoints for **FTP**, **SFTP**, and **FTPS**.
- Clients connect the way they always have; **AWS** runs the **protocol servers**. Data typically lands in **Amazon S3**, and **Amazon EFS** is supported in **supported** integration patterns where the exam scenario applies.

## Personal notes / memory hooks
- **Protocol names** in the stem (**SFTP**, **FTP**, **FTPS**) point toward **Transfer Family**. **Scheduled copy jobs** with a **DataSync agent** point toward **DataSync**.
- **Practice (Windows file server question):** A distractor may bundle **Transfer Family** with **S3**. That gives you **FTP-style** access to **objects**, not a **SMB file share** in the **VPC** for **general Windows** application file serving.

## When to use it
- **Business-to-business** file exchange where partners upload files with **SFTP** or legacy **FTP** clients.
- You want to **retire self-hosted** transfer servers on **EC2** and use a **fully managed** endpoint with **IAM**-aware access to **S3** prefixes.

## When NOT to use it
- The requirement is **SMB** **Windows shares** in the **VPC** for day-to-day corporate file access. **FSx for Windows** plus **DataSync** (when migrating from on premises) usually matches that story better than **Transfer Family** plus **S3** alone.

## Exam clues
- **SFTP**, **FTP**, **third-party upload to S3**, **managed file transfer**, and **B2B ingest** language.

## Common distractors
- Treating **Transfer Family** as a **Windows file server** replacement for **SMB** workloads.
- Confusing it with **DataSync**, which is an **agent-based** **copy and sync** engine, not a **protocol listener** for external partners.

## Architecture patterns
- **Transfer Family** server in front of an **S3** bucket with **IAM** mappings; optional **AWS Lambda** for **decryption** or **post-processing** after upload.

## Comparison with nearby services
- **Transfer Family:** **protocol servers** for **FTP family** clients.
- **DataSync:** **migration and synchronization** between **on-premises** agents and **AWS** storage.
- **Storage Gateway:** **hybrid** appliance at the **edge** with **File**, **Volume**, or **Tape** modes.

## Example scenarios
- A vendor drops **CSV** files via **SFTP** into a **landing bucket** for downstream **ETL**.

## Links to related questions
- [Windows File Server, DataSync, and FSx](../questions/windows-file-server-datasync-fsx.md)
