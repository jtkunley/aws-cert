# Multi-region deployments

## What it is
Running workloads in **more than one AWS Region** for latency to users, disaster recovery, regulatory residency, or capacity; data and traffic patterns must be designed (read replicas, Global Accelerator, Route 53, Aurora Global Database, etc.).

## When to use it
User bases spread globally, RTO/RPO requiring geographic failover, data sovereignty, scaling beyond a single region’s limits.

## When NOT to use it
Premature complexity for single-region users with no compliance driver; when the exam answer is cheaper single-region HA across **AZs** only.

## Exam clues
“Multiple regions,” “low latency worldwide,” “failover between regions,” “active-active,” “global audience,” “Aurora Global Database,” “Route 53 routing policies.”

## Common distractors
Confusing **multi-AZ** (one region) with **multi-region**; choosing multi-region when stem only needs **AZ** high availability.

## Related AWS services
Route 53, CloudFront, Global Accelerator, Aurora Global Database, DynamoDB global tables, S3 cross-region replication, multi-region KMS.

## Comparison with nearby patterns
**Multi-region** vs **multi-cloud**: different axis (AWS geography vs multiple CSPs); stems may require both.

## Example scenarios
E-commerce front ends in `us-east-1` and `eu-west-1` with regional data residency rules.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Stem says “across multiple regions” → flag DR/latency patterns; combine with **multi-cloud** only when other CSPs are explicit.
