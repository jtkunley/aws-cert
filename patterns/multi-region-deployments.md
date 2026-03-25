# Multi-region deployments

## What it is
- Workloads in **>1 AWS Region**: DR, latency, residency, capacity.

## When to use it
- Global users; RTO/RPO across geography; data sovereignty.

## When NOT to use it
- Single-region users; stem only needs **multi-AZ** in one region.

## Exam clues
- Multiple regions, active-active, Global Accelerator, Route 53 policies, Aurora Global Database.

## Common distractors
- **Multi-AZ** labeled multi-region.

## Related AWS services
- Route 53, CloudFront, Global Accelerator, Aurora Global DB, DynamoDB global tables, S3 CRR.

## Comparison with nearby patterns
- **Multi-region:** AWS geography.
- **Multi-cloud:** multiple CSPs—orthogonal.

## Example scenarios
- E-commerce front ends in two regions for residency.
- **Practice (serverless Q):** EC2 **multi-region** = current state; stem also adds **other CSP clusters**.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- “Across multiple regions” → DR/latency signals; stack with multi-cloud only if stem says so.
