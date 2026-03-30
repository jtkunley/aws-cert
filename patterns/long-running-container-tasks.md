# Long-running container tasks

## What it is
- This pattern runs long jobs in containers that start per unit of work and stop when done.
- It is commonly implemented with **Amazon ECS** and **AWS Fargate** for serverless container execution.

## When to use it
- Individual jobs run longer than Lambda limits.
- Work arrives intermittently and you want compute to run only while jobs are active.

## When NOT to use it
- Jobs are tiny and fit cleanly in Lambda.
- Workloads require fixed always-on hosts for specialized OS behavior.

## Exam clues
- Long per-item processing time (for example tens of minutes).
- Requirements for high availability, scaling, and lower operations.

## Common distractors
- Rewriting long jobs into a single Lambda function.
- Containerizing but keeping always-on EC2 polling workers as the primary design.

## Related AWS services
- Amazon ECS, AWS Fargate, AWS Lambda, Amazon S3, Amazon SQS.

## Comparison with nearby patterns
- Compared with Lambda-only execution, container tasks handle longer runtime workloads.
- Compared with EC2 worker fleets, Fargate tasks reduce host management overhead.

## Example scenarios
- Video transcoding jobs launched per file upload.
- Batch media processing where each unit can run for tens of minutes.

## Links to related questions
- [3. Cost-effective video transcoding with Fargate](../questions/3-cost-effective-video-transcoding-with-fargate.md)

## Personal notes / memory hooks
- If job runtime is long and bursty, think “event triggers task,” not “always-on poller.”
