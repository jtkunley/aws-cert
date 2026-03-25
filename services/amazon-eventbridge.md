# Amazon EventBridge

## What it is
- **Amazon EventBridge** is a **serverless event bus**.
- It ingests events from **AWS services**, your own applications, **SaaS** partners, and **scheduled rules**, then **filters and routes** them to **targets** such as **Lambda**, **Amazon SQS**, **Amazon ECS**, **API destinations**, and more.

## Personal notes / memory hooks
- When a question talks about **streamlining application data flows** or **event-driven** integration across services, **EventBridge** is often the star of the correct answer.
- **Practice (serverless modernization question):** **EventBridge** commonly appears with **microservices** and **serverless data** (for example **Aurora Serverless** and **Redshift Serverless**) in the option that best matches the stem.

## When to use it
- You want an **event-driven** architecture where services stay **loosely coupled**.
- You need **rules** (filtering, routing), **schedules** (cron-like automation), or **partner event sources**.
- You are integrating **across AWS accounts** or with **external SaaS** products.

## When NOT to use it
- You only need a **simple fan-out** to many subscribers with **no routing logic**—**Amazon SNS** may be enough.
- You need **very high throughput**, **ordered**, **shard-based streaming**—look at **Amazon Kinesis** or **Amazon MSK** instead.

## Exam clues
- **Event-driven**, **event bus**, **rules**, **targets**, **schedule**, **decouple producers and consumers**, **SaaS integration**.

## Common distractors
- Confusing **EventBridge** with **SNS**. **EventBridge** adds **content-based rules**, **schedules**, and **partner integrations** beyond a basic **topic**.
- **Practice (serverless modernization question):** **SNS** used only to **route data to EC2 and databases** is a weaker match than **EventBridge** when the stem wants a real **integration bus** and **streamlined flows**.

## Architecture patterns
- **Domain events** between microservices, automation triggered by **AWS CloudTrail** or control-plane APIs, and **multi-target** rules (for example **SQS** plus **Lambda**).
- **Practice (serverless modernization question):** Shows up next to **ECS or EKS microservices** plus **Aurora Serverless** and **Redshift Serverless** in the answer set.

## Comparison with nearby services
- **EventBridge:** **rules and bus** semantics.
- **SNS:** **topic** pub/sub broadcast.
- **SQS:** **queue**, usually **one consumer** pulling messages at a time.
- **Kinesis:** **streaming** at high volume with **shards**.

## Example scenarios
- An **order placed** event triggers **inventory**, **payment**, and **notification** paths through separate targets.
- **Practice (serverless modernization question):** Ties together domains like **sales**, **inventory**, **orders**, and **shipping** using **event-driven** wiring.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
