# Six Rs cloud migration

## What it is
- The **Six Rs** (sometimes summarized as **5 Rs** in older material) describe how far you change an application when you move it to the cloud: **rehost**, **replatform**, **refactor** / **re-architect**, plus retire, retain, and repurchase variants depending on the framework.
- Exam questions often pair a **strategy label** in the answer text with concrete AWS services, so you must check whether the **depth of change** matches the scenario constraints.

## Personal notes / memory hooks
- **Rehost (lift-and-shift):** Move workloads with minimal change, often **Amazon EC2** mirroring today’s servers.
- **Replatform (lift-and-reshape):** Same core application shape but swap to managed building blocks, for example **Amazon ECS** for containers or **Amazon RDS** instead of self-managed database VMs.
- **Refactor / re-architect:** Rework how the app runs, for example **AWS Lambda** for compute or **Amazon DynamoDB** instead of a relational engine; this usually implies **major** design and code work.

## When to use it
- The stem mentions **migration strategy**, **minimal change**, **agility**, or names a **Six R** label in the options.

## When NOT to use it
- Do not pick **re-architect** answers when the scenario explicitly requires **no major application changes**.

## Exam clues
- **Without major changes** usually rules out **Lambda**-first and **relational-to-NoSQL** jumps in the same breath.
- **Replatform** answers often combine **containers on a managed orchestrator**, **a container registry**, and **managed relational databases** with **AWS DMS**.

## Links to related questions
- [5. Re-platform Docker and MySQL with OpenJDK on ECS and RDS](../questions/5-replatform-docker-mysql-openjdk-ecs-rds.md)
- [6. Java and MongoDB migration to EC2 and DocumentDB for high availability](../questions/6-java-mongodb-ec2-documentdb-multi-az.md)
