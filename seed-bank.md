## Cost-effective media processing with SQS and EC2 Auto Scaling

- Scenario summary: A web portal uploads media to on-premises NAS and enqueues work; a single worker processes messages with jobs up to 30 minutes; the queue is much deeper during business hours and drains overnight; the goal is a more cost-effective AWS design.
- Primary driver: Long-running per-message work rules out Lambda for the processor tier, and the architecture should scale workers with queue backlog while keeping storage economical for media outputs.
- Decision focus: Pick a consistent queue plus worker scaling story and object storage that fits bursty backlog and the 30-minute runtime.
- Correct answer pattern: Standard SQS queue, EC2 Auto Scaling scaled on SQS backlog, and processed media stored in Amazon S3.

- Key services:
  - Amazon SQS
  - Amazon EC2
  - Amazon EC2 Auto Scaling
  - Amazon S3

- Common distractor services:
  - AWS Lambda
  - Amazon MQ
  - Amazon Elastic File System (EFS)

- Key signals:
  - up to 30 minutes to process
  - message queue
  - higher backlog during business hours
  - most cost-effective
  - media files

- Constraints:
  - Each processing job must support runtimes longer than AWS Lambda’s maximum execution timeout.
  - The solution should scale processing capacity with queue depth to reduce idle cost after hours.
  - Processed media storage should favor cost-effective object storage for this exam framing.

- Common traps:
  - Using Lambda to process each queued media job end-to-end.
  - Mixing Amazon MQ publishing with Amazon SQS metrics or consumption language in the same option.
  - Sending processed media to Amazon EFS when Amazon S3 fits object-style outputs and cost emphasis.

- Why traps are wrong:
  - Lambda as the media processor → violates the long-running job constraint because 30-minute work exceeds Lambda’s timeout limit.
  - Amazon MQ paired with SQS scaling or SQS pull wording → violates a coherent queue architecture constraint for the exam answer.
  - EFS for processed media in this stem → violates the cost-effective object-storage fit that Amazon S3 provides for media outputs.

- Pattern tags:
  - #sqs-backlog-scaling
  - #ec2-auto-scaling
  - #long-running-workers
  - #lambda-duration-limit
  - #s3-media-storage


## Cost-effective video transcoding with Fargate

- Scenario summary: A video platform currently transcodes uploads on one EC2-based Java worker, each item takes about 40 minutes, and metrics show meaningful idle time; the architecture must become more available, scalable, and cheaper to run.
- Primary driver: The per-video runtime is too long for Lambda and the workload should avoid always-on EC2 workers.
- Decision focus: Select an event-driven compute model that launches long-running jobs on demand with low operational overhead.
- Correct answer pattern: S3 upload events trigger orchestration that starts serverless container tasks for each file, so compute scales per job and stops when work is done.

- Key services:
  - Amazon S3
  - AWS Lambda
  - Amazon ECS
  - AWS Fargate

- Common distractor services:
  - Amazon EC2
  - EC2 Auto Scaling groups
  - Amazon SQS
  - AWS Lambda (as the main transcoder)

- Key signals:
  - 40-minute processing time
  - uploaded to Amazon S3
  - EC2 idle 35 percent
  - high availability and scalability
  - reduce management overhead
  - most cost-effective

- Constraints:
  - The processing unit must support long-running jobs that exceed Lambda duration limits.
  - The design should avoid continuous polling workers and minimize always-on compute cost.
  - The architecture should scale automatically with upload events and keep operations low.

- Common traps:
  - Using Lambda directly for full transcoding jobs.
  - Keeping EC2 workers as the main execution layer with polling.
  - Adding queues but still requiring a minimum always-on instance fleet.

- Why traps are wrong:
  - Lambda-only transcoding → violates the long-running processing constraint because 40-minute jobs exceed Lambda runtime limits.
  - EC2 polling workers → violates the low-operations and cost-efficiency constraints by keeping managed instances and idle capacity.
  - SQS plus minimum EC2 Auto Scaling baseline → violates the on-demand compute constraint because baseline instances still run when demand is low.

- Pattern tags:
  - #event-driven-processing
  - #serverless-containers
  - #long-running-jobs
  - #ec2-to-fargate-modernization
  - #cost-efficient-elastic-compute


## Java and MongoDB migration to EC2 and DocumentDB for high availability

- Scenario summary: An on-premises Java web backend and MongoDB must move to AWS with no application changes, an architecture that stays similar to today, and high availability for both application and database tiers.
- Primary driver: The design must preserve MongoDB-oriented access patterns and avoid single points of failure across Availability Zones.
- Decision focus: Choose compute and database services that match MongoDB compatibility and multi-AZ high availability without swapping to unrelated engines or partial HA.
- Correct answer pattern: Java on EC2 Auto Scaling across multiple Availability Zones with MongoDB-compatible data on Amazon DocumentDB deployed for high availability across multiple Availability Zones.

- Key services:
  - Amazon EC2
  - Amazon EC2 Auto Scaling
  - Amazon DocumentDB

- Common distractor services:
  - AWS App2Container
  - Amazon Elastic Kubernetes Service (EKS)
  - Amazon DynamoDB
  - AWS Elastic Beanstalk
  - Amazon Aurora

- Key signals:
  - Java backend
  - MongoDB
  - cannot be modified
  - similar architecture
  - high availability
  - backend and database

- Constraints:
  - The application must not be modified during migration.
  - The architecture must remain similar to the on-premises Java plus MongoDB layout.
  - Both the application tier and the database tier must support high availability.

