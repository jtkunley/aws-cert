# Microservices

## What it is
- You split an application into **small**, **independently deployable** services that align with **business capabilities**.
- Services talk over the **network** using **APIs**, **events**, or **messages** instead of sharing one **monolithic** deployment unit.

## When to use it
- Different parts of the system need **different scaling** profiles, teams want **autonomy**, or you are **modernizing** a **legacy monolith** in steps.
- You run **polyglot** stacks or want **fault** boundaries between capabilities.

## When NOT to use it
- The team and product are **small** enough that **operational overhead** outweighs benefit, or **latency** inside a **single transaction** is extremely tight.
- **DevOps** maturity is low—a **modular monolith** may be wiser.

## Exam clues
- Phrases like **break into services**, **independently scale**, **deploy separately**, **domain boundaries**, and **containers** with **Kubernetes** or **ECS**.

## Common distractors
- **Microservices on EC2** **without** **event** integration or **managed data** paths can still behave like a **distributed monolith** if everything is **tightly coupled**.

## Related AWS services
- **Amazon ECS**, **Amazon EKS**, **Fargate**, **Lambda**, **API Gateway**, **EventBridge**, **SNS**, **SQS**.

## Comparison with nearby patterns
- **Microservices** overlaps with older **service-oriented architecture** ideas but uses **modern** **container** and **serverless** tooling; **Lambda** can be **smaller** than a full **service** in some designs.

## Example scenarios
- **Checkout**, **inventory**, and **shipping** as **separate** deployable services behind a **backend-for-frontend** or **API** layer.
- **Practice (serverless modernization question):** The stem lists **online sales**, **inventory**, **order processing**, and **shipping**—that **domain split** pairs naturally with **microservices** and **containers** in the answer set.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- **Microservices** plus **containers** plus **events** is a common **exam triple**.
