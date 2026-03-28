# Re-platform Docker and MySQL with OpenJDK on ECS and RDS

## Original question
A company is hosting its production environment on its on-premises servers. Most of the applications are packed as Docker containers that are manually run on self-managed virtual machines. The web servers are using the latest commercial Oracle Java SE suite which costs the company thousands of dollars in licensing costs. The MySQL databases are installed on separate servers configured on a 'source-replica' setup for high availability. The company wants to migrate the whole environment to AWS Cloud to take advantage of its flexibility and agility, as well as use OpenJDK to save licensing costs without major changes in its applications.

Which of the following application migration strategies meet the above requirement?

**Option A:** Re-host the environment on the AWS Cloud platform by creating EC2 Instances that mirror the current web servers and database servers. Host the Docker instances on Amazon EC2 and test the new OpenJDK Docker containers on these instances. Create a dump of the on-premises MySQL databases and upload it to an Amazon S3 bucket. Launch a new Amazon EC2 Instance with a MySQL database and import the data from Amazon S3.

**Option B:** Re-platform the environment on the AWS Cloud platform by running the Docker containers on Amazon ECS. Test the new OpenJDK Docker containers and upload them on Amazon Elastic Container Registry. Migrate the MySQL database to Amazon RDS using AWS Database Migration Service.

**Option C:** Re-factor/re-architect the environment on AWS Cloud by converting the Docker containers to run on AWS Lambda Functions. Convert the MySQL database to Amazon DynamoDB using the AWS Schema Conversion Tool (AWS SCT) to save on costs.

**Option D:** Re-platform the environment on the AWS Cloud platform by deploying the Docker containers on AWS App Runner to reduce operational overhead. Test the new OpenJDK Docker containers and upload them on Amazon Elastic Container Registry (ECR). Convert the MySQL database to Amazon DynamoDB using the AWS Schema Conversion Tool (AWS SCT) to save on costs.

## Correct answer
- **Option B** is the best fit.
- It **re-platforms** Docker onto **Amazon ECS**, stores images in **Amazon Elastic Container Registry**, swaps **Oracle Java** for **OpenJDK** in the container workflow, and moves **MySQL** to **Amazon RDS** using **AWS Database Migration Service** for managed relational migration.

## Why it is correct
- **OpenJDK** in **Docker** images addresses the **Oracle Java SE** licensing cost without forcing a new compute paradigm.
- **Amazon ECS** is a standard managed path for running the same **container** workloads with less VM babysitting than purely mirrored **EC2** roles.
- **Amazon RDS** keeps a **managed MySQL-compatible** relational tier that fits **source-replica** style high availability in AWS, while **AWS DMS** supports online migration into **RDS**.

## Why the other options are wrong
- **Option A:** This is **re-host** lift-and-shift onto **EC2** with a **manual dump to S3** and restore on another **EC2** instance. It does not match the keyed **re-platform** pattern with **ECS**, **ECR**, **RDS**, and **DMS**, and it keeps more undifferentiated database operations on instances.
- **Option C:** **AWS Lambda** is a different execution model than long-running **Docker** services, and **DynamoDB** is not a drop-in **MySQL** replacement. Together this is **re-architect** scale change, which conflicts with **without major changes**.
- **Option D:** **App Runner** could be a managed container option for some web stacks, but pairing it with **DynamoDB** via **AWS SCT** still implies a **major relational-to-NoSQL** redesign, which violates the **no major changes** constraint even though the label says **re-platform**.

## Trap type
- **Six R mismatch:** Options that say **re-platform** but include **Lambda** or **DynamoDB**-style re-architecture.
- **Relational versus NoSQL:** Treating **MySQL** migration as **DynamoDB** conversion when the scenario requires continuity.
- **Manual database path:** **S3** dump and **EC2** import presented as the full strategy versus **RDS** plus **DMS**.

## Services involved
- [Amazon EC2](../services/amazon-ec2.md)
- [Amazon S3](../services/amazon-s3.md)
- [Amazon ECS](../services/amazon-ecs.md)
- [Amazon Elastic Container Registry](../services/amazon-elastic-container-registry.md)
- [AWS App Runner](../services/aws-app-runner.md)
- [AWS Lambda](../services/aws-lambda.md)
- [Amazon RDS](../services/amazon-rds.md)
- [AWS Database Migration Service](../services/aws-database-migration-service.md)
- [AWS Schema Conversion Tool](../services/aws-schema-conversion-tool.md)
- [Amazon DynamoDB](../services/amazon-dynamodb.md)

## Pattern tags
- [Six Rs cloud migration](../patterns/six-rs-cloud-migration.md)
- [Managed database modernization](../patterns/managed-database-modernization.md)

## Question Seed

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
