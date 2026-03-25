# Amazon EventBridge

## What it is
Serverless **event bus**: ingest events from AWS services, custom applications, SaaS partners, and route/filter/transform to targets (Lambda, SQS, ECS, API destinations, etc.).

## When to use it
**Event-driven** architectures, decoupled microservices, scheduled rules (cron), SaaS integration, cross-account event sharing, schema registry workflows.

## When NOT to use it
Simple fan-out to many subscribers where **SNS** is enough and you don’t need content-based filtering/routing; ultra-high-throughput ordered streams—consider **Kinesis**.

## Exam clues
“Event-driven,” “event bus,” “rules,” “targets,” “schedule,” “decouple producers and consumers,” “SaaS integration.”

## Common distractors
**EventBridge vs SNS**: EventBridge = bus + rules + schedules + partner events; SNS = topic pub/sub, often simpler fan-out.

## Architecture patterns
Domain events between microservices, audit pipelines, automation on CloudTrail/API calls, cross-service orchestration.

## Comparison with nearby services
**EventBridge** vs **SNS** vs **SQS**: bus/routing vs pub/sub vs queue; **Kinesis** for stream processing at scale.

## Example scenarios
Order placed → EventBridge rule → multiple targets (inventory Lambda, analytics pipe, notification).

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
“Streamline application data flows” + decoupling → **EventBridge** is a flagship answer.
