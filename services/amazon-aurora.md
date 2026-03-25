# Amazon Aurora

## What it is
AWS-designed relational database compatible with **MySQL** or **PostgreSQL**, with storage auto-scaling, fast failover replicas, and global database options.

## When to use it
Managed OLTP needing PostgreSQL/MySQL compatibility, high durability, read scaling with replicas, or global/low-latency read patterns (Global Database).

## When NOT to use it
Pure key-value or document at massive scale—**DynamoDB**; analytics warehouse—**Redshift**; simplest serverless SQL with unpredictable spikes—consider **Aurora Serverless** variants when the stem matches.

## Exam clues
“MySQL/PostgreSQL compatible,” “Aurora,” “replicas,” “Serverless v2,” “Global Database,” “backtrack.” When the stem demands **serverless** for OLTP, prefer **Aurora Serverless** naming over provisioned **Aurora** alone if both appear.

## Common distractors
Migrating analytics PostgreSQL to **Aurora** when the workload is **warehouse**-style—Redshift family fits analytics better.

## Architecture patterns
Aurora writer + read replicas; Aurora Serverless for variable OLTP; multi-AZ high availability.

## Comparison with nearby services
**Aurora** vs **RDS** (same engines but Aurora storage model); **Aurora Serverless** for auto-scaling capacity; **Redshift** for analytics.

## Example scenarios
E-commerce transactional DB (MySQL-compat), app replacing self-managed MySQL on EC2.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
OLTP + MySQL/Postgres → Aurora. Warehouse/analytics → Redshift, not Aurora.
