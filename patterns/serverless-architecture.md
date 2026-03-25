# Serverless architecture

## What it is
- You build so you **do not** provision or manage **servers** for the main building blocks: compute **scales** with demand, and you pay closer to **per use** for many services.
- Examples include **AWS Lambda**, **AWS Fargate**, **Amazon API Gateway**, **Amazon EventBridge**, **Amazon Aurora Serverless**, and **Amazon Redshift Serverless**.

## When to use it
- Traffic is **variable**, you want **less operations** work, workflows are **event-driven**, or you need **API** backends and **stream** handlers without running a **fleet** you patch yourself.

## When NOT to use it
- Workloads are **always on** and **heavy** where **dedicated** capacity is **cheaper** at steady state.
- You need **low-level** **operating system** or **hardware** control, or licensing ties you to **virtual machines**.

## Exam clues
- Phrases like **no server management**, **scale to zero** (where applicable), **pay per use**, **managed capacity**, and the word **Serverless** in **service names**.

## Common distractors
- **Amazon EC2** with **Auto Scaling** is **elastic** but **not** **serverless** in typical **exam** wording.
- **Practice (serverless modernization question):** **Amazon EKS** with **Fargate** helps on the **compute** side, but a distractor may swap **Aurora Serverless** for **provisioned Aurora** or **Redshift Serverless** for **provisioned Redshift**—read **serverless** in the stem **literally**.

## Related AWS services
- **Lambda**, **Fargate**, **EventBridge**, **AWS Step Functions**, **Aurora Serverless**, **Redshift Serverless**, **API Gateway**, **AWS AppSync**.

## Comparison with nearby patterns
- **Serverless** differs from **containers on EC2** in who runs and **patches** worker **nodes**; **Elastic Beanstalk** still hides servers but is not the same bucket as **Lambda** or **Fargate** in many questions.

## Example scenarios
- An order pipeline: **API Gateway** to **Lambda** to **DynamoDB**; **microservices** on **Fargate** without **self-managed** node groups.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- If the stem demands **serverless**, scan answers for **Fargate**, **Lambda**, and **Serverless** **data** tiers—not only the word **managed**.
