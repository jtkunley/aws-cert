# Lift-and-shift MongoDB with DocumentDB compatibility

## What it is
- This pattern moves a **MongoDB**-oriented workload to AWS while keeping **document** semantics and **MongoDB wire-protocol** compatibility where the exam expects it.
- **Amazon DocumentDB (with MongoDB compatibility)** is the managed AWS service that targets existing **MongoDB** applications without forcing a move to a different NoSQL model.

## Personal notes / memory hooks
- If the stem names **MongoDB** and forbids **application changes**, answers that swap in **Amazon DynamoDB** or **Amazon Aurora** usually break the **data API** story.
- Pair **Java on Amazon EC2** in an **Auto Scaling group** across **Availability Zones** with **multi-AZ** **DocumentDB** when **high availability** covers **both** tiers.

## When to use it
- **Lift-and-shift** or **minimal-change** migration from **MongoDB** on premises.
- Requirements mention **similar architecture**, **no code changes**, and **HA** for app and database.

## When NOT to use it
- The scenario explicitly wants **DynamoDB** access patterns or **relational SQL** only.

## Exam clues
- **MongoDB**, **cannot be modified**, **similar architecture**, **DocumentDB**, **multi-AZ**.

## Links to related questions
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
