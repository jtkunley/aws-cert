# Schema conversion plus replication

## What it is
- This pattern separates migration into two managed stages: convert schema first, then replicate data changes.
- It supports cleaner cutovers in cross-engine migrations.

## When to use it
- Database engines differ and schema compatibility must be addressed before replication.
- Downtime reduction is important during migration.

## When NOT to use it
- Migration is homogeneous and schema conversion is unnecessary.

## Exam clues
- Option wording that explicitly includes **schema conversion** and **database migration service** together.

## Common distractors
- Using one tool for both conversion and replication when both roles are required.

## Related AWS services
- AWS Schema Conversion Tool, AWS Database Migration Service, Amazon RDS.

## Comparison with nearby patterns
- More complete than one-step dump/load for heterogeneous enterprise migrations.

## Example scenarios
- Converting SQL Server schema to MySQL and then replicating data into RDS.

## Links to related questions
- [4. SQL Server to MySQL managed migration](../questions/4-sql-server-to-mysql-managed-migration.md)

## Personal notes / memory hooks
- In exam stems, this pairing is often the “managed and correct” migration pathway.
