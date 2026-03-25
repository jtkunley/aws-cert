# Amazon Aurora

## What it is
- MySQL- or PostgreSQL-compatible relational DB; AWS storage layer; replicas; Global Database.

## Personal notes / memory hooks
- OLTP here; warehouse → **Redshift**, not Aurora.
- **Practice (serverless Q):** one **Aurora PostgreSQL** for OLTP+analytics → wrong split.
- **Practice (serverless Q):** stem says **serverless** → **Aurora Serverless** beats provisioned Aurora in keyed answer.

## When to use it
- Managed OLTP; MySQL/Postgres apps; read replicas; Global DB reads.

## When NOT to use it
- Massive key-value—**DynamoDB**.
- Analytics warehouse—**Redshift**.
- Stem says serverless OLTP—prefer **Aurora Serverless** SKU.

## Exam clues
- Aurora, MySQL/Postgres compat, Serverless v2, Global DB, backtrack.

## Common distractors
- Analytics PostgreSQL → **Aurora** instead of **Redshift**.

## Architecture patterns
- Writer + replicas; Aurora Serverless variable OLTP; multi-AZ.

## Comparison with nearby services
- **Aurora vs RDS:** storage model.
- **Aurora Serverless:** auto capacity.
- **Redshift:** analytics only.

## Example scenarios
- E-commerce OLTP MySQL-compat off EC2 MySQL.
- **Practice (serverless Q):** MySQL-on-EC2 → **Aurora Serverless MySQL**; analytics PG-on-EC2 → **Redshift Serverless**.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
