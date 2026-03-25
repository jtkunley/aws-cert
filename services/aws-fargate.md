# AWS Fargate

## What it is
- Serverless **container** run: no EC2 worker patching for ECS or EKS pods.

## Personal notes / memory hooks
- Containers without a node fleet.
- **Practice (serverless Q):** serverless = Fargate **and** Aurora Serverless + Redshift Serverless in keyed answer.

## When to use it
- No node ops; spiky or variable container load.

## When NOT to use it
- Steady maxed CPU 24/7 on bare metal—dedicated nodes can cost less.
- DaemonSets / host-level agents—limited vs EC2 nodes.

## Exam clues
- “Serverless containers,” Fargate + **ECS or EKS**.

## Common distractors
- Fargate ≠ Lambda (long-running tasks OK).

## Architecture patterns
- ECS service on Fargate; EKS Fargate profile; ALB + private subnets.

## Comparison with nearby services
- **Fargate vs EC2 nodes:** ops vs control vs price.
- **Lambda:** not a general container runtime.

## Example scenarios
- EC2 → containers without K8s ops (ECS+Fargate).
- K8s portability (EKS+Fargate).

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
