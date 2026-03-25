# Legacy EC2 data tier

## What it is
Anti-pattern or transitional state: **self-managed databases** (MySQL, PostgreSQL, etc.) running on **EC2**—you patch OS, backups, failover, and scaling yourself.

## When to use it
Rare in greenfield; legacy compliance, exotic extensions, or migration interim states.

## When NOT to use it
Exam scenarios asking for **managed**, **serverless**, or **higher availability** with less ops—move toward **Aurora/RDS**, **DynamoDB**, **Redshift**, etc.

## Exam clues
“Database on EC2,” “self-managed,” “patching,” “manual failover,” “legacy.”

## Common distractors
Assuming EC2 + ASG “modernizes” the data plane—it doesn’t replace managed DB services.

## Related AWS services
EC2, EBS, RDS, Aurora, DMS for migration, backup strategies.

## Comparison with nearby patterns
**Self-managed on EC2** vs **RDS/Aurora** (AWS manages engine ops); vs **data warehouse** (Redshift) for analytics workloads.

## Example scenarios
Starting point in exam stems: e-commerce MySQL and analytics PostgreSQL both on EC2 before migration.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Stem starts ugly (EC2 DBs) → answers should **lift data to managed/serverless** tiers.
