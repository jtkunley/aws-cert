# S3 event-triggered processing

## What it is
- This pattern starts downstream processing when objects are uploaded to **Amazon S3**.
- It avoids constant polling by reacting to storage events.

## When to use it
- New files should trigger immediate asynchronous processing.
- Workload volume is variable and you want elastic compute activation.

## When NOT to use it
- Processing requires strict synchronous request-response behavior.
- The workload should run on a fixed schedule regardless of uploads.

## Exam clues
- Phrases like “when a new file is uploaded to S3” and “start processing on upload.”
- Requirements to reduce idle compute and management overhead.

## Common distractors
- Polling S3 continuously from EC2 containers or instances.
- Using event triggers but keeping fixed baseline worker fleets unnecessarily.

## Related AWS services
- Amazon S3, AWS Lambda, Amazon ECS, AWS Fargate, Amazon SQS.

## Comparison with nearby patterns
- Compared with queue polling, direct S3 events reduce continuous polling behavior.
- Compared with schedule-driven jobs, S3 events align compute usage with actual arrivals.

## Example scenarios
- Media transcoding starts when new source files are uploaded.
- File validation and metadata extraction pipelines.

## Links to related questions
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)

## Personal notes / memory hooks
- “Uploaded to S3” is often a trigger phrase for event-driven compute choices.
