# Legacy EC2 data tier

## What it is
- **Self-managed DB** on **EC2** (MySQL, PostgreSQL, …): you own patching, HA, backup.

## When to use it
- Rare greenfield; exotic extensions; interim migration.

## When NOT to use it
- Stem asks managed/serverless—move to **Aurora/RDS/Redshift/DynamoDB**.

## Exam clues
- Database on EC2, self-managed, manual failover.

## Common distractors
- ASG “modernizes” the **data** layer—false.

## Related AWS services
- EC2, EBS, RDS, Aurora, DMS.

## Comparison with nearby patterns
- **EC2 DB** vs **RDS/Aurora** (managed engine) vs **Redshift** (warehouse).

## Example scenarios
- E-commerce MySQL + analytics PostgreSQL both on EC2 at start of stem.
- **Practice (serverless Q):** split targets **Aurora Serverless MySQL** + **Redshift Serverless**, not one Aurora PG for both.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Ugly EC2 DB opening → answers lift to **managed/serverless** tiers.
