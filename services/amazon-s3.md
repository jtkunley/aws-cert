# Amazon S3

## What it is
- **Amazon Simple Storage Service (S3)** is **object storage**: you store **objects** in **buckets** under **keys**.
- It scales to very large data sets, offers **durability** targets for standard storage classes, and supports **versioning**, **lifecycle** rules, **event notifications**, and integrations across analytics and machine learning.

## Personal notes / memory hooks
- Read the stem carefully when it says **file system** versus **bucket** or **object**. **S3** is **not** a **Windows SMB share** by itself.
- **Practice (Windows file server question):** **DataSync** into **S3** plus **AWS Transfer Family** still leaves you in the **object** world. That usually does **not** satisfy “**file system for the servers in AWS**” the way **FSx for Windows** does.

## When to use it
- **Data lakes**, **backups**, **static websites**, **log** archives, and **big data** landing zones.
- Ingest from **Transfer Family** (SFTP/FTP) or as the backing store behind **Storage Gateway** file interfaces.

## When NOT to use it
- The application expects a **POSIX** or **SMB** **file system** with **directory and locking** semantics like a traditional **Windows** file server, unless another service (for example **FSx**) provides that layer.

## Exam clues
- **Bucket**, **object**, **S3**, **lifecycle**, **Glacier** transitions, **static website hosting**, **Transfer Family** landing in S3.

## Common distractors
- Treating **S3** as a plug-in replacement for **NTFS/SMB application storage** without an appropriate **file** service on top.
- **Practice (Windows file server question):** **S3** remains **object storage**; it does not become a **managed Windows file share in the VPC** just because **DataSync** copied files there.
- **Practice (SQL Server to MySQL migration question):** S3 backup and load workflows are often a distractor when the requirement is heterogeneous database migration with managed schema conversion and replication.

## Architecture patterns
- **Data lake** on S3 with **AWS Glue**, **Athena**, or **Redshift Spectrum**.
- **DataSync** bulk copy into S3.
- **S3 event notifications** to **Lambda** or **SQS**.
- **File Gateway** presents **SMB** on premises while storing **objects** in S3.
- **Practice (video transcoding question):** Upload events in **S3** can trigger **Lambda**, which then starts **ECS Fargate** tasks for long-running processing.

## Comparison with nearby services
- **S3:** **object** store with a **REST** API model.
- **EBS:** **block** volumes attached to **one instance** in most cases.
- **EFS / FSx:** **file** protocols (**NFS** or **SMB**).

## Example scenarios
- Central **archive**, **analytics** landing zone, or **static** content delivery (often with **CloudFront**).
- **Practice (Windows file server question):** Wrong when the stem insists on a **VPC file system** for **Windows** application servers.

## Links to related questions
- [Windows File Server, DataSync, and FSx](../questions/windows-file-server-datasync-fsx.md)
- [Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/cost-effective-media-processing-sqs-ec2-s3.md)
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
- [Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/replatform-docker-mysql-openjdk-ecs-rds.md)
