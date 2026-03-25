# Amazon EventBridge

## What it is
- Serverless **event bus**: rules, filters, targets (Lambda, SQS, ECS, API destinations, SaaS).

## Personal notes / memory hooks
- “Streamline application data flows” in stem → EventBridge before SNS/Kinesis-only stories.
- **Practice (serverless Q):** EventBridge + microservices + serverless data = keyed integration choice.

## When to use it
- Event-driven microservices; schedules; SaaS partners; cross-account rules.

## When NOT to use it
- Dumb fan-out, no routing—**SNS** enough.
- Shard-scale ordered streams—**Kinesis/MSK**.

## Exam clues
- Event bus, rules, targets, schedule, decouple producers/consumers.

## Common distractors
- SNS as full **bus** with routing—weak vs EventBridge.
- **Practice (serverless Q):** SNS “route to EC2 and DBs” ≠ event-driven architecture ask.

## Architecture patterns
- Domain events; CloudTrail-driven automation; multi-target rules.

## Comparison with nearby services
- **EventBridge:** bus + rules.
- **SNS:** topic pub/sub.
- **SQS:** queue.
- **Kinesis:** stream processing scale.

## Example scenarios
- OrderPlaced → rule → inventory Lambda + SQS + analytics pipe.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
