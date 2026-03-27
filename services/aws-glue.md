# AWS Glue

## What it is
- **AWS Glue** is a managed data integration service for extract, transform, and load (ETL) jobs and metadata cataloging.
- It is commonly used in analytics pipelines, data lakes, and batch transformations.

## Personal notes / memory hooks
- Glue is strongest in data engineering and ETL contexts, not as the primary relational migration engine.
- **Practice (SQL Server to MySQL migration question):** Glue with S3 can be a distractor when the problem is heterogeneous database migration.

## When to use it
- You need managed ETL processing and transformation workflows.
- You are preparing and loading datasets for analytics platforms.

## When NOT to use it
- You need engine-aware relational migration semantics with minimal-downtime replication.
- You need schema conversion from one database engine to another.

## Exam clues
- Phrases like **ETL**, **data catalog**, **crawler**, and **transform and load**.

## Common distractors
- Choosing Glue to replace SCT plus DMS in SQL Server-to-MySQL migration scenarios.

## Architecture patterns
- Read from S3, transform data, write to analytics or relational targets.

## Comparison with nearby services
- **AWS Glue** focuses on transformation and data integration.
- **AWS DMS** focuses on database migration and ongoing replication.
- **AWS SCT** focuses on cross-engine schema conversion.

## Example scenarios
- Batch transforming semi-structured data for reporting pipelines.

## Links to related questions
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
