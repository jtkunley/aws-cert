# AWS Fargate

## What it is
- **AWS Fargate** runs containers without you provisioning or managing **Amazon EC2** instances for the worker layer.
- You use it with **Amazon Elastic Container Service (ECS)** or **Amazon Elastic Kubernetes Service (EKS)**. Fargate starts tasks or pods; AWS operates the infrastructure underneath.

## Personal notes / memory hooks
- Think of it as **containers without a node fleet** you patch or scale by hand.
- On the serverless modernization practice question, the exam often pairs **Fargate** (serverless compute for containers) with **serverless data** such as **Amazon Aurora Serverless** and **Amazon Redshift Serverless** in the correct answer.

## When to use it
- You have containerized workloads and want **no EC2 instance management** for workers (patching, capacity planning for nodes).
- Traffic is **variable** or you want simpler operations than self-managed node groups.
- You are building on **ECS** or **EKS** and the stem points to **serverless** or **minimal ops** for compute.

## When NOT to use it
- **Cost** is the only driver and load is **steady and high** 24/7—dedicated **EC2** nodes can be cheaper in some cases.
- You need **custom kernel** settings, very tight **latency** tuning at the host, or **DaemonSets** that require direct host access (Fargate has more limits than EC2-backed workers).

## Exam clues
- Phrases like **serverless containers**, **no clusters to manage** (meaning no worker nodes for you to run), and **Fargate** together with **ECS** or **EKS**.

## Common distractors
- Treating Fargate as the same as **AWS Lambda**. Fargate is for **long-running containers** and normal task/pod lifecycles; Lambda is built around short, event-driven function invocations.

## Architecture patterns
- **ECS** services on Fargate behind an **Application Load Balancer**.
- **EKS** pods scheduled with **Fargate profiles**, often in private subnets.
- **Practice (serverless modernization question):** When the scenario stresses **Kubernetes** and **multi-cloud**, **EKS with Fargate** is a common correct pattern. **ECS with Fargate** is a strong option when the story stays AWS-native; the exam uses context to choose between them.

## Comparison with nearby services
- **Fargate** versus **EC2 launch type or managed node groups**: you trade **less operations** for **less control** and a different **price** shape.
- **Lambda** fits **short, event-driven** compute, not general-purpose long-lived containers the way Fargate does.

## Example scenarios
- Moving microservices off **EC2** using **ECS and Fargate** when you do not want to run **Kubernetes**.
- Using **EKS and Fargate** when you want **Kubernetes** APIs and portability without managing worker nodes.
- **Practice (serverless modernization question):** A winning answer often puts **Fargate** on the compute side and **Aurora Serverless** plus **Redshift Serverless** on the data side so the whole stack matches a **serverless** requirement.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
