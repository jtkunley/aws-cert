# Amazon SNS

## What it is
Managed **pub/sub** messaging: publishers send to a **topic**, subscribers (SQS, Lambda, HTTP, email, mobile) receive notifications.

## Personal notes / memory hooks
- SNS = “one message, many subscribers.” Not the same as a centralized event bus.

## When to use it
Fan-out notifications, decoupling with multiple consumers, mobile push, email/SMS alerts, integrating with SQS for worker pools.

## When NOT to use it
Complex event **routing/filtering** across many event types and schedules—**EventBridge** is usually better; ordered, replayable stream processing—**Kinesis** or **MSK**.

## Exam clues
- “Fan-out,” “topic,” “subscription,” “publish,” “notify many systems.”
- **Practice (serverless modernization Q):** wording like **route incoming data** to **EC2 + databases**—SNS as glue vs **EventBridge** for **event-driven** architecture wording.

## Common distractors
- Using SNS as a full **event bus** replacement when the stem wants rule-based routing, SaaS sources, or schedules—EventBridge fits better.
- **Practice (serverless modernization Q):** **SNS to route data to EC2 instances and databases** alongside **Aurora PostgreSQL**—does not meet **serverless** goal and blurs **event bus** vs **simple pub/sub**.

## Architecture patterns
- Alarm → SNS → Lambda + email; order events → SNS → multiple SQS queues for workers.

## Comparison with nearby services
- **SNS** vs **EventBridge** vs **SQS**: pub/sub topics vs event bus vs point-to-point queue.

## Example scenarios
- Ops alerts, broadcasting configuration changes to many services.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
