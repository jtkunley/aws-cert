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
- **C**

## Why it is correct
- **Serverless:** Fargate; **Aurora Serverless MySQL**; **Redshift Serverless**.
- **Event-driven:** **EventBridge** = “streamline application data flows.”
- **Real-time analytics:** warehouse role → **Redshift Serverless** (ex–analytics PostgreSQL on EC2).
- **Multi-cloud:** stem names **other CSPs’ clusters** → **EKS** beats **ECS**.

## Why the other options are wrong
- **A:** **ECS** loses **Kubernetes portability** framing vs **EKS** when multi-cloud explicit.
- **B:** **EC2+ASG** ≠ serverless; **one Aurora PostgreSQL** for OLTP+analytics → wrong split (warehouse → **Redshift**); **SNS** ≠ bus for this stem.
- **D:** **Provisioned** Aurora MySQL + **provisioned** Redshift—drops **Serverless** keyword; **Kinesis** does not fix that gap.

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
- Partial fit: modern stack but wrong **Serverless** SKU, wrong **bus vs stream vs SNS**, **ECS vs EKS** on multi-cloud.

## Confidence / review status
- Unreviewed. Re-check exam wording on **Aurora Serverless** vs provisioned.

## Source asset
- `/Users/james/.cursor/projects/Users-james-work-aws-cert/assets/Screenshot_2026-03-24_at_8.29.40_PM-caf5db23-2a64-47d9-a69f-1d9d5a32fef1.png`

## Related pages
- [Services template](../.cursor/rules/services-template.mdc)
- [Patterns template](../.cursor/rules/patterns-template.mdc)
- [Questions template](../.cursor/rules/questions-template.mdc)
