# Pub/sub fan-out

## What it is
One publisher sends a message to a **topic**; many **subscribers** receive copies—classic **SNS** pattern (often combined with **SQS** for buffering).

## When to use it
Alerts, notifications, broadcasting the same message to Lambda + email + multiple queues, simple decoupled fan-out.

## When NOT to use it
Need per-event routing, transformation, and schedules across hundreds of event types—prefer **EventBridge**; strict ordering per key—**SQS FIFO** or **Kinesis**.

## Exam clues
“Fan-out,” “topic,” “multiple subscribers,” “notify,” “publish.”

## Common distractors
Choosing SNS when the scenario is clearly an **event bus** with rules and SaaS sources.

## Related AWS services
SNS, SQS, Lambda, KMS for encryption, mobile push/email integrations.

## Comparison with nearby patterns
**Pub/sub** vs **event bus**: SNS is simpler broadcast; EventBridge is richer routing/integration.

## Example scenarios
CloudWatch Alarm → SNS → Ops email + Lambda pager + SQS ticket queue.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
SNS = “radio broadcast.” EventBridge = “mail sorting facility with rules.”
