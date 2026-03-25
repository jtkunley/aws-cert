# Amazon ECS

## What it is
- AWS-native container orchestration: tasks, services, IAM/VPC/LB integration.

## Personal notes / memory hooks
- AWS API scheduler—not Kubernetes.
- **Practice (serverless Q):** ECS+Fargate+serverless data+EventBridge loses when stem names **other CSPs’ Kubernetes** → **EKS** wins.

## When to use it
- AWS-only microservices; team wants simpler path than EKS.

## When NOT to use it
- Stem: **multi-cloud**, same manifests on GKE/AKS → **EKS**.

## Exam clues
- Task definition, service, Fargate vs EC2 launch type, `awsvpc`.

## Common distractors
- ECS vs EKS confused.
- **Practice (serverless Q):** strong stack, wrong only on **K8s portability** wording.

## Architecture patterns
- Microservices + ALB; App Mesh; EventBridge/Lambda beside tasks.

## Comparison with nearby services
- **ECS:** AWS control plane.
- **EKS:** Kubernetes API; both support **Fargate**.

## Example scenarios
- Retail microservices on AWS only.
- **Practice (serverless Q):** ECS+Fargate+EventBridge valid—eliminated by **multi-cloud clusters** line.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
