# Amazon EKS

## What it is
- Managed **Kubernetes** control plane in AWS; standard K8s API.

## Personal notes / memory hooks
- “Other cloud providers’ clusters” + containers → **EKS** beats ECS in exam framing.
- **Practice (serverless Q):** two EKS+Fargate options; wrong one drops **Serverless** on Aurora/Redshift, adds **Kinesis** without fixing serverless requirement.

## When to use it
- K8s portability; Helm; mesh; **multi-cloud** same as GKE/AKS.

## When NOT to use it
- Small AWS-only team, no K8s need → **ECS** simpler.

## Exam clues
- Pods, Fargate profile, managed node group, multi-cloud.

## Common distractors
- EKS “more serverless” than ECS by default—both need **Fargate** for that angle.

## Architecture patterns
- GitOps, ingress, cluster autoscaler, multi-account clusters.

## Comparison with nearby services
- **EKS** = Kubernetes; **ECS** = AWS-native; **GKE/AKS** = peer clouds.

## Example scenarios
- Same images on EKS + another CSP’s Kubernetes.
- **Practice (serverless Q):** keyed = EKS+Fargate+EventBridge+Aurora Serverless MySQL+Redshift Serverless.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
