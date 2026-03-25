# Pub/sub fan-out

## What it is
- One **publisher** sends a message to a **topic**, and **many subscribers** each receive a **copy** of that message.
- **Amazon SNS** is the classic **AWS** service for this **fan-out** pattern, often combined with **Amazon SQS** for **buffering** and **worker** pools.

## When to use it
- **Alerts**, **notifications**, **broadcasting** the same message to **Lambda**, **email**, and **multiple queues**, or **simple decoupled** fan-out.

## When NOT to use it
- You need **per-event routing**, **transformation**, and **schedules** across **many event types**—prefer **EventBridge**.
- You need **strict ordering** per key—**SQS FIFO** or **Kinesis** may fit better.

## Exam clues
- **Fan-out**, **topic**, **multiple subscribers**, **notify**, and **publish**.

## Common distractors
- Choosing **SNS** when the scenario is clearly an **event bus** with **rules** and **SaaS** sources.
- **Practice (serverless modernization question):** **SNS** plus **EC2 Auto Scaling** plus a **single Aurora PostgreSQL** path is the wrong **tool** and the wrong **serverless** posture for that stem.

## Related AWS services
- **SNS**, **SQS**, **Lambda**, **KMS** for **encryption**, and **mobile** or **email** integrations.

## Comparison with nearby patterns
- **Pub/sub** is a **broadcast** model; **EventBridge** adds **richer routing** and **integration** features.

## Example scenarios
- A **CloudWatch** alarm publishes to **SNS**, which fans out to **email**, **Lambda**, and an **SQS** ticket queue.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Think of **SNS** as a **radio broadcast** and **EventBridge** as a **mail-sorting facility** with **rules**.
