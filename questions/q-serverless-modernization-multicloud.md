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
Option C (exam-style intent: EKS + Fargate for portable microservices, Aurora Serverless + Redshift Serverless for serverless data tiers, EventBridge for event-driven flows—matches serverless + event-driven + multi-cloud Kubernetes narrative).

## Why it is correct
- **Serverless:** Fargate removes worker-node management; **Aurora Serverless** and **Redshift Serverless** align with serverless data planes.
- **Event-driven + streamlined flows:** **EventBridge** is the standard event-bus pattern for routing and integration between services.
- **Real-time analytics:** **Redshift Serverless** supports the analytics/warehouse role that PostgreSQL-on-EC2 held; streaming/real-time can feed the warehouse via established patterns.
- **Multi-cloud:** **EKS** (Kubernetes) matches portability across other CSPs’ Kubernetes clusters better than ECS in typical exam framing.

## Why the other options are wrong
- **Option A:** Strong on serverless containers and EventBridge, but **ECS** is less aligned with explicit **multi-cloud Kubernetes** portability than **EKS** when the stem calls out other cloud providers’ clusters.
- **Option B:** **EC2 + ASG** is not **serverless**; consolidating analytics into **Aurora PostgreSQL** blurs OLTP vs **warehouse** (analytics PostgreSQL on EC2 → **Redshift** family is a better analytics target); **SNS** is pub/sub, not a full event-bus replacement for complex routing.
- **Option D:** **EKS + Fargate** fits, and **Kinesis** fits **real-time streaming**, but **Aurora MySQL** and **Redshift** without **Serverless** weaken the explicit **serverless architecture** requirement compared to Option C’s **Aurora Serverless** + **Redshift Serverless**; EventBridge in C also maps cleanly to “streamline application data flows” as an integration bus.

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
**Partial fit:** Options that sound modern (EKS, Kinesis, Aurora) but miss **serverless** qualifiers or swap **event bus** vs **streaming** vs **SNS** incorrectly; **ECS vs EKS** on multi-cloud wording.

## Confidence / review status
Unreviewed — revisit after timed practice; validate against current AWS exam guides for wording on “serverless” (provisioned Aurora vs Aurora Serverless naming).

## Source asset
- Screenshot: `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.29.40_PM-caf5db23-2a64-47d9-a69f-1d9d5a32fef1.png`

## Related pages
- [Services template](../.cursor/rules/services-template.md)
- [Patterns template](../.cursor/rules/patterns-template.md)
- [Questions template](../.cursor/rules/questions-template.md)
