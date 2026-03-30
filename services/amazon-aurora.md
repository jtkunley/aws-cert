# Amazon Aurora

## What it is
- **Amazon Aurora** is a relational database engine built by AWS that is compatible with **MySQL** or **PostgreSQL**.
- It uses a **distributed storage** layer that scales automatically, supports **fast failover** read replicas, and offers options such as **Aurora Global Database** for cross-Region reads.

## Personal notes / memory hooks
- Use **Aurora** for **online transaction processing (OLTP)** when you want **MySQL or PostgreSQL** compatibility.
- **Practice (Java MongoDB migration question):** **Aurora** does not satisfy a **MongoDB** datastore requirement; pairing **Elastic Beanstalk** with **Aurora** still fails the **document** database constraint.
- Use **Amazon Redshift** for **analytics warehouses**, not Aurora, when the workload is **reporting and aggregates** at warehouse scale.
- **Practice (serverless modernization question):** Putting **both** migrated **e-commerce MySQL** and **analytics PostgreSQL** into **one Aurora PostgreSQL** cluster usually **mixes roles**. The exam often wants **Aurora Serverless MySQL** for **OLTP** and **Redshift Serverless** for the **warehouse**.

## When to use it
- You need a **managed** relational database with **MySQL or PostgreSQL** compatibility, **high durability**, and **read scaling** through **replicas**.
- You want **global** read patterns with **Aurora Global Database** (where offered).

## When NOT to use it
- You need **massive key-value or document** scale-out—**Amazon DynamoDB** may fit better.
- The workload is **analytics warehouse** style—**Redshift** is usually the right family.
- The stem asks for **serverless SQL** with **spiky** OLTP—compare **Aurora Serverless** to **provisioned Aurora** when both appear.

## Exam clues
- **MySQL-compatible**, **PostgreSQL-compatible**, **Aurora**, **replicas**, **Aurora Serverless v2**, **Global Database**, **backtrack** (where applicable).

## Common distractors
- Moving **analytics PostgreSQL on EC2** to **Aurora** when the exam expects a **data warehouse** answer (**Redshift**).
- **Practice (serverless modernization question):** When the stem says **serverless**, prefer answers that name **Aurora Serverless** over **provisioned Aurora** if both show up.

## Architecture patterns
- One **Aurora writer** plus **Aurora replicas** for read traffic.
- **Aurora Serverless** for **variable OLTP** load.
- **Multi-AZ** high availability within a Region.

## Comparison with nearby services
- **Aurora versus RDS:** similar **MySQL/PostgreSQL** engines on the surface; **Aurora** has a different **storage** architecture.
- **Aurora Serverless:** **capacity** adjusts automatically within the serverless model.
- **Redshift:** **columnar warehouse** for analytics, not primary **OLTP**.

## Example scenarios
- **E-commerce** transactional data that used to live in **self-managed MySQL on EC2**.
- **Practice (serverless modernization question):** Starting state **MySQL on EC2** plus **PostgreSQL on EC2 for analytics** often maps to **Aurora Serverless MySQL** plus **Redshift Serverless**, **not** a single **Aurora PostgreSQL** for everything.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
