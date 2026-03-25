# Serverless modernization & multi-cloud

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

## Trap type
- **Partial fit:** The option looks modern (**EKS**, **Kinesis**, **Aurora**) but drops **serverless** on the **data tier** or swaps the wrong integration primitive.
- **Event bus versus pub/sub versus streaming:** Choosing **SNS** or **Kinesis** when the stem pairs **event-driven** and **streamline application data flows** with a **serverless** stack that **EventBridge** fits best.
- **ECS versus EKS on multi-cloud:** When the stem names **other cloud providers** and **Kubernetes**-style portability, **EKS** usually wins over **ECS** even if both are otherwise plausible.

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

## Question Seed

- Scenario summary: Legacy platforms and databases on EC2 across regions must move to an event-driven serverless model with real-time analytics, cleaner cross-service data flow, and Kubernetes clusters on other cloud providers.
- Primary driver: The stem insists on serverless end-to-end, an integration bus for data flows, and Kubernetes portability to other clouds—so compute, data planes, and messaging must all line up with those keywords, not partial matches.
- Decision focus: Tests whether you pick EKS over ECS for multi-cloud Kubernetes, keep Aurora Serverless and Redshift Serverless (not provisioned) when “serverless architecture” is explicit, and use EventBridge rather than SNS or Kinesis alone for streamlining flows.
- Correct answer pattern: Microservices on EKS with Fargate; Aurora Serverless for transactional MySQL; Redshift Serverless for analytics; EventBridge to integrate and route flows between services.

- Key services:
  - Amazon EKS
  - AWS Fargate
  - Amazon Aurora Serverless
  - Amazon Redshift Serverless
  - Amazon EventBridge

- Common distractor services:
  - Amazon ECS
  - Amazon EC2
  - EC2 Auto Scaling
  - Amazon SNS
  - Amazon Kinesis
  - Amazon Aurora (provisioned)
  - Amazon Redshift (provisioned)

- Key signals:
  - serverless architecture
  - event-driven
  - streamline application data flows
  - real-time analytics
  - multi-cloud
  - Kubernetes on other cloud providers

- Constraints:
  - major components must be serverless, not just auto-scaling EC2
  - OLTP and analytics must stay in separate appropriate tiers
  - portability to non-AWS Kubernetes favors EKS over ECS when the stem says so

- Common traps:
  - ECS with Fargate instead of EKS when other CSP Kubernetes is explicit
  - EKS with Kinesis but provisioned Aurora and Redshift
  - EC2 Auto Scaling with SNS routing and one Aurora PostgreSQL for both OLTP and analytics

- Why traps are wrong:
  - ECS → weaker multi-cloud Kubernetes portability vs EKS when other providers’ clusters are explicit
  - provisioned Aurora/Redshift → violates serverless architecture constraint even if Kinesis satisfies “streaming” language
  - EC2 + SNS + single Aurora PostgreSQL → not serverless; SNS is not a full event bus; one relational store mixes OLTP and warehouse roles

- Pattern tags:
  - #serverless
  - #event-driven
  - #eks-fargate
  - #aurora-serverless
  - #redshift-serverless
  - #eventbridge
  - #multi-cloud-k8s
  - #oltp-vs-warehouse
