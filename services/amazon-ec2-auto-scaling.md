# Amazon EC2 Auto Scaling

## What it is
- Scales **EC2 instance count** (or related resources) on metrics, schedule, health.

## Personal notes / memory hooks
- More VMs when busy—not serverless units.
- **Practice (serverless Q):** ASG + fixed counts + SNS to EC2/DB → wrong for **serverless** stem.

## When to use it
- Variable traffic on EC2; AZ spread; replace unhealthy nodes; scheduled peaks.

## When NOT to use it
- Stem asks **serverless** compute → Fargate/Lambda, not ASG fleets.

## Exam clues
- ASG, target tracking, scheduled scaling, health checks, multi-AZ.
- **Practice (serverless Q):** ASG per component still = EC2 story.

## Common distractors
- “Elastic” ASG labeled **serverless** → wrong.

## Architecture patterns
- ALB + ASG; workers scale on queue depth (custom metric).

## Comparison with nearby services
- **ASG:** EC2 fleet size.
- **Application Auto Scaling:** ECS tasks, DynamoDB, Aurora replicas, etc.
- **Fargate:** no EC2 node fleet to scale.

## Example scenarios
- Three-tier: ASG app servers; DB separate.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
