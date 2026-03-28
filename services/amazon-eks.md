# Amazon EKS

## What it is
- **Amazon Elastic Kubernetes Service (EKS)** is a **managed Kubernetes control plane** in AWS.
- You use the **standard Kubernetes API** (for example `kubectl`, Helm charts). AWS operates the **control plane** and wires it into **VPC**, **IAM**, and load balancers.

## Personal notes / memory hooks
- If the stem says **Kubernetes** or **running the same style of clusters on another cloud provider**, start by considering **EKS**.
- **Practice (Java MongoDB migration question):** **EKS** with **App2Container** is a poor fit when the stem forbids **application changes** and demands an **architecture similar** to **EC2** plus **MongoDB**.
- **Practice (serverless modernization question):** Two answers may both say **EKS** and **Fargate**. The wrong one often keeps **provisioned Amazon Aurora** and **provisioned Amazon Redshift** and adds **Kinesis**, while the stem still insists on a **serverless architecture** and names **Aurora Serverless** and **Redshift Serverless** in the better option.

## When to use it
- Your organization already invests in **Kubernetes** skills and tooling.
- You need **multi-cloud** or **portable** manifests that also run on **GKE**, **AKS**, or similar.
- You want **service mesh**, **GitOps**, or other **Kubernetes-native** patterns.

## When NOT to use it
- A small **AWS-only** team with no Kubernetes requirement may find **Amazon ECS** simpler for the same container workloads.
- A **static site** or tiny service rarely justifies EKS overhead.

## Exam clues
- **Pods**, **Fargate profile**, **managed node group**, **EKS cluster**, **multi-cloud**, **Kubernetes**.

## Common distractors
- Assuming **EKS** is automatically **more serverless** than **ECS**. Either can pair with **Fargate**; **EKS** adds **Kubernetes** complexity either way.
- **Practice (serverless modernization question):** **EKS** and **Fargate** are not enough if the distractor drops **Serverless** from the **database and warehouse** names when the question stresses **serverless architecture**.

## Architecture patterns
- **GitOps** (for example Argo CD), **ingress** controllers, **cluster autoscaler**, multi-account **EKS**, optional **service mesh**.

## Comparison with nearby services
- **EKS** speaks **Kubernetes**. **ECS** speaks **AWS’s** container model. For **multi-cloud** talk, **GKE** and **AKS** are the **non-AWS** counterparts.
- **Practice (serverless modernization question):** The keyed answer often combines **EKS**, **Fargate**, **EventBridge**, **Aurora Serverless MySQL**, and **Redshift Serverless** to hit **event-driven**, **serverless**, and **multi-cloud Kubernetes** at once.

## Example scenarios
- Running the **same container images** on **EKS** in AWS and on another cloud’s **Kubernetes** for performance or residency reasons.
- **Practice (serverless modernization question):** Matches the “**additional clusters on other cloud service providers**” line in the stem.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)
- [Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/java-mongodb-ec2-documentdb-multi-az.md)
