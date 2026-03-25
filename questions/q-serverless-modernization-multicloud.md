# Q-SERVERLESS-MODERNIZATION-MULTICLOUD

## Original question
An organization operates web and mobile platforms for online sales, inventory management, order processing, and shipping logistics. The platforms are running on Amazon EC2 instances across multiple regions. The organization's databases include a MySQL database for the e-commerce site and a PostgreSQL database for analytics, both managed on EC2 instances.

A solutions architect requires a solution to transition the organization's architecture to an **event-driven, serverless architecture** to improve efficiency and data processing speeds, enable **real-time analytics**, and **streamline application data flows**. The company also plans to launch a **multi-cloud configuration** that runs additional clusters on other cloud service providers to further improve the site's performance.

Which of the following options would most efficiently meet these requirements?

**Option A:** Use Amazon ECS with Fargate to repackage applications as microservices. Migrate e-commerce and analytics databases to Aurora Serverless MySQL and Redshift Serverless. Manage data flow between services using Amazon EventBridge.

**Option B:** Create Auto Scaling groups for each platform component with specific EC2 instance numbers. Migrate e-commerce MySQL and analytics PostgreSQL databases to Amazon Aurora PostgreSQL. Use Amazon SNS to route incoming data to the right EC2 instances and databases.

**Option C:** Migrate to microservices with Amazon EKS and Fargate. Use Aurora Serverless MySQL for e-commerce and Redshift Serverless for analytics. Use Amazon EventBridge to streamline and manage data flows.

**Option D:** Migrate app components to microservices with Amazon EKS using AWS Fargate. Change e-commerce MySQL to Amazon Aurora MySQL and analytics DB to Amazon Redshift. Use Amazon Kinesis for real-time data streaming.

## Correct answer
- **Option C** is the best match for how this kind of question is usually scored.
- It combines **Amazon EKS** with **AWS Fargate** so **microservices** run on **Kubernetes** without you managing worker nodes, uses **Amazon Aurora Serverless** and **Amazon Redshift Serverless** for **serverless** relational and **warehouse** tiers, and uses **Amazon EventBridge** to **route** and **integrate** events between services.

## Why it is correct
- **Serverless posture:** **Fargate** removes **EC2 worker-node** management for the container plane, while **Aurora Serverless** and **Redshift Serverless** keep the **data** side aligned with a **serverless** ask in the stem.
- **Event-driven flows:** **EventBridge** is the usual **event bus** answer when the scenario wants to **streamline** and **coordinate** data flow across **many services** with **rules** and **targets**.
- **Real-time analytics:** **Redshift Serverless** fits the **analytics warehouse** role that **PostgreSQL on EC2** held; **real-time** paths can still **feed** the warehouse through **ingestion** patterns the exam accepts without forcing **Kinesis** into every correct option.
- **Multi-cloud:** **EKS** (**Kubernetes**) lines up with running **similar clusters** on **other cloud providers** better than **ECS** in typical **exam framing**, because **Kubernetes** is the **portable** control plane across vendors.

## Why the other options are wrong
- **Option A** is strong on **serverless containers** and **EventBridge**, but **Amazon ECS** is a weaker fit than **EKS** when the stem **explicitly** calls out **additional clusters on other cloud service providers** and **Kubernetes** portability.
- **Option B** keeps **EC2** and **Auto Scaling groups**, which is **not** a **serverless** architecture. Moving both **OLTP** and **analytics** into **one Amazon Aurora PostgreSQL** blurs **transactional** versus **warehouse** roles; **analytics PostgreSQL on EC2** usually maps to the **Redshift** family. **Amazon SNS** is **pub/sub**, not a full **event bus** replacement for **rich routing** like **EventBridge**.
- **Option D** keeps **EKS** and **Fargate**, and **Amazon Kinesis** matches **real-time streaming** language, but **Amazon Aurora MySQL** and **Amazon Redshift** **without** the **Serverless** names weaken the stem’s **serverless architecture** requirement compared with **Option C**. **Option C** also maps **streamline application data flows** cleanly to **EventBridge** as an **integration bus**.

## Services involved
- [Amazon EC2](../services/amazon-ec2.md), [EC2 Auto Scaling](../services/amazon-ec2-auto-scaling.md)
- [Amazon ECS](../services/amazon-ecs.md), [AWS Fargate](../services/aws-fargate.md), [Amazon EKS](../services/amazon-eks.md)
- [Amazon EventBridge](../services/amazon-eventbridge.md), [Amazon SNS](../services/amazon-sns.md), [Amazon Kinesis](../services/amazon-kinesis.md)
- [Amazon Aurora](../services/amazon-aurora.md), [Amazon Redshift](../services/amazon-redshift.md)

## Pattern tags
- [Multi-region deployments](../patterns/multi-region-deployments.md)
- [Microservices](../patterns/microservices.md)
- [Serverless architecture](../patterns/serverless-architecture.md)
- [Event-driven architecture](../patterns/event-driven-architecture.md)
- [Real-time analytics](../patterns/real-time-analytics.md)
- [Multi-cloud with Kubernetes](../patterns/multi-cloud-kubernetes.md)
- [Event bus integration](../patterns/event-bus-integration.md)
- [Pub/sub fan-out](../patterns/pub-sub-fan-out.md)
- [Streaming data ingestion](../patterns/streaming-data-ingestion.md)
- [Legacy EC2 data tier](../patterns/legacy-ec2-data-tier.md)

## Trap type
- **Partial fit:** Answers that sound modern (**EKS**, **Kinesis**, **Aurora**) but drop **serverless** qualifiers on the **data tier**, or mix up **event bus** (**EventBridge**), **streaming** (**Kinesis**), and **pub/sub** (**SNS**).
- Watch **ECS versus EKS** when the stem mentions **multi-cloud** and **Kubernetes** on **other providers**.

## Confidence / review status
- **Unreviewed** under exam conditions; revisit after **timed** practice.
- Confirm wording against the **current** exam guide if **Amazon** tightens what **serverless** means (**provisioned Aurora** versus **Aurora Serverless** naming).

## Source asset
- Screenshot: `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.29.40_PM-caf5db23-2a64-47d9-a69f-1d9d5a32fef1.png`

## Related pages
- [Services template](../.cursor/rules/services-template.mdc)
- [Patterns template](../.cursor/rules/patterns-template.mdc)
- [Questions template](../.cursor/rules/questions-template.mdc)
