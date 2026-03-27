# Amazon RDS

## What it is
- **Amazon Relational Database Service (Amazon RDS)** is a managed relational database service that automates backups, patching, and high availability operations for supported engines.
- It reduces infrastructure management overhead compared with self-managed database servers.

## Personal notes / memory hooks
- Think of RDS as managed database operations with engine choice.
- **Practice (SQL Server to MySQL migration question):** RDS for MySQL is the target after schema conversion and managed replication.

## When to use it
- You need managed relational databases with lower operational burden.
- You are migrating from self-managed databases and want managed backups and maintenance.

## When NOT to use it
- You need full OS-level control for database hosts.
- You need a migration tool by itself; RDS is the destination, not the migration engine.

## Exam clues
- Phrases like **managed relational database**, **RDS for MySQL**, and **reduce operational overhead**.

## Common distractors
- Treating RDS provisioning as a complete migration plan without schema conversion and data-move tooling.

## Architecture patterns
- Provision **Amazon RDS for MySQL** as migration target.
- Use migration tools to move schema and data into RDS.

## Comparison with nearby services
- **RDS** is managed database hosting.
- **AWS DMS** migrates data into or between database engines.
- **AWS SCT** converts schemas for heterogeneous targets.

## Example scenarios
- Moving on-premises SQL Server workloads to managed MySQL databases in AWS.

## Links to related questions
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
