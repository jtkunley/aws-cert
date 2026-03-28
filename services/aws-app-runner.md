# AWS App Runner

## What it is
- **AWS App Runner** is a fully managed service that runs **containerized web applications** and APIs from a container image or source repository with minimal infrastructure configuration.
- AWS handles scaling, load balancing, and patching of the runtime around your container.

## Personal notes / memory hooks
- **App Runner** is a plausible **replatform** target for **stateless web** containers when the stem stresses **low operations**.
- **Practice (Docker migration question):** If the same option also forces **MySQL to DynamoDB** with **AWS SCT**, treat that as a **major data-tier rewrite**, not a minor replatform.

## When to use it
- You want a **simple** path from a **web container image** to a managed HTTPS endpoint without managing clusters or instances.

## When NOT to use it
- The workload needs **Kubernetes**, **custom networking**, or **fine-grained ECS/EKS** control described in the scenario.

## Exam clues
- Mentions of **App Runner**, **operational overhead**, and **containerized web apps** in the same option.

## Common distractors
- Choosing **App Runner** when **ECS** is paired with **full environment** needs, or when another part of the same answer breaks constraints (for example **relational to NoSQL**).

## Links to related questions
- [Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/replatform-docker-mysql-openjdk-ecs-rds.md)
