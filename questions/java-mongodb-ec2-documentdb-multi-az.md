# Java and MongoDB migration to EC2 and DocumentDB for high availability

## Original question
An organization is migrating its on-premises web application to AWS. The application comprises a Java-based backend and a NoSQL MongoDB database. Due to constraints, the application cannot be modified during the migration process, and the migrated solution must maintain an architecture similar to the on-premises setup. Additionally, the application requires high availability for both the backend and the database to ensure continuous operation.

Which solution will meet these requirements while adhering to the constraints?

**Option A:** Deploy the Java application on Amazon EC2 instances within an Auto Scaling group spanning multiple Availability Zones. Migrate the MongoDB database to Amazon DocumentDB (with MongoDB compatibility) across multiple Availability Zones.

**Option B:** Containerize the Java application using AWS App2Container and deploy it on Amazon Elastic Kubernetes Service (EKS). Use Amazon DynamoDB for the database layer to achieve high availability.

**Option C:** Use AWS Elastic Beanstalk to deploy the Java application and migrate the MongoDB database to Amazon Aurora with multiple read replicas across different Availability Zones.

**Option D:** Deploy the Java application on Amazon EC2 instances within an Auto Scaling group spanning multiple Availability Zones. Use Amazon DocumentDB (with MongoDB compatibility) in a single Availability Zone deployment to host the MongoDB database.

## Correct answer
- **Option A** is the best fit.
- It keeps **Java** on **Amazon EC2** behind an **Auto Scaling group** across **multiple Availability Zones** for **backend** high availability, and moves **MongoDB** to **Amazon DocumentDB** with **MongoDB compatibility** deployed **across multiple Availability Zones** for **database** high availability.

## Why it is correct
- **EC2** with **Auto Scaling** across **AZs** matches a **similar** classic **compute** architecture to many on-premises **Java** deployments without forcing **Kubernetes** or **containers**.
- **DocumentDB** provides a **managed**, **MongoDB-compatible** target so the **NoSQL** application can migrate without rewriting data access around a different engine.
- **Multi-AZ** coverage for **both** tiers satisfies the **continuous operation** requirement stated in the stem.

## Why the other options are wrong
- **Option B:** **AWS App2Container** and **Amazon EKS** introduce a **container** and **Kubernetes** operational model that conflicts with **similar architecture** and **no modification** constraints in exam framing. **Amazon DynamoDB** is **not** a **MongoDB**-compatible replacement for an existing **MongoDB** application.
- **Option C:** **Amazon Aurora** is a **relational** **MySQL** or **PostgreSQL**–compatible engine, not a **MongoDB** datastore, so it fails the **MongoDB** requirement even though **Elastic Beanstalk** can run **Java**.
- **Option D:** **Single-AZ** **DocumentDB** does not meet the **high availability** requirement for the **database** when the stem requires **HA** for **both** backend and database, even though the **compute** tier is multi-AZ.

## Trap type
- **Wrong database family:** **Aurora** or **DynamoDB** paired with a **MongoDB** stem.
- **HA gap:** **Multi-AZ** compute with **single-AZ** database.
- **False modernization:** **EKS** and **App2Container** when the scenario locks **architecture** and **change** depth.

## Services involved
- [Amazon EC2](../services/amazon-ec2.md)
- [Amazon EC2 Auto Scaling](../services/amazon-ec2-auto-scaling.md)
- [Amazon DocumentDB](../services/amazon-documentdb.md)
- [AWS App2Container](../services/aws-app2container.md)
- [Amazon EKS](../services/amazon-eks.md)
- [Amazon DynamoDB](../services/amazon-dynamodb.md)
- [AWS Elastic Beanstalk](../services/aws-elastic-beanstalk.md)
- [Amazon Aurora](../services/amazon-aurora.md)

## Pattern tags
- [Lift-and-shift MongoDB with DocumentDB compatibility](../patterns/lift-shift-mongodb-documentdb.md)
- [Six Rs cloud migration](../patterns/six-rs-cloud-migration.md)

## Question Seed

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
