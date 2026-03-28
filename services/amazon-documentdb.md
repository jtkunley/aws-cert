# Amazon DocumentDB

## What it is
- **Amazon DocumentDB (with MongoDB compatibility)** is a managed **document database** that implements a **MongoDB-compatible** API for many application drivers and tools.
- AWS operates **clustering**, **storage**, and **maintenance** so teams avoid self-managing MongoDB servers on **EC2**.

## Personal notes / memory hooks
- When the question says **MongoDB** on premises and **no application changes**, **DocumentDB** is usually the managed target, not **DynamoDB** or **Aurora**.
- **Multi-AZ** deployments matter when the stem requires **high availability** for the **database** tier.

## When to use it
- Migrating **MongoDB** workloads that should keep **document** and **MongoDB driver** compatibility.
- You need **managed operations** with **high availability** options across **Availability Zones**.

## When NOT to use it
- The application is built for **DynamoDB** APIs or **relational SQL** only.

## Exam clues
- **MongoDB**, **DocumentDB**, **MongoDB compatibility**, **multi-AZ** clusters.

## Common distractors
- Choosing **Amazon DynamoDB** or **Amazon Aurora** when the scenario locks you to **MongoDB** semantics.

## Architecture patterns
- **Application tier** on **EC2** (often with **Auto Scaling**) plus **DocumentDB** for the **document** data store.
- **Multi-AZ** **DocumentDB** for **database** resilience when the question stresses **continuous operation**.

## Comparison with nearby services
- **DocumentDB:** **MongoDB-compatible** managed **document** database.
- **DynamoDB:** **AWS-native** key-value and document model with different APIs and design patterns.
- **Aurora:** **Relational** **MySQL** or **PostgreSQL** compatibility, not **MongoDB**.

## Links to related questions
- [Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/java-mongodb-ec2-documentdb-multi-az.md)
