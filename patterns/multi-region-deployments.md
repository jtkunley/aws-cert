# Multi-region deployments

## What it is
- You run workloads in **more than one AWS Region** for **latency** to users, **disaster recovery**, **regulatory residency**, or **capacity**.
- **Data** and **traffic** patterns must be designed on purpose: **read replicas**, **AWS Global Accelerator**, **Amazon Route 53** policies, **Aurora Global Database**, and similar building blocks.

## When to use it
- Users are spread **globally**, **RTO** and **RPO** call for **geographic failover**, **data sovereignty** applies, or a single **Region** limit matters.

## When NOT to use it
- **Complexity** is **premature** for **single-Region** users with **no** compliance driver.
- The **exam** answer is **high availability across Availability Zones** **only** inside **one Region**.

## Exam clues
- **Multiple Regions**, **low latency worldwide**, **failover between regions**, **active-active**, **global audience**, **Aurora Global Database**, and **Route 53 routing policies**.
- **Practice (serverless modernization question):** **EC2 across multiple regions** describes **current state**; the **keyed** answer may still emphasize **multi-cloud** (**other providers**) as a **separate** requirement.

## Common distractors
- Mixing up **multi-AZ** (**one Region**) with **multi-region** designs.
- Choosing **multi-region** when the stem only needs **AZ-level** resilience.

## Related AWS services
- **Route 53**, **Amazon CloudFront**, **Global Accelerator**, **Aurora Global Database**, **DynamoDB global tables**, **S3 cross-Region replication**, **multi-Region KMS**.

## Comparison with nearby patterns
- **Multi-region** is **AWS geography**; **multi-cloud** is **multiple CSPs**; stems sometimes need **both**.

## Example scenarios
- **E-commerce** front ends in **us-east-1** and **eu-west-1** with **data residency** rules per **jurisdiction**.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- **Across multiple regions** in the stem → flag **DR** and **latency** patterns; add **multi-cloud** only when **other providers** are **explicit**.
