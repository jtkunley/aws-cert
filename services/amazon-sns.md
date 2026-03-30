# Amazon SNS

## What it is
- **Amazon Simple Notification Service (SNS)** is a **managed pub/sub** messaging service.
- Publishers send messages to an **SNS topic**. **Subscribers** (for example **Amazon SQS** queues, **Lambda** functions, **HTTP** endpoints, **email**, or **SMS**) each receive their own copy of the message.

## Personal notes / memory hooks
- One image that works is **“one announcement, many listeners.”** That is different from a full **event bus** with rich **routing rules**.
- **Practice (serverless modernization question):** When an option uses **SNS** mainly to **route traffic to EC2 instances and databases**, compare it to **EventBridge** for **event-driven** wording and check whether the overall design is still **serverless**.

## When to use it
- **Fan-out notifications**: operations alerts, **email** and **SMS**, **mobile push**.
- You want several systems to **react in parallel** to the same message, often with **SQS** in front of workers for buffering.

## When NOT to use it
- You need **complex routing**, **content filtering**, **scheduled rules**, or many **SaaS** sources. **EventBridge** is usually the better match.
- You need **strict ordering** or **replay** at streaming scale—consider **SQS FIFO**, **Kinesis**, or **MSK**.

## Exam clues
- **Fan-out**, **topic**, **subscription**, **publish**, **notify many systems**.

## Common distractors
- Treating **SNS** as a drop-in replacement for **EventBridge** when the scenario clearly needs an **event bus** with **rules** and **schedules**.
- **Practice (serverless modernization question):** **SNS** plus **EC2 Auto Scaling** plus a single **Aurora PostgreSQL** answer often **fails** the **serverless** requirement and the **warehouse versus OLTP** split.

## Architecture patterns
- A **CloudWatch** alarm publishes to **SNS**, which fans out to **email** and a **Lambda** pager function.
- A business event goes to **SNS**, then to **multiple SQS queues** for independent workers.

## Comparison with nearby services
- **SNS:** **broadcast** pub/sub to many subscribers.
- **EventBridge:** **event bus** with **rules** and **targets**.
- **SQS:** **point-to-point** queue consumption.

## Example scenarios
- **Operations** paging, **security** notifications, or **broadcasting configuration changes** to several services.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)
