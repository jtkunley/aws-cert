# AWS Schema Conversion Tool

## What it is
- **AWS Schema Conversion Tool (AWS SCT)** converts database schema objects and related code from a source engine to a target engine format.
- It is commonly paired with AWS DMS in heterogeneous database migrations.

## Personal notes / memory hooks
- SCT handles schema and code conversion; DMS handles data movement.
- **Practice (SQL Server to MySQL migration question):** SCT is the key clue for SQL Server-to-MySQL engine conversion.
- **Practice (Docker migration question):** SCT paired with **Amazon DynamoDB** in an option is a strong signal of a **major** data-tier change, not a minor **MySQL** move.

## When to use it
- Source and target engines are different and schema conversion is required.
- You need an assessment and conversion workflow before data replication.

## When NOT to use it
- Source and target engines are homogeneous and schema conversion is minimal.
- You need only data copy without cross-engine schema transformation.

## Exam clues
- Phrases like **convert schema**, **heterogeneous migration**, and **SQL Server to MySQL**.

## Common distractors
- Skipping SCT in cross-engine migrations and relying on load tools alone.
- Treating ETL services as complete schema-conversion replacements.

## Architecture patterns
- Run SCT assessment and conversion for target engine compatibility.
- Apply converted schema to target database before DMS replication.

## Comparison with nearby services
- **AWS SCT** converts schema and code.
- **AWS DMS** migrates data and ongoing changes.

## Example scenarios
- Preparing SQL Server schemas for Amazon RDS for MySQL target databases.

## Links to related questions
- [4. SQL Server to MySQL managed migration](../questions/4-sql-server-to-mysql-managed-migration.md)
- [5. Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/5-replatform-docker-mysql-openjdk-ecs-rds.md)
