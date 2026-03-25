# Multi-cloud with Kubernetes

## What it is
Running the same **container workloads** and Kubernetes patterns on **EKS** and on other clouds’ Kubernetes (GKE, AKS, etc.) for portability, resilience, or latency—often same images, Helm charts, GitOps.

## When to use it
Regulatory/geo requirements, acquisition of multiple clouds, avoiding single-vendor API lock-in for the **orchestration** layer, global performance with local clusters.

## When NOT to use it
AWS-only roadmap with no K8s expertise—**ECS** may reduce complexity; small static workloads.

## Exam clues
“Multi-cloud,” “other cloud providers,” “Kubernetes,” “portable workloads,” “same clusters elsewhere.”

## Common distractors
**ECS** is powerful on AWS but less aligned with “same as GKE/AKS” portability than **EKS**.

## Related AWS services
EKS, Fargate (EKS), ECR, App Mesh, ExternalDNS, cluster autoscaler, hybrid with Outposts (related but not multi-cloud CSP).

## Comparison with nearby patterns
**Multi-cloud K8s** vs **single-cloud PaaS** (Elastic Beanstalk, Lightsail); vs **Lambda everywhere** (different portability story).

## Example scenarios
E-commerce runs EKS in AWS and a second CSP region/cluster for failover or edge performance.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Stem mentions **other cloud providers** + containers → **EKS** often beats **ECS** in exam intent.
