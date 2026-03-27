# SQL Server to MySQL managed migration

## Original question
An organization operates web and mobile platforms for online sales, inventory management, order processing, and shipping logistics. The platforms are running on Amazon EC2 instances across multiple regions. The organization's databases include a MySQL database for the e-commerce site and a PostgreSQL database for analytics, both managed on EC2 instances.

A solutions architect requires a solution to transition the organization's architecture to an event-driven, serverless architecture to improve efficiency and data processing speeds, enable real-time analytics, and streamline application data flows. The company also plans to launch a multi-cloud configuration that runs additional clusters on other cloud service providers to further improve the site's performance.

Which of the following options would most efficiently meet these requirements?

**Option A:** Utilize the native SQL Server backup utility to create a copy of the current database. Upload the created backup file to an Amazon S3 bucket. Create a new Amazon RDS for MySQL instance. Use AWS Glue to load S3 data into the Amazon RDS MySQL table.

**Option B:** Create a backup copy of the on-premises SQL Server. Request an AWS Snowball Edge Storage Optimized device to copy and transfer the data to an Amazon S3 bucket. Create an Amazon RDS for MySQL instance. Use the SQL Server BULK INSERT feature to load data from the S3 bucket to the RDS instance.

**Option C:** Install the AWS Schema Conversion Tool on the on-premises data center to convert the database schema from Microsoft SQL Server to MySQL. Create an Amazon RDS for MySQL instance. Migrate the on-premises database to the RDS instance using AWS Database Migration Service (DMS).

**Option D:** Establish a secure VPN connection from the on-premises network to Amazon VPC. Create a new Amazon RDS for MySQL instance. Use the AWS DataSync service to replicate the SQL server database to AWS. Promote the RDS instance as a master database once replication is completed.

## Correct answer
- **Option C** is the recommended solution.
- It uses **AWS Schema Conversion Tool** for heterogeneous schema conversion and **AWS Database Migration Service (AWS DMS)** for ongoing data migration into **Amazon RDS for MySQL** with managed services.

## Why it is correct
- The requirement explicitly asks for a **heterogeneous** migration from **Microsoft SQL Server** to **MySQL**.
- **AWS Schema Conversion Tool** is designed to convert source schemas and code objects to target engine formats.
- **AWS DMS** handles data movement with minimal downtime patterns and is the standard managed migration service for this scenario.
- The option keeps operations on managed AWS services, which aligns with the management goal in the stem.

## Why the other options are wrong
- **Option A:** Backup to **Amazon S3** and loading with **AWS Glue** is not the standard path for SQL Server-to-MySQL heterogeneous migration. It also misses dedicated schema-conversion tooling and can add manual transformation overhead.
- **Option B:** **AWS Snowball Edge** is for offline transfer and bulk seeding. It is a poor fit when the question does not require offline transport and still does not provide the right schema conversion plus managed replication path.
- **Option D:** **AWS DataSync** replicates file/object data stores, not relational database engine migration semantics between SQL Server and MySQL.

## Trap type
- **Wrong migration primitive:** Using file-transfer services for relational engine migration.
- **Offline transfer overuse:** Choosing Snowball when managed online migration tools are the intended fit.
- **Partial workflow:** Loading data without robust heterogeneous schema conversion.

## Services involved
- [Amazon EC2](../services/amazon-ec2.md)
- [Amazon RDS](../services/amazon-rds.md)
- [Amazon S3](../services/amazon-s3.md)
- [Amazon VPC](../services/amazon-vpc.md)
- [AWS Glue](../services/aws-glue.md)
- [AWS Snowball Edge](../services/aws-snowball-edge.md)
- [AWS Schema Conversion Tool](../services/aws-schema-conversion-tool.md)
- [AWS Database Migration Service](../services/aws-database-migration-service.md)
- [AWS DataSync](../services/aws-datasync.md)

## Pattern tags
- [Heterogeneous database migration](../patterns/heterogeneous-database-migration.md)
- [Schema conversion plus replication](../patterns/schema-conversion-plus-replication.md)
- [Managed database modernization](../patterns/managed-database-modernization.md)
- [Legacy EC2 data tier](../patterns/legacy-ec2-data-tier.md)

## Question Seed

- Scenario summary: A mission-critical on-premises Microsoft SQL Server workload must move to AWS with lower operations, and the target platform requires a heterogeneous migration into MySQL using managed AWS services.
- Primary driver: The migration must correctly handle SQL Server-to-MySQL heterogeneity with managed tools, not file-copy workflows.
- Decision focus: This question tests whether you choose schema conversion plus managed database replication for heterogeneous migration, instead of backup or file-transfer pipelines.
- Correct answer pattern: Convert source schema objects to the target engine format, provision managed MySQL on Amazon RDS, and run managed ongoing replication from source database to target database.

- Key services:
  - AWS Schema Conversion Tool
  - AWS Database Migration Service
  - Amazon RDS for MySQL

- Common distractor services:
  - AWS Glue
  - AWS Snowball Edge
  - AWS DataSync
  - Amazon S3

- Key signals:
  - heterogeneous migration
  - SQL Server to MySQL
  - managed services preferred
  - mission-critical database
  - on-premises to AWS

- Constraints:
  - The solution must support cross-engine schema compatibility from SQL Server to MySQL.
  - The migration path should rely on managed AWS services to reduce operational overhead.
  - The data movement mechanism must match relational database migration semantics, not file replication.

- Common traps:
  - Using S3 plus Glue as the primary migration workflow for SQL Server-to-MySQL conversion.
  - Choosing Snowball Edge for a migration that does not require offline transfer as the primary approach.
  - Using DataSync to replicate relational databases across different engines.

- Why traps are wrong:
  - S3 plus Glue workflow → violates the heterogeneous schema-conversion constraint for SQL Server-to-MySQL migration.
  - Snowball Edge primary path → violates the managed online migration-fit constraint when SCT plus DMS directly solve the engine migration problem.
  - DataSync for SQL Server replication → violates the relational migration-semantics constraint because DataSync is for file and object data movement.

- Pattern tags:
  - #heterogeneous-database-migration
  - #schema-conversion-and-replication
  - #managed-migration-services
  - #sql-server-to-mysql
