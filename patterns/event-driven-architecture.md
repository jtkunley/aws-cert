# Event-driven architecture

## What it is
Components react to **events** (state changes, signals, schedules) instead of synchronous chains only; producers don’t need to know all consumers; coupling is reduced.

## When to use it
Multiple downstream reactions to one business event, async workflows, extensibility (add consumers without changing producer), decoupled microservices.

## When NOT to use it
Simple request/response with strict synchronous UX and no fan-out; debugging complexity unacceptable without strong observability.

## Exam clues
“Event-driven,” “decouple,” “publish event,” “react to changes,” “orchestration vs choreography.”

## Common distractors
Using **SNS** alone when the stem implies **routing rules**, schedules, or SaaS sources—**EventBridge** is often the better fit.

## Related AWS services
EventBridge, SNS, SQS, Lambda, Step Functions, Kinesis (stream of events), EventBridge Pipes.

## Comparison with nearby patterns
**Event-driven** vs **batch ETL** on a clock; vs **streaming** (continuous high-volume) where Kinesis leads.

## Example scenarios
`OrderCreated` event triggers payment, inventory, and analytics updates independently.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Event-driven + AWS exam → **EventBridge** is the default “bus” answer unless pure fan-out (SNS).
