## Serverless modernization & multi-cloud

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


## Windows File Server, DataSync, and FSx

- Scenario summary: A hybrid workload needs to migrate data from an on-premises Windows file server into AWS, with ongoing daily updates and private network connectivity already in place.
- Primary driver: The stem requires a real file system in the VPC that Windows servers in AWS can use like a traditional share, plus a way to keep data in sync from on premises—not object access or edge-only SMB.
- Decision focus: Tests whether you pair managed SMB storage in AWS (FSx for Windows) with scheduled incremental replication (DataSync) over the existing private path, versus EFS, S3+Transfer, or File Gateway as the main destination.
- Correct answer pattern: Hybrid Windows file migration into managed SMB storage in AWS, using scheduled incremental replication over a private connection.

- Key services:
  - Amazon FSx for Windows File Server
  - AWS DataSync
  - AWS Direct Connect

- Common distractor services:
  - Amazon EFS
  - Amazon S3
  - AWS Transfer Family
  - AWS Storage Gateway File Gateway

- Key signals:
  - Windows file server
  - SMB semantics
  - file system for servers in AWS
  - scheduled daily replication
  - Direct Connect

- Constraints:
  - destination must support Windows-style file sharing
  - destination must be usable by workloads in the VPC
  - migration must support ongoing incremental sync

- Common traps:
  - EFS with DataSync
  - S3 with Transfer Family
  - File Gateway as the primary cloud destination

- Why traps are wrong:
  - EFS with DataSync → wrong protocol/workload fit vs FSx for Windows for corporate SMB shares
  - S3 with Transfer Family → object storage and FTP-family access, not a VPC SMB file system for apps
  - File Gateway as primary cloud target → hybrid edge pattern, not authoritative FSx in VPC for migrated Windows compute

- Pattern tags:
  - #hybrid-storage-migration
  - #windows-file-shares
  - #fsx-windows
  - #datasync
  - #file-vs-object-storage
