# Amazon EC2 Auto Scaling

## What it is
Automatically adjusts the number of EC2 instances (or other resources in broader Auto Scaling concepts) based on demand, schedules, or health.

## Personal notes / memory hooks
ASG = “more VMs when busy.” It does not make the architecture serverless by itself.

## When to use it
Variable traffic on EC2, need high availability across AZs, replace unhealthy instances, scheduled scale for known peaks.

## When NOT to use it
When requirements call for **serverless** compute (Fargate/Lambda) or managed scaling at the service layer (Aurora Serverless, etc.)—ASG still implies **EC2 fleets**.

## Exam clues
- “Scale out/in,” “ASG,” “target tracking,” “scheduled scaling,” “health checks,” “across Availability Zones.”
- **Practice (serverless modernization Q):** answer choice pairs ASG with **fixed instance counts** per component—still **EC2-centric**.

## Common distractors
- Picking ASG + EC2 as “modern serverless”—it scales **instances**, not serverless units.
- **Practice (serverless modernization Q):** ASG + **SNS “routing” to EC2 and DBs** does not satisfy **serverless** or **event-driven bus** requirements in the stem.

## Architecture patterns
- Web tier behind ALB with ASG; worker tier scaling on queue depth (CloudWatch custom metrics).

## Comparison with nearby services
- **ASG** scales EC2; **Application Auto Scaling** scales ECS tasks, DynamoDB, Aurora replicas, etc.; **Fargate** capacity is abstracted differently.

## Example scenarios
- Three-tier app: ASG for app servers, fixed or separate DB tier.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
