# Amazon EC2 Auto Scaling

## What it is
- **Amazon EC2 Auto Scaling** changes how many **EC2 instances** you run (or adjusts related capacity in broader Auto Scaling scenarios) based on demand, schedules, or health checks.

## Personal notes / memory hooks
- Think **“more virtual machines when load goes up.”** That is different from **serverless** units that are not EC2 fleets you size yourself.
- Auto Scaling **does not** by itself make an architecture **serverless**. It still centers on **EC2**.

## When to use it
- Traffic to your application **goes up and down** and you are already on EC2.
- You want **high availability across Availability Zones** or automatic replacement of **unhealthy** instances.
- You need **scheduled** scaling for known peaks (for example, end-of-quarter jobs).

## When NOT to use it
- The exam wants **serverless compute** such as **Fargate** or **Lambda**, or scaling at the **database** layer (for example **Amazon Aurora Serverless**). **Auto Scaling groups** still mean **EC2 instances** in the picture.

## Exam clues
- Phrases like **scale out**, **scale in**, **Auto Scaling group**, **target tracking**, **scheduled scaling**, **health checks**, and **across Availability Zones**.
- **Practice (serverless modernization question):** An answer that pairs **Auto Scaling** with **fixed instance counts** per component is still an **EC2-first** design.

## Common distractors
- Calling **EC2 plus Auto Scaling** **serverless**. The exam treats **serverless** as a different idea (no EC2 fleet you manage for that tier).
- **Practice (serverless modernization question):** **Auto Scaling**, **Amazon SNS** “routing” to EC2 and databases, and a non-serverless data story usually **fail** a stem that asks for **serverless** and a real **event bus**.
- **Practice (video transcoding question):** A minimum size of one instance still leaves baseline cost and management overhead when event-triggered serverless containers are available.

## Architecture patterns
- An **Application Load Balancer** in front of an **Auto Scaling group** of web servers.
- A **worker** tier that scales on **queue depth** using a **CloudWatch** custom metric.

## Comparison with nearby services
- **EC2 Auto Scaling** changes **how many EC2 instances** run.
- **Application Auto Scaling** can scale other resources (for example **Amazon ECS** tasks, **Amazon DynamoDB** throughput, **Aurora** replicas).
- **Fargate** abstracts away the **EC2 worker** layer for containers.

## Example scenarios
- A three-tier application where the **application tier** uses an Auto Scaling group and the **database** is handled separately.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)
- [Cost-effective video transcoding with Fargate](../questions/cost-effective-video-transcoding-with-fargate.md)
- [Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/java-mongodb-ec2-documentdb-multi-az.md)
