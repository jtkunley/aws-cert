# Amazon ECS

## What it is
AWS-native container orchestration: run Docker containers as tasks/services, integrated with IAM, VPC, and AWS load balancers.

## When to use it
AWS-centric microservices, tight integration with AWS APIs, simpler learning curve than Kubernetes for teams standardized on AWS.

## When NOT to use it
When the exam emphasizes **portable Kubernetes** workloads across clouds or strong multi-cloud **same control plane** story—**EKS** often fits that narrative better than ECS.

## Exam clues
“ECS task definition,” “service,” “Fargate launch type,” “EC2 launch type,” “awsvpc network mode.”

## Common distractors
- Confusing ECS with EKS; choosing ECS when stem requires **Kubernetes** everywhere (GKE/AKS parity).
- **Practice (serverless modernization Q):** **ECS + Fargate + Aurora Serverless + Redshift Serverless + EventBridge** is strong but loses when stem explicitly names **additional clusters on other cloud providers**—**EKS** wins portability framing.

## Architecture patterns
- Microservices behind ALB, sidecars, service mesh (App Mesh), EventBridge/Lambda alongside tasks.
- **Practice (serverless modernization Q):** ECS appears as **microservices** host with **EventBridge** data flow—valid pattern, wrong option only because of **multi-cloud Kubernetes** wording.

## Comparison with nearby services
- **ECS** = AWS API; **EKS** = Kubernetes API; both can use **Fargate** for serverless containers.
- **Practice (serverless modernization Q):** compare **ECS vs EKS** when stem says **multi-cloud** and **other CSPs’ clusters**.

## Example scenarios
- Retail microservices on AWS only, batch jobs as scheduled ECS tasks.
- **Practice (serverless modernization Q):** **ECS + Fargate** + serverless data + **EventBridge** is a plausible modern stack—eliminated only by **multi-cloud Kubernetes** requirement.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
ECS = “AWS’s own scheduler.” EKS = “Kubernetes as a service.”
