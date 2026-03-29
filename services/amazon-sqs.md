# Amazon SQS

## What it is
- **Amazon Simple Queue Service (SQS)** is a managed message queue for decoupling producers and consumers.
- It buffers work and helps absorb traffic spikes with at-least-once delivery semantics.

## Personal notes / memory hooks
- SQS is a durable work backlog, not compute by itself.
- **Practice (video transcoding question):** SQS can queue upload events, but a polling EC2 fleet can still leave baseline idle cost.
- **Practice (media processing question):** **SQS** queue depth driving **EC2 Auto Scaling** is the keyed pattern when jobs run **tens of minutes** and **Lambda** is a trap.

## When to use it
- You need asynchronous decoupling between components.
- You want workers to scale on queue depth.

## When NOT to use it
- You are trying to replace compute logic with a queue.
- The best answer requires fully event-triggered serverless workers that start only when needed.

## Exam clues
- Phrases like **queue**, **decouple**, **poll messages**, **backlog**, and **retry**.
- If options include minimum EC2 capacity plus polling, check whether a more serverless pattern is offered.

## Common distractors
- Picking SQS plus always-on EC2 workers when the stem stresses cost reduction and low management overhead.
- Assuming adding SQS automatically makes architecture serverless.

## Architecture patterns
- **Amazon S3** sends events to **SQS**, and worker services consume messages.
- Queue-depth metrics drive consumer scaling.

## Comparison with nearby services
- **SQS** is point-to-point queueing.
- **SNS** is pub/sub fan-out.
- **EventBridge** is an event bus with rules and routing.

## Example scenarios
- Offloading bursty background processing jobs.
- Buffering file-processing requests before worker execution.

## Links to related questions
- [Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/cost-effective-media-processing-sqs-ec2-s3.md)
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)
