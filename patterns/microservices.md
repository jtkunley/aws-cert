# Microservices

## What it is
- Small deployable services by capability; network calls (API, events).

## When to use it
- Different scale per domain; team boundaries; isolate failures.

## When NOT to use it
- Tiny team; tight sync latency inside one transaction; no ops maturity.

## Exam clues
- Break into services, deploy separately, ECS/EKS, domain language.

## Common distractors
- Microservices on EC2 **without** events/queues—still a distributed monolith.

## Related AWS services
- ECS, EKS, Fargate, Lambda, API Gateway, EventBridge, SNS/SQS.

## Comparison with nearby patterns
- **Microservices** vs **SOA** (era/tooling) vs **Lambda-only** (finer grain).

## Example scenarios
- Checkout, inventory, shipping as separate services.
- **Practice (serverless Q):** sales, inventory, orders, shipping → container microservices in answers.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Microservices + **containers** + **events** = common exam triple.
