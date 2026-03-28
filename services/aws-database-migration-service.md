# AWS Database Migration Service

## What it is
- **AWS Database Migration Service (AWS DMS)** is a managed service for migrating data between database engines and database endpoints.
- It supports minimal-downtime migration workflows by moving ongoing changes after initial load.

## Personal notes / memory hooks
- DMS moves data; it does not replace schema-conversion requirements for cross-engine migrations.
- **Practice (SQL Server to MySQL migration question):** DMS is the standard managed replication engine after schema conversion with AWS SCT.
- **Practice (Docker migration question):** **AWS DMS** into **Amazon RDS** supports **MySQL** continuity for on-premises **MySQL** migration.

## When to use it
- You are migrating relational databases to AWS with low-downtime goals.
- You need ongoing replication from source to target during cutover windows.

## When NOT to use it
- You need file transfer only; use file/object transfer services instead.
- You expect DMS to convert complex schemas automatically in heterogeneous migrations without SCT.

## Exam clues
- Phrases like **heterogeneous migration**, **minimal downtime**, **ongoing replication**, and **DMS**.

## Common distractors
- Using DMS alone for heterogeneous schema conversion.
- Replacing DMS with DataSync or Glue for core relational migration workflows.

## Architecture patterns
- AWS SCT converts schema from source engine to target engine.
- AWS DMS performs initial load plus ongoing change replication.

## Comparison with nearby services
- **AWS DMS** handles database data migration and change replication.
- **AWS SCT** handles schema conversion for heterogeneous engines.
- **AWS DataSync** handles file/object transfer, not relational migration semantics.

## Example scenarios
- Migrating on-premises Microsoft SQL Server to Amazon RDS for MySQL.

## Links to related questions
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
- [Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/replatform-docker-mysql-openjdk-ecs-rds.md)
