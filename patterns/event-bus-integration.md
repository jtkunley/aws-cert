# Event bus integration

## What it is
- A central **event bus** receives events, applies **rules** for **filtering** and **routing**, and delivers to **targets**.
- **Amazon EventBridge** is the classic **AWS** service for **application** and **enterprise** integration in this style.

## When to use it
- You have **many event types**, **cross-account** routing, **scheduled** automation, **SaaS** partner integrations, or **schema** evolution with a **registry**.

## When NOT to use it
- You only need a **simple** one-to-many **notification** with **no** rich routing—**SNS** may be enough.
- You need **ordered** stream processing at **shard** scale—**Kinesis** or **FIFO** queues may fit better.

## Exam clues
- **Event bus**, **rules**, **targets**, **schedule**, **decouple microservices**, and **custom events**.

## Common distractors
- Describing **SNS topics** as a full substitute for **content-based routing** and **partner event sources**.

## Related AWS services
- **EventBridge**, **Lambda**, **SQS**, **SNS**, **Step Functions**, **API destinations**.

## Comparison with nearby patterns
- An **event bus** (**EventBridge**) differs from **pub/sub** (**SNS**) and from a **queue** (**SQS**) in **coupling** and **consumption** models.

## Example scenarios
- An **InventoryUpdated** rule sends messages to **SQS** for workers and invokes **Lambda** for **cache** invalidation.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- When the stem says **streamline data flows** between many services, sketch **EventBridge** first.
- **Practice (serverless modernization question):** The exact phrase **streamline application data flows** points to **EventBridge** over **SNS** as a **router** or **Kinesis** alone.
