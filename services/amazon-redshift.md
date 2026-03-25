# Amazon Redshift

## What it is
Cloud **data warehouse** for analytics: columnar storage, MPP SQL queries, integrates with the data lake (Spectrum), ML (Redshift ML), and serverless options (**Redshift Serverless**).

## Personal notes / memory hooks
“Analytics DB” in the stem → Redshift family. “Online orders row-by-row” → OLTP elsewhere.

## When to use it
Business intelligence, large historical analytics, aggregations across huge datasets, integrating warehouse queries with S3 data.

## When NOT to use it
Primary **OLTP** for web transactions—use **Aurora/RDS/DynamoDB**; low-latency single-row app lookups.

## Exam clues
“Analytics,” “data warehouse,” “BI,” “Redshift Spectrum,” “Serverless,” “PostgreSQL wire protocol” (compatibility note—still warehouse semantics).

## Common distractors
- Putting the **e-commerce transactional** database in Redshift because “PostgreSQL” was mentioned for analytics—keep OLTP on Aurora, analytics on Redshift.
- **Practice (serverless modernization Q):** **Redshift** without **Serverless** vs **Redshift Serverless**—stem requires **serverless**; prefer **Redshift Serverless** in keyed answer.

## Architecture patterns
- ETL/ELT from S3/Kinesis/Firehose into Redshift; separate workgroups (Serverless); datasharing.

## Comparison with nearby services
- **Redshift** vs **Athena** (ad-hoc S3 SQL) vs **OpenSearch** (search/logs) vs **Aurora** (OLTP).

## Example scenarios
- PostgreSQL-on-EC2 analytics migrated to **Redshift Serverless**; dashboards on sales/inventory history.
- **Practice (serverless modernization Q):** **PostgreSQL-on-EC2 for analytics** → **Redshift Serverless**, not **Aurora PostgreSQL** for warehouse workloads.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
