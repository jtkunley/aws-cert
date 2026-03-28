# Amazon DynamoDB

## What it is
- **Amazon DynamoDB** is a fully managed **NoSQL key-value and document** database built for single-digit millisecond access at almost any scale.
- It uses a different data modeling approach than **relational** engines such as **MySQL**.

## Personal notes / memory hooks
- Moving **MySQL** to **DynamoDB** is usually a **re-architect** decision, not a simple license or hosting swap.
- **Practice (Docker migration question):** Pairing **AWS SCT** toward **DynamoDB** signals a **heterogeneous** data tier change that conflicts with **no major application changes** when the app is built around **MySQL**.

## When to use it
- You need **NoSQL** access patterns, predictable performance at scale, and fully managed operations without database servers.

## When NOT to use it
- The scenario requires **SQL**, **joins**, and **MySQL compatibility** without redesign.

## Exam clues
- **DynamoDB** appears with **serverless** or **massive scale** NoSQL requirements, not as a silent replacement for **MySQL** when the stem forbids major change.

## Links to related questions
- [Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/replatform-docker-mysql-openjdk-ecs-rds.md)
