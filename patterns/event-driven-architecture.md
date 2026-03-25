# Event-driven architecture

## What it is
- Components react to **events**; producers decoupled from consumers.

## When to use it
- One event → many reactions; add consumers without editing producer.

## When NOT to use it
- Strict sync UX only; no fan-out need.

## Exam clues
- Event-driven, decouple, publish, choreography.

## Common distractors
- **SNS** only when stem needs **rules, schedules, SaaS**—**EventBridge**.

## Related AWS services
- EventBridge, SNS, SQS, Lambda, Step Functions, Kinesis, Pipes.

## Comparison with nearby patterns
- **Events** vs **batch cron ETL** vs **high-volume streams** (Kinesis).

## Example scenarios
- OrderCreated → payment + inventory + notify async.
- **Practice (serverless Q):** **EventBridge** over SNS/Kinesis-only distractors for “streamline flows.”

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Event-driven on AWS → **EventBridge** unless pure dumb fan-out (SNS).
