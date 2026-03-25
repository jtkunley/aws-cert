# Amazon Redshift

## What it is
- Columnar **data warehouse**; MPP SQL; Spectrum; ML; **Redshift Serverless** option.

## Personal notes / memory hooks
- “Analytics DB” in stem → Redshift family.
- **Practice (serverless Q):** **Redshift Serverless** in keyed answer; provisioned Redshift in distractor fails **serverless** keyword.

## When to use it
- BI; big aggregates; historical analytics; lake queries (Spectrum).

## When NOT to use it
- OLTP row lookups—**Aurora/DynamoDB**.

## Exam clues
- Warehouse, BI, Spectrum, Serverless workgroup.

## Common distractors
- Put **transactional** e-commerce DB here because “PostgreSQL” appeared.

## Architecture patterns
- ETL from S3/Kinesis/Firehose; Serverless workgroups; datasharing.

## Comparison with nearby services
- **Redshift** vs **Athena** (S3 SQL) vs **OpenSearch** vs **Aurora** (OLTP).

## Example scenarios
- PostgreSQL-on-EC2 analytics → **Redshift Serverless**.
- **Practice (serverless Q):** analytics role ≠ **Aurora PostgreSQL** consolidation option.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
