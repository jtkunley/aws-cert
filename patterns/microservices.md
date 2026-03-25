# Microservices

## What it is
Decomposing an application into small, independently deployable services aligned to business capabilities, communicating over networks (often APIs, events, or messages).

## When to use it
Different scaling profiles per capability, team autonomy, need to modernize legacy monoliths gradually, polyglot stacks, fault isolation boundaries.

## When NOT to use it
Small teams/products where operational overhead exceeds benefit; strict latency inside a single transaction boundary; immature DevOps—monolith or modular monolith may win.

## Exam clues
“Break into services,” “independently scale,” “deploy separately,” “domain boundaries,” containers/Kubernetes/ECS.

## Common distractors
Microservices on **EC2 without** event integration or managed data paths—still “distributed monolith” if tightly coupled.

## Related AWS services
ECS, EKS, Fargate, Lambda, API Gateway, EventBridge, SNS/SQS.

## Comparison with nearby patterns
**Microservices** vs **SOA** (similar ideas, different era/tooling); vs **serverless functions** (smaller units than “service” sometimes).

## Example scenarios
- Checkout, inventory, shipping as separate deployable services behind a BFF or API layer.
- **Practice (serverless modernization Q):** domain split mirrors **online sales, inventory, order processing, shipping logistics**—microservices + **containers** is the modernization path in options.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Microservices + **containers** + **events** is a common exam triple.
