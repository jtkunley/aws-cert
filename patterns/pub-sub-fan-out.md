# Pub/sub fan-out

## What it is
- One publish to **topic**; N subscribers get copy—**SNS**.

## When to use it
- Alerts; email/SMS; parallel Lambda + SQS from same message.

## When NOT to use it
- Per-event routing across types—**EventBridge**.
- Per-key ordering—**SQS FIFO / Kinesis**.

## Exam clues
- Topic, fan-out, publish, subscription.

## Common distractors
- SNS when stem clearly needs **EventBridge** rules/SaaS.

## Related AWS services
- SNS, SQS, Lambda, KMS, mobile push.

## Comparison with nearby patterns
- **SNS:** broadcast.
- **EventBridge:** routed bus.

## Example scenarios
- Alarm → SNS → email + Lambda + queue.
- **Practice (serverless Q):** SNS + ASG + Aurora PG-only option = wrong stack.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- SNS = radio broadcast; EventBridge = sorted mail with rules.
