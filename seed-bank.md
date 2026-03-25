## Serverless modernization & multi-cloud

- Scenario summary: Legacy applications and databases on Amazon EC2 across regions need to become event-driven and serverless, improve analytics latency, smooth data movement between services, and support Kubernetes clusters on other cloud providers.
- Primary driver: The stem requires a **serverless** architecture for the main building blocks, not only elastic scaling on instances.
- Decision focus: This question checks whether you choose portable managed Kubernetes and serverless data tiers, wire services with a real event bus, and reject answers that slip back to EC2, wrong data roles, or streaming or pub/sub tools used as a substitute for that bus.
- Correct answer pattern: Serverless container workloads on managed Kubernetes, separate serverless relational and analytics warehouse tiers, and a managed event bus that routes and integrates traffic between services.

- Key services:
  - Amazon Elastic Kubernetes Service (EKS)
  - AWS Fargate
  - Amazon Aurora Serverless
  - Amazon Redshift Serverless
  - Amazon EventBridge

- Common distractor services:
  - Amazon Elastic Container Service (ECS)
  - Amazon EC2
  - EC2 Auto Scaling groups
  - Amazon Simple Notification Service (SNS)
  - Amazon Kinesis
  - Amazon Aurora (provisioned)
  - Amazon Redshift (provisioned)

- Key signals:
  - serverless architecture
  - event-driven
  - streamline data flows
  - real-time analytics
  - multi-cloud
  - Kubernetes elsewhere

- Constraints:
  - Core compute and data services must be serverless, not merely EC2 with Auto Scaling.
  - Transactional data and analytics warehouse data must stay in separate, appropriate tiers.
  - When the stem names Kubernetes on other cloud providers, the orchestration choice should align with cross-cloud portability.

- Common traps:
  - Picking Elastic Container Service with Fargate when the scenario stresses Kubernetes on other cloud providers.
  - Pairing Elastic Kubernetes Service and Kinesis with provisioned Aurora and provisioned Redshift while the stem demands a serverless architecture.
  - Relying on EC2 Auto Scaling, SNS routing, and a single Aurora PostgreSQL database for both storefront transactions and analytics.

- Why traps are wrong:
  - Elastic Container Service with Fargate → violates the constraint that Kubernetes portability to other clouds should drive the orchestration pick when the stem says so.
  - Elastic Kubernetes Service with Kinesis and provisioned Aurora and Redshift → violates the constraint that the architecture stay serverless for major components.
  - EC2 Auto Scaling with SNS and one Aurora PostgreSQL for both roles → violates serverless design, full event-bus integration, and separate OLTP versus warehouse tiers.

- Pattern tags:
  - #serverless-architecture
  - #event-driven-design
  - #kubernetes-portability
  - #managed-event-bus
  - #transactional-versus-analytics
  - #multi-cloud-kubernetes


## Windows File Server, DataSync, and FSx

- Scenario summary: A company keeps data on an on-premises Windows file server and needs it available in AWS for instances already in a VPC, with daily growth, incremental updates, and private connectivity already available.
- Primary driver: The answer must provide a **Windows-style file share inside the VPC**, not only object storage or a share that stays anchored at the edge.
- Decision focus: This question checks whether you select managed SMB file storage in the Region plus scheduled file replication from on premises, instead of NFS-oriented file, object plus transfer protocols, or a hybrid gateway as the main place data lives for cloud workloads.
- Correct answer pattern: Ongoing replication from an on-premises Windows file server into managed Windows file storage in the VPC, using a private network path and a scheduled synchronization service.

- Key services:
  - Amazon FSx for Windows File Server
  - AWS DataSync
  - AWS Direct Connect

- Common distractor services:
  - Amazon Elastic File System (EFS)
  - Amazon S3
  - AWS Transfer Family
  - AWS Storage Gateway (File Gateway)

- Key signals:
  - Windows file server
  - SMB
  - file system in VPC
  - daily replication
  - Direct Connect

- Constraints:
  - The destination must behave like Windows file sharing for applications in AWS.
  - The destination must live where VPC workloads can mount it as their primary file tier.
  - The migration approach must support repeated incremental synchronization after the initial bulk copy.

- Common traps:
  - Choosing Elastic File System with DataSync and mounting it for a classic Windows file-server scenario.
  - Landing files in S3 and using Transfer Family as the main access path for general Windows application storage.
  - Making File Gateway the primary destination for data that migrated Windows instances in the VPC must treat as their file system.

- Why traps are wrong:
  - Elastic File System with DataSync → violates the constraint that the workload is Windows SMB–first rather than NFS-first.
  - S3 with Transfer Family → violates the constraint that the scenario asks for a file system in the VPC, not object storage with FTP-style protocols.
  - File Gateway as the primary cloud destination → violates the constraint that authoritative Windows file storage for instances in AWS should sit in the VPC as managed SMB, not mainly at the on-premises edge.

- Pattern tags:
  - #hybrid-file-migration
  - #windows-smb-shares
  - #vpc-file-storage
  - #incremental-replication
  - #file-versus-object-storage
