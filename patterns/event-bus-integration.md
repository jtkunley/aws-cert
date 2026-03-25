# Event bus integration

## What it is
- Central **bus** + **rules** route events to targets—**EventBridge** pattern.

## When to use it
- Many event types; cross-account; schedules; SaaS sources; schema registry.

## When NOT to use it
- Simple broadcast, no routing—**SNS**.

## Exam clues
- Event bus, rules, targets, schedule, custom events.

## Common distractors
- **SNS topic** as full bus with content routing.

## Related AWS services
- EventBridge, Lambda, SQS, SNS, Step Functions, API Destinations.

## Comparison with nearby patterns
- **Bus** vs **pub/sub** vs **queue**.

## Example scenarios
- InventoryUpdated → SQS + Lambda cache bust.
- **Practice (serverless Q):** stem phrase **“streamline application data flows”** → EventBridge.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- “Streamline flows” between many services → draw EventBridge first.
