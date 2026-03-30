# AWS App2Container

## What it is
- **AWS App2Container (A2C)** is a command-line tool that helps **containerize** existing **Java** and **.NET** applications and produce artifacts you can deploy to **Amazon ECS** or **Amazon EKS**.

## Personal notes / memory hooks
- **App2Container** implies a **containerization** and deployment path change, which often conflicts with stems that say the **application cannot be modified** during migration.
- **Practice (Java MongoDB migration question):** Pairing **App2Container**, **EKS**, and **DynamoDB** breaks both the **no-change** spirit and the **MongoDB** data tier.

## When to use it
- You are **modernizing** toward **containers** and accept **migration tooling** work beyond a strict lift-and-shift.

## When NOT to use it
- The scenario forbids **meaningful application or packaging changes** and expects **EC2**-style hosting similar to today.

## Exam clues
- Mentions of **App2Container** alongside **EKS** or **ECS** in **replatform** answers.

## Links to related questions
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
