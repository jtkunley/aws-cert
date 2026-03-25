# Event bus integration

## What it is
A central **event bus** receives events, applies **rules** (filtering, routing), and delivers to **targets**—the classic **EventBridge** pattern for enterprise and application integration.

## When to use it
Many event types, cross-account routing, scheduled automation, SaaS partner integrations, schema evolution with registry.

## When NOT to use it
Simple one-to-many notify pattern with no routing—**SNS** may be enough; ordered stream processing at shard scale—**Kinesis**.

## Exam clues
“Event bus,” “rules,” “targets,” “schedule,” “decouple microservices,” “custom events.”

## Common distractors
Describing **SNS topics** as a full substitute for content-based routing and partner event sources.

## Related AWS services
EventBridge, Lambda, SQS, SNS, Step Functions, API Destinations.

## Comparison with nearby patterns
**Event bus** (EventBridge) vs **pub/sub** (SNS) vs **queue** (SQS)—different coupling and consumption models.

## Example scenarios
`InventoryUpdated` rule sends to SQS for workers and invokes Lambda for cache invalidation.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- “Streamline data flows” between many services → draw EventBridge first.
- **Practice (serverless modernization Q):** exact stem phrase **“streamline application data flows”** → **EventBridge** over **SNS** “routing” or **Kinesis** alone.
