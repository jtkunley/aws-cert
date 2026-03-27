# Heterogeneous database migration

## What it is
- This pattern migrates between different database engines, such as Microsoft SQL Server to MySQL.
- It usually requires both schema conversion and managed data replication.

## When to use it
- Source and target engines are different.
- The migration must preserve structure and data integrity while reducing downtime.

## When NOT to use it
- Source and target engines are the same and native homogeneous replication is enough.

## Exam clues
- Keywords like **heterogeneous migration**, **SQL Server to MySQL**, and **managed services preferred**.

## Common distractors
- Treating file transfer or ETL loading as a complete replacement for engine-aware migration tooling.

## Related AWS services
- AWS Schema Conversion Tool, AWS Database Migration Service, Amazon RDS.

## Comparison with nearby patterns
- Heterogeneous migration adds schema-conversion requirements beyond standard homogeneous database copy.

## Example scenarios
- Moving on-premises SQL Server workloads into Amazon RDS for MySQL.

## Links to related questions
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)

## Personal notes / memory hooks
- Think “SCT then DMS” when engines differ.
