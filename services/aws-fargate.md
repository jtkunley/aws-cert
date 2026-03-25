# AWS Fargate

## What it is
Serverless compute for containers: run ECS or EKS pods without provisioning or managing EC2 instances for the worker layer.

## When to use it
Containerized workloads where you want **no EC2 patching/scaling** for workers, variable traffic, and simpler ops than self-managed node groups.

## When NOT to use it
Extreme cost optimization at steady high CPU/memory with predictable 24/7 load (dedicated EC2 nodes *can* be cheaper); very low latency custom kernel tuning; DaemonSet-style node agents that require host access (limitations vs EC2 nodes).

## Exam clues
“Serverless containers,” “no clusters to manage” (worker nodes), “Fargate,” with **ECS** or **EKS**.

## Common distractors
Calling Fargate “Lambda for containers” in a pedantic sense—it’s still long-running container tasks/pods, not the Lambda invocation model.

## Architecture patterns
ECS services on Fargate; EKS pods on Fargate profiles; often paired with ALB and private subnets.

## Comparison with nearby services
**Fargate** vs **EC2 launch type / managed node groups**: trade ops burden vs control and price; **Lambda** for short event-driven functions, not arbitrary long-lived containers.

## Example scenarios
Microservices modernization from EC2 without Kubernetes ops (ECS+Fargate) or with K8s portability (EKS+Fargate).

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Fargate = “containers without the node fleet.” Pairs with ECS *or* EKS.
