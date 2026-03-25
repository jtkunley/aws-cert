# DataSync migration and replication

## What it is
- This pattern uses **AWS DataSync** for **one-time** or **scheduled** data movement between **on-premises** storage and **AWS** (or between supported AWS locations).
- DataSync handles **verification**, **bandwidth throttling**, and **incremental** sync after an initial copy from sources such as **NFS** or **SMB** into destinations such as **Amazon S3**, **Amazon EFS**, or **Amazon FSx**.

## When to use it
- You have **daily churn** after a large initial dataset, or you are preparing for **cutover** with repeated sync jobs.
- The stem uses language like **schedule a daily task** to **replicate** or **sync** data from on premises into **FSx**, **S3**, or **EFS**.

## When NOT to use it
- Partners need **SFTP or FTP** uploads into a bucket—**AWS Transfer Family** fits that protocol story.
- You need **ongoing logical replication** between databases—**AWS Database Migration Service (DMS)** is the usual answer.
- You need **offline** bulk movement—**AWS Snow Family** is the truck-and-device path.

## Exam clues
- Watch for **DataSync**, **agent**, **scheduled replication**, **on-premises to FSx, S3, or EFS**, and **bandwidth** limits.

## Common distractors
- The answer names **DataSync** correctly but picks the **wrong destination** for the workload—for example **EFS** instead of **FSx for Windows File Server** when the stem is clearly **Windows** and **SMB**.

## Related AWS services
- **AWS DataSync**, **AWS Direct Connect**, **Amazon FSx**, **Amazon EFS**, **Amazon S3**.

## Comparison with nearby patterns
- **DataSync** is the **copy and sync engine**.
- **Storage Gateway** **presents** storage **continuously** at the **hybrid edge**.
- **Transfer Family** exposes **FTP-family** endpoints for **ingest**.

## Example scenarios
- **Nightly** sync of about **5 GB per day** from a **Windows file server** into **FSx** after the **1 TB** bulk load.

## Links to related questions
- [Q: Windows file server → FSx + DataSync](../questions/q-windows-fileserver-datasync-fsx.md)

## Personal notes / memory hooks
- **Schedule**, **replicate**, and **on-premises agent** together strongly suggest **DataSync**.
- **Practice (Windows file server question):** **Daily task** language plus on-premises **Windows SMB** means the **DataSync destination** must match the workload—usually **FSx for Windows**, not **EFS** or **S3** for this stem.
