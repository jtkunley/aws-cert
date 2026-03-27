# Legacy EC2 data tier

## What it is
- A **transitional** or **undesirable** state where **databases** such as **MySQL** or **PostgreSQL** run **self-managed** on **Amazon EC2**.
- You handle **patching**, **backups**, **failover**, and **scaling** yourself instead of using a **managed** database or **warehouse** service.

## When to use it
- **Rare** in **greenfield** designs; sometimes **compliance**, **exotic extensions**, or a **migration** **interim** keeps engines on **EC2**.

## When NOT to use it
- Exam scenarios ask for **managed**, **serverless**, or **higher availability** with **less operations**—answers should move toward **Amazon Aurora** or **RDS**, **DynamoDB**, **Redshift**, or other **managed** tiers.

## Exam clues
- **Database on EC2**, **self-managed**, **patching**, **manual failover**, and **legacy** language.

## Common distractors
- Assuming **EC2** plus **Auto Scaling** **modernizes** the **data plane**—it does **not** replace **managed** database services by itself.
- Keeping always-on **EC2** workers for bursty jobs can miss a cheaper event-driven model when serverless containers are available.

## Related AWS services
- **EC2**, **EBS**, **RDS**, **Aurora**, **DMS** for **migration**, and **backup** strategies.

## Comparison with nearby patterns
- **Self-managed on EC2** differs from **RDS** or **Aurora**, where **AWS** manages more of the **engine** operations, and from **Redshift** for **analytics warehouse** roles.

## Example scenarios
- **Starting state** in a stem: **e-commerce MySQL** and **analytics PostgreSQL** both on **EC2** before migration.
- **Practice (serverless modernization question):** Split targets are **Aurora Serverless MySQL** for **OLTP** and **Redshift Serverless** for the **warehouse**, not **one** **Aurora PostgreSQL** cluster for **both** roles.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)

## Personal notes / memory hooks
- When the stem opens with **ugly EC2 databases**, the **correct** path usually **lifts** data to **managed** or **serverless** tiers.
