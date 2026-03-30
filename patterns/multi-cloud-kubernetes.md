# Multi-cloud with Kubernetes

## What it is
- You run the **same container images** and **Kubernetes** patterns on **Amazon EKS** and on **other** clouds’ **Kubernetes** offerings (for example **GKE** or **AKS**) for **portability**, **resilience**, or **latency**.
- Teams often reuse **Helm** charts, **GitOps**, and similar **tooling** across clusters.

## When to use it
- **Regulatory** or **geography** rules, **acquisitions** that span **clouds**, or a strategy to avoid **lock-in** at the **orchestration** layer.
- You want **global** performance with **local** clusters in more than one **cloud service provider**.

## When NOT to use it
- The roadmap is **AWS-only** and the team lacks **Kubernetes** depth—**Amazon ECS** can reduce **complexity** for some teams.
- Workloads are **small** and **static**.

## Exam clues
- **Multi-cloud**, **other cloud service providers**, **Kubernetes**, **portable workloads**, and **same clusters elsewhere**.

## Common distractors
- **Amazon ECS** is strong on **AWS** but is **less** aligned with “**same as** **GKE** or **AKS**” **portability** than **EKS** in typical **exam** framing.

## Related AWS services
- **Amazon EKS**, **Fargate** for **EKS**, **Amazon ECR**, **AWS App Mesh**, **ExternalDNS**, **cluster autoscaler**, and **related** hybrid offerings where the stem applies.

## Comparison with nearby patterns
- **Multi-cloud Kubernetes** differs from **single-cloud PaaS** (**Elastic Beanstalk**, **Lightsail**) and from **Lambda everywhere**, which is a different **portability** story.

## Example scenarios
- **E-commerce** runs **EKS** in **AWS** and a **second** cluster at another **provider** for **failover** or **edge** performance.
- **Practice (serverless modernization question):** When the stem explicitly mentions **additional clusters on other cloud service providers**, **EKS** often **beats** **ECS** even when both options look **modern** otherwise.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- **Other cloud providers** plus **containers** in the stem → lean toward **EKS** over **ECS** unless the question **narrows** the scope to **AWS-only** portability.
