# Amazon EC2

## What it is
- **Amazon Elastic Compute Cloud (EC2)** gives you virtual machines in the cloud.
- You choose an instance type and an Amazon Machine Image (AMI), then run a full guest operating system with complete control over the machine.

## Personal notes / memory hooks
- A simple way to remember EC2 is **“I own the box.”** You are responsible for the operating system and what runs on it.
- If an exam question is pushing **serverless** or **no servers to manage**, EC2 is usually the wrong answer.
- On the serverless modernization practice question, the starting point is often **EC2 spread across multiple regions**. The correct modernization path moves toward **serverless compute and data**, not a bigger EC2 footprint.

## When to use it
- **Lift-and-shift** migrations where you need a normal server environment.
- You have strict **kernel**, driver, or licensing needs that managed services do not support.
- Workloads run **steadily at high utilization** where **Reserved Instances** or Savings Plans can reduce cost.
- You need **instance store** or unusual hardware (for example GPUs).

## When NOT to use it
- The question asks for **serverless**, minimal operations, or **scale to zero** on compute. In those cases, look at **AWS Fargate**, **AWS Lambda**, or a managed service instead, unless the stem explicitly says EC2.

## Exam clues
- Watch for words like **instances**, **SSH**, **AMI**, **instance store**, **Dedicated Hosts**, **placement groups**, or legacy apps described as running on **servers**.
- When the scenario opens with **EC2 in multiple Regions** and then asks you to **modernize**, treat that as a **legacy baseline**, not as proof that EC2 should stay the center of the design.
- **Practice (serverless modernization question):** Web and mobile **e-commerce** (sales, inventory, orders, shipping) still on EC2, with a **multi-Region** footprint, matches this pattern.

## Common distractors
- Picking **EC2 plus Auto Scaling** when the requirement is **serverless** or **no server management**.
- Mixing up **EC2** with **container workers**: **Fargate** removes the need for you to manage EC2 for the worker layer.
- **Practice (serverless modernization question):** If the stem lists **EC2** as today’s compute, the right answers generally **reduce reliance on EC2**, not grow fleets.
- **Practice (video transcoding question):** If a worker is idle a large percentage of time, always-on EC2 polling can be less cost-effective than event-triggered Fargate tasks.

## Architecture patterns
- Classic **three-tier** web applications, **bastion** hosts for administrative access, **batch** workers on a fixed pool of instances, and **hybrid** designs that use **AWS Direct Connect** or a **Site-to-Site VPN**.
- **Practice (serverless modernization question):** The same business areas (online sales, inventory, orders, logistics) often appear as separate **microservices** in the answer choices.

## Comparison with nearby services
- **EC2:** you operate the virtual machine.
- **Fargate:** you do not manage EC2 instances for your container workers.
- **Lambda:** short-lived, function-shaped compute rather than a long-running server you treat like a VM.
- **Elastic Beanstalk:** a platform layer that still runs your application on EC2 underneath.

## Example scenarios
- A legacy monolith on Linux, software that requires a specific OS, **GPU** workloads, or a **custom kernel module**.
- **Practice (serverless modernization question):** The described current state is often **applications on EC2** plus **self-managed MySQL and PostgreSQL on EC2**. That lines up with the [Legacy EC2 data tier](../patterns/legacy-ec2-data-tier.md) pattern.
- **Practice (SQL Server to MySQL migration question):** On-premises SQL Server clusters often represent the legacy operational baseline that managed migration targets aim to replace.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)
- [7. Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/7-cost-effective-media-processing-sqs-ec2-s3.md)
- [3. Cost-effective video transcoding with Fargate](../questions/3-cost-effective-video-transcoding-with-fargate.md)
- [4. SQL Server to MySQL managed migration](../questions/4-sql-server-to-mysql-managed-migration.md)
- [5. Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/5-replatform-docker-mysql-openjdk-ecs-rds.md)
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
