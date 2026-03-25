# Amazon ECS

## What it is
- **Amazon Elastic Container Service (ECS)** is AWS’s **native** service for running **Docker** containers.
- You define **task definitions** and **services**, and ECS schedules work onto capacity you choose (**Fargate** or **EC2**). It integrates with **IAM**, **Amazon VPC**, and load balancers.

## Personal notes / memory hooks
- **ECS** is often described as **AWS’s own container scheduler** (AWS APIs and consoles), while **EKS** is **Kubernetes** on AWS.
- **Practice (serverless modernization question):** A stack with **ECS**, **Fargate**, **Aurora Serverless**, **Redshift Serverless**, and **EventBridge** can look very strong. It tends to lose only when the stem explicitly wants **Kubernetes portability** and **clusters on other cloud providers**—then **EKS** is usually the better fit.

## When to use it
- You are **standardized on AWS** and want **tight integration** with AWS networking, identity, and load balancing.
- Your team wants **simpler operations** than running a full **Kubernetes** control plane themselves (AWS runs the **ECS** control plane).

## When NOT to use it
- The question stresses **portable Kubernetes** workloads that should look the same on **Google GKE**, **Azure AKS**, and **AWS**. In that framing, **Amazon EKS** is usually preferred over **ECS**.

## Exam clues
- Mentions of **task definition**, **ECS service**, **Fargate launch type** versus **EC2 launch type**, and **`awsvpc` network mode**.

## Common distractors
- Mixing up **ECS** and **EKS** when the stem clearly says **Kubernetes** everywhere.
- **Practice (serverless modernization question):** **ECS with Fargate** plus serverless data and **EventBridge** is a believable modern answer. It is ruled out only when the wording forces **multi-cloud Kubernetes**, not AWS-only orchestration.

## Architecture patterns
- **Microservices** behind an **Application Load Balancer**, optional **AWS App Mesh**, and **EventBridge** or **Lambda** for side workflows.
- **Practice (serverless modernization question):** **ECS** appears as the **microservices** runtime with **EventBridge** for integration. That is valid engineering; the exam eliminates it when **EKS** is required by the scenario text.

## Comparison with nearby services
- **ECS** exposes an **AWS-shaped** API for containers.
- **EKS** exposes the **Kubernetes** API. Both can run on **Fargate** so you avoid managing EC2 worker nodes.
- **Practice (serverless modernization question):** When you see **multi-cloud** and **other providers’ clusters**, compare **ECS versus EKS** carefully.

## Example scenarios
- Retail microservices that stay on **AWS** only, or **batch** jobs packaged as scheduled **ECS** tasks.
- **Practice (serverless modernization question):** **ECS**, **Fargate**, serverless databases, and **EventBridge** form a coherent option until the stem demands **Kubernetes everywhere**.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)
