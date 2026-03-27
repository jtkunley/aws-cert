# AWS Lambda

## What it is
- **AWS Lambda** is a serverless compute service that runs code in response to events.
- You do not manage servers, and billing is based on execution duration and requests.

## Personal notes / memory hooks
- Lambda is excellent for short event-driven processing, orchestration, and glue logic.
- **Practice (video transcoding question):** Lambda can trigger container tasks, but it should not run a 40-minute transcode job directly.

## When to use it
- Event-driven functions triggered by **Amazon S3**, **Amazon EventBridge**, **Amazon SQS**, or APIs.
- Short orchestration logic, transforms, enrichment, and routing.

## When NOT to use it
- Long-running single-task processing that exceeds Lambda duration limits.
- Workloads that need full OS control or long-lived processes.

## Exam clues
- Phrases like **event trigger**, **no servers**, **function**, and **invoke on object upload**.
- Mentions of runtime limits should make you validate Lambda fit before selecting it.

## Common distractors
- Choosing Lambda for long jobs that exceed its maximum execution time.
- Confusing Lambda orchestration use with Lambda as the heavy compute engine.

## Architecture patterns
- **Amazon S3** event triggers **Lambda**, which calls downstream services such as **ECS RunTask**.
- Event bus or queue events invoke Lambda for lightweight orchestration.

## Comparison with nearby services
- **Lambda** is short-lived function compute.
- **AWS Fargate** is better for long-running container tasks.
- **Amazon EC2** gives full host control but increases management overhead.

## Example scenarios
- Triggering metadata extraction when a file lands in **Amazon S3**.
- **Practice (video transcoding question):** Invoking **ECS on Fargate** per uploaded video.

## Links to related questions
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)
