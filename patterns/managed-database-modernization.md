# Managed database modernization

## What it is
- This pattern moves from self-managed database operations to managed AWS database services.
- The goal is lower operational overhead while improving reliability and scalability.

## When to use it
- Management asks to prioritize managed services.
- Existing workloads run on self-managed database hosts and operations are heavy.

## When NOT to use it
- Regulatory or technical constraints require host-level control over database servers.

## Exam clues
- Requirements like **use managed services whenever possible** and **reduce operational overhead**.

## Common distractors
- Rebuilding workflows around manual backup and load pipelines instead of managed migration tooling.

## Related AWS services
- Amazon RDS, AWS Database Migration Service, AWS Schema Conversion Tool.

## Comparison with nearby patterns
- Managed modernization emphasizes operational ownership shift, not only data movement mechanics.

## Example scenarios
- Migrating on-premises SQL Server workloads to Amazon RDS for MySQL with managed tools.
- Moving on-premises MySQL into Amazon RDS with AWS Database Migration Service while modernizing the app tier.

## Links to related questions
- [4. SQL Server to MySQL managed migration](../questions/4-sql-server-to-mysql-managed-migration.md)
- [5. Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/5-replatform-docker-mysql-openjdk-ecs-rds.md)

## Personal notes / memory hooks
- If the stem says “managed whenever possible,” favor RDS + migration services over manual pipelines.
