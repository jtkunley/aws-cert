# Event-driven architecture

## What it is
- Components **react** to **events** (state changes, signals, schedules) instead of relying only on **synchronous** call chains.
- **Producers** do not need to know every **consumer** in advance, which **reduces coupling** between teams and services.

## When to use it
- One **business event** should trigger **several** independent downstream actions.
- You want **asynchronous** workflows, **extensibility** (add consumers without changing the producer), or **decoupled microservices**.

## When NOT to use it
- The user experience is strictly **request–response** with **no fan-out**, or **observability** is too weak for the team to operate **async** flows safely.

## Exam clues
- Wording like **event-driven**, **decouple**, **publish event**, **react to changes**, and **choreography** versus **orchestration**.

## Common distractors
- Choosing **Amazon SNS** alone when the stem implies **routing rules**, **schedules**, or **SaaS** sources—**Amazon EventBridge** is often the better fit.

## Related AWS services
- **EventBridge**, **SNS**, **SQS**, **Lambda**, **Step Functions**, **Amazon Kinesis** (as a stream of events), **EventBridge Pipes**.

## Comparison with nearby patterns
- **Event-driven** design differs from **batch ETL** on a **clock** and from **streaming** at **shard** scale where **Kinesis** leads.

## Example scenarios
- An **OrderCreated** event triggers **payment**, **inventory**, and **analytics** updates **independently**.
- **Practice (serverless modernization question):** **EventBridge** matches **streamline application data flows** between **microservices** better than **SNS-only** or **Kinesis-only** distractors in that framing.
- **Practice (video transcoding question):** An **S3 upload** event triggers orchestration that starts a per-file compute task instead of continuous polling.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)
- [7. Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/7-cost-effective-media-processing-sqs-ec2-s3.md)
- [3. Cost-effective video transcoding with Fargate](../questions/3-cost-effective-video-transcoding-with-fargate.md)

## Personal notes / memory hooks
- **Event-driven** plus **AWS** exam → draw **EventBridge** first as the **bus** unless the stem is pure **fan-out** (**SNS**).
