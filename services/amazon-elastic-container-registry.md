# Amazon Elastic Container Registry

## What it is
- **Amazon Elastic Container Registry (Amazon ECR)** is a managed **container image registry** that stores Docker and Open Container Initiative images for deployment to AWS container services.
- It integrates with **IAM**, **Amazon ECS**, **Amazon EKS**, and other AWS runtimes that pull images.

## Personal notes / memory hooks
- If the scenario says **build**, **test**, and **upload** container images, **ECR** is the standard AWS destination before running tasks on **ECS** or **EKS**.
- **Practice (Docker migration question):** Re-platform paths often pair **ECS** with **ECR** for OpenJDK-based images.

## When to use it
- You need private image storage with AWS-native pull permissions for **ECS**, **EKS**, or **Lambda** container images.

## When NOT to use it
- You only need public images from an external registry and have no requirement for a private AWS-managed registry in the answer.

## Exam clues
- Phrases like **upload container images**, **Elastic Container Registry**, **ECR**, and **Docker** together with **ECS**.

## Common distractors
- Using **Amazon S3** as if it were a substitute for a container registry workflow without a clear pull integration story in the option.

## Architecture patterns
- **CI/CD** builds an image, pushes to **ECR**, and **ECS** or **EKS** deploys from that registry.

## Links to related questions
- [Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/replatform-docker-mysql-openjdk-ecs-rds.md)
