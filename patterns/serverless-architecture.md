# Serverless architecture

## What it is
You build without provisioning or managing servers for major components: compute scales automatically, and you pay roughly for use (Lambda, Fargate, API Gateway, EventBridge, Aurora Serverless, Redshift Serverless, etc.).

## When to use it
Variable traffic, ops reduction goals, event-driven workflows, API backends, stream handlers, spiky analytics or OLTP.

## When NOT to use it
Long-running always-on heavy compute where dedicated capacity is cheaper; strict low-level OS/hardware control; some licensing models tied to VMs.

## Exam clues
“No server management,” “scale to zero,” “pay per use,” “managed capacity,” “Serverless” in service names.

## Common distractors
**EC2 + Auto Scaling** is elastic but **not** serverless in exam language.

## Related AWS services
Lambda, Fargate, EventBridge, Step Functions, Aurora Serverless, Redshift Serverless, API Gateway, AppSync.

## Comparison with nearby patterns
**Serverless** vs **containers on EC2**: ops and unit of scaling differ; **PaaS** (Beanstalk) still hides servers but isn’t the same marketing bucket as Lambda/Fargate serverless.

## Example scenarios
Order pipeline: API Gateway → Lambda → DynamoDB; microservices on Fargate without node groups.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
If the stem demands **serverless**, scan answers for Fargate/Lambda/Serverless data plane—not just “managed.”
