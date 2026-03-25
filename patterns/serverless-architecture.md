# Serverless architecture

## What it is
- No server provisioning for major pieces: Lambda, Fargate, EventBridge, Aurora Serverless, Redshift Serverless, etc.

## When to use it
- Variable load; cut ops; event-driven; pay-per-use friendly.

## When NOT to use it
- 24/7 maxed dedicated capacity cheaper; strict host/kernel control.

## Exam clues
- No server management, scale-to-zero, “Serverless” in service names.

## Common distractors
- **EC2 + ASG** called serverless.
- **Practice (serverless Q):** EKS+Fargate OK; dropping **Serverless** on Aurora/Redshift breaks stem.

## Related AWS services
- Lambda, Fargate, EventBridge, Step Functions, Aurora Serverless, Redshift Serverless, API Gateway.

## Comparison with nearby patterns
- **Serverless** vs **EC2 containers:** who patches nodes.

## Example scenarios
- API Gateway → Lambda → DynamoDB.
- **Practice (serverless Q):** scan answers for **Fargate + *Serverless* data** together.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Stem says **serverless** → require **Serverless** SKUs where offered, not “managed” only.
