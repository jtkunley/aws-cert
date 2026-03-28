# AWS Elastic Beanstalk

## What it is
- **AWS Elastic Beanstalk** is a **platform as a service** that deploys and scales **web applications** and **services** you upload as **code** or **containers**.
- It provisions **EC2** (or other supported capacity) and **load balancing** under a managed **application** abstraction.

## Personal notes / memory hooks
- **Elastic Beanstalk** can host **Java** without forcing **DynamoDB**, but the **database** in the answer must still match the stem. **Aurora** answers **SQL**, not **MongoDB**.
- **Practice (Java MongoDB migration question):** **Beanstalk plus Aurora** is wrong for **MongoDB** continuity even if **Beanstalk** fits **Java**.

## When to use it
- Teams want **faster** deployment of **Java**, **.NET**, **PHP**, **Node.js**, **Python**, **Ruby**, or **Go** apps with less **raw infrastructure** wiring.

## When NOT to use it
- The exam answer is wrong because of the **paired database** or **high availability** gap, not because **Beanstalk** is never valid for **Java**.

## Exam clues
- **Elastic Beanstalk**, **deploy application**, **managed platform**, often with **EC2** underneath.

## Links to related questions
- [Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/java-mongodb-ec2-documentdb-multi-az.md)