- Common traps:
  - Replacing MongoDB with DynamoDB or Aurora while claiming the same application fit.
  - Using single-AZ DocumentDB while the compute tier spans multiple Availability Zones.
  - Containerizing on EKS with App2Container when the scenario stresses minimal change and similar architecture.

- Why traps are wrong:
  - App2Container with EKS and DynamoDB → violates the MongoDB compatibility constraint and conflicts with the similar-architecture and no-modification constraints.
  - Elastic Beanstalk with Aurora → violates the MongoDB datastore constraint because Aurora is a relational SQL engine family, not MongoDB-compatible document storage.
  - Multi-AZ EC2 with single-AZ DocumentDB → violates the database high availability constraint when continuous operation is required for both tiers.

- Pattern tags:
  - #mongodb-compatibility
  - #amazon-documentdb
  - #multi-az-high-availability
  - #ec2-auto-scaling
  - #lift-and-shift-constraints


## Re-platform Docker and MySQL with OpenJDK on ECS and RDS

- Scenario summary: On-premises Docker runs on self-managed VMs, web tiers use costly commercial Oracle Java, and MySQL runs in a source-replica layout; the company wants AWS agility, OpenJDK to cut license cost, and no major application rewrite.
- Primary driver: The migration must save Java licensing with OpenJDK while keeping Docker and MySQL continuity and avoiding a full re-architecture.
- Decision focus: Match the Six R strategy label to the real depth of change, and keep relational MySQL on a managed path instead of serverless or NoSQL rewrites.
- Correct answer pattern: Re-platform containers onto managed orchestration with a private registry for OpenJDK images, and migrate MySQL into Amazon RDS using AWS DMS.

- Key services:
  - Amazon ECS
  - Amazon Elastic Container Registry
  - Amazon RDS
  - AWS Database Migration Service

- Common distractor services:
  - Amazon EC2
  - Amazon S3
  - AWS Lambda
  - AWS App Runner
  - Amazon DynamoDB
  - AWS Schema Conversion Tool

- Key signals:
  - Docker on virtual machines
  - Oracle Java licensing
  - OpenJDK
  - MySQL source-replica
  - without major changes
  - migration strategy

- Constraints:
  - The application must not undergo a major redesign or data model rewrite.
  - The database tier must stay relational and MySQL-compatible rather than move to NoSQL for this scenario.
  - The answer’s migration strategy label must align with how much the option actually changes compute and data tiers.

- Common traps:
  - Re-architect answers that move Docker services into Lambda and MySQL into DynamoDB.
  - Re-platform wording paired with DynamoDB and AWS Schema Conversion Tool as if it were a minor MySQL move.
  - Re-host on EC2 with S3 dump and manual MySQL restore when the exam expects ECS, ECR, RDS, and DMS together.

- Why traps are wrong:
  - Lambda plus DynamoDB → violates the no-major-changes constraint and the stay-on-relational-MySQL constraint.
  - App Runner with DynamoDB and AWS Schema Conversion Tool → violates the keep-MySQL-relational constraint because DynamoDB is not a drop-in MySQL replacement.
  - Re-host with EC2 and S3 restore → violates the keyed re-platform pattern that uses Amazon ECS, Amazon ECR, Amazon RDS, and AWS DMS for managed containers and managed MySQL migration.

- Pattern tags:
  - #six-rs-migration
  - #replatform
  - #docker-to-ecs
  - #rds-mysql-migration
  - #openjdk-versus-oracle-java


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


## SQL Server to MySQL managed migration

- Scenario summary: A mission-critical on-premises SQL Server environment must move to AWS with lower operational overhead, and the target platform requires migration into MySQL using managed services.
- Primary driver: The migration must solve heterogeneous SQL Server-to-MySQL conversion with managed migration tooling, not file-transfer workflows.
- Decision focus: This question tests whether you choose schema conversion plus managed database replication for cross-engine migration, instead of backup-and-load or file synchronization options.
- Correct answer pattern: Convert source schema to the target engine format, provision a managed MySQL target in Amazon RDS, and run managed replication from source to target during migration.

- Key services:
  - AWS Schema Conversion Tool
  - AWS Database Migration Service
  - Amazon RDS for MySQL

- Common distractor services:
  - AWS Glue
  - AWS Snowball Edge
  - AWS DataSync
  - Amazon S3

- Key signals:
  - heterogeneous migration
  - SQL Server to MySQL
  - managed services preferred
  - mission-critical database
  - on-premises to AWS

- Constraints:
  - The migration must support cross-engine schema compatibility from SQL Server to MySQL.
  - The solution should prioritize managed AWS services to reduce operational overhead.
  - The data-move mechanism must match relational database migration semantics rather than file replication semantics.

- Common traps:
  - Using S3 backup plus Glue load as the main migration workflow.
  - Choosing Snowball Edge as the primary migration method without offline-transfer need.
  - Using DataSync for SQL Server-to-MySQL relational migration.

- Why traps are wrong:
  - S3 backup plus Glue load → violates the heterogeneous schema-conversion constraint for SQL Server-to-MySQL migration.
  - Snowball Edge primary path → violates the managed online migration-fit constraint when schema conversion plus managed replication is required.
  - DataSync for relational migration → violates the relational migration-semantics constraint because DataSync is for file and object transfer patterns.

- Pattern tags:
  - #heterogeneous-database-migration
  - #schema-conversion-and-replication
  - #managed-migration-services
  - #sql-server-to-mysql


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
