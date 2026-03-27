# AWS Snowball Edge

## What it is
- **AWS Snowball Edge** is a physical data transfer device for moving large data volumes into or out of AWS when network transfer is impractical.
- It is designed for offline or constrained-connectivity bulk migration cases.

## Personal notes / memory hooks
- Snowball Edge solves bulk transfer logistics, not heterogeneous database schema migration by itself.
- **Practice (SQL Server to MySQL migration question):** Snowball can be a distractor when online managed migration services are the intended solution.

## When to use it
- Data volumes are very large and network transfer would take too long.
- You need offline transfer due to bandwidth or connectivity constraints.

## When NOT to use it
- A managed online migration path with schema conversion and database replication is available and preferred.
- You need ongoing change replication during cutover.

## Exam clues
- Phrases like **offline transfer**, **petabyte-scale copy**, and **physical device shipment**.

## Common distractors
- Choosing Snowball as the primary answer when the core requirement is heterogeneous database migration semantics.

## Architecture patterns
- Export source data to Snowball Edge, ship device, import data into AWS landing zone.

## Comparison with nearby services
- **Snowball Edge** is offline bulk transfer.
- **AWS DMS** is online database migration and replication.
- **AWS DataSync** is online file/object transfer.

## Example scenarios
- Large one-time archive or dataset transfer where network links are insufficient.

## Links to related questions
- [SQL Server to MySQL managed migration](../questions/sql-server-to-mysql-managed-migration.md)
