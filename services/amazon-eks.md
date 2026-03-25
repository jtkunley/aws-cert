# Amazon EKS

## What it is
Managed Kubernetes control plane on AWS: you use standard Kubernetes APIs; AWS runs the control plane and integrates with VPC, IAM, and load balancers.

## When to use it
Kubernetes skills/portability, multi-team platforms, Helm charts, service mesh, or exam scenarios mentioning **multi-cloud** / same manifests on other CSPs’ Kubernetes.

## When NOT to use it
Small AWS-only teams with no K8s need—**ECS** can be simpler; very simple static sites—overkill.

## Exam clues
“Kubernetes,” “pods,” “EKS,” “Fargate profile,” “managed node group,” “multi-cloud clusters.”

## Common distractors
- Assuming EKS is “more serverless” than ECS by default—both can be serverless **with Fargate**; EKS adds Kubernetes complexity.
- **Practice (serverless modernization Q):** two answers use **EKS + Fargate**; wrong one pairs **provisioned Aurora MySQL + provisioned Redshift + Kinesis**—misses **Serverless** in **Aurora Serverless** / **Redshift Serverless** when stem demands **serverless architecture**.

## Architecture patterns
- GitOps (Argo CD), ingress controllers, cluster autoscaler, hybrid mesh, multi-account EKS.

## Comparison with nearby services
- **EKS** (Kubernetes) vs **ECS** (AWS-native); both orchestrate containers; **GKE/AKS** are the non-AWS counterparts in multi-cloud talk.

## Example scenarios
- Same container images deployed on EKS and another cloud’s Kubernetes for performance/geo.
- **Practice (serverless modernization Q):** **EKS + Fargate + EventBridge + Aurora Serverless MySQL + Redshift Serverless** matches **event-driven + serverless + multi-cloud Kubernetes**.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Stem says “Kubernetes” or “multi-cloud same as other providers” → think **EKS**.
