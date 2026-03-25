# Amazon SNS

## What it is
- **Pub/sub:** topic → many subscribers (SQS, Lambda, HTTP, email, mobile).

## Personal notes / memory hooks
- One message, many subscribers—not a rule-based bus.
- **Practice (serverless Q):** “route incoming data” to EC2+DBs + Aurora PG only → fails serverless + bus narrative.

## When to use it
- Fan-out alerts; push; email/SMS; SNS→SQS workers.

## When NOT to use it
- Content routing, schedules, SaaS sources—**EventBridge**.
- Ordered replay streams—**Kinesis/MSK**.

## Exam clues
- Topic, fan-out, publish, subscription.

## Common distractors
- SNS substituted for **EventBridge** when stem wants a **bus**.

## Architecture patterns
- Alarm → SNS → Lambda + email; topic → multiple SQS queues.

## Comparison with nearby services
- **SNS:** broadcast pub/sub.
- **EventBridge:** routed bus.
- **SQS:** point-to-point queue.

## Example scenarios
- Ops paging; config broadcast.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
