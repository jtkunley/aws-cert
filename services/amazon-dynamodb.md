# Amazon DynamoDB

## What it is
- **Amazon DynamoDB** is a fully managed **NoSQL key-value and document** database built for single-digit millisecond access at almost any scale.
- It uses a different data modeling approach than **relational** engines such as **MySQL**.

## Personal notes / memory hooks
- Moving **MySQL** to **DynamoDB** is usually a **re-architect** decision, not a simple license or hosting swap.
- **Practice (Docker migration question):** Pairing **AWS SCT** toward **DynamoDB** signals a **heterogeneous** data tier change that conflicts with **no major application changes** when the app is built around **MySQL**.
- **Practice (Java MongoDB migration question):** **DynamoDB** is not a drop-in **MongoDB** engine; stems that name **MongoDB** usually point to **Amazon DocumentDB** when a managed AWS target is required.

## When to use it
- You need **NoSQL** access patterns, predictable performance at scale, and fully managed operations without database servers.

## When NOT to use it
- The scenario requires **SQL**, **joins**, and **MySQL compatibility** without redesign.

## Exam clues
- **DynamoDB** appears with **serverless** or **massive scale** NoSQL requirements, not as a silent replacement for **MySQL** when the stem forbids major change.

## Links to related questions
- [5. Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/5-replatform-docker-mysql-openjdk-ecs-rds.md)
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
