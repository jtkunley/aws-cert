# Multi-cloud with Kubernetes

## What it is
- Same container/K8s model on **EKS** + other CSP Kubernetes (GKE, AKS).

## When to use it
- Portability mandate; multi-vendor; same Helm/manifests everywhere.

## When NOT to use it
- AWS-only, no K8s—**ECS** simpler.

## Exam clues
- Other cloud providers, Kubernetes, clusters elsewhere, portable workloads.

## Common distractors
- **ECS** when stem demands **same as GKE/AKS**.

## Related AWS services
- EKS, Fargate (EKS), ECR, App Mesh, autoscaler.

## Comparison with nearby patterns
- **Multi-cloud K8s** vs **single-cloud PaaS** vs **Lambda everywhere**.

## Example scenarios
- EKS + second CSP cluster for perf/geo.
- **Practice (serverless Q):** “additional clusters on other CSPs” → **EKS** over **ECS**.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Other CSPs + containers → **EKS** in keyed answers.
