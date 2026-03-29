# Amazon MQ

## What it is
- **Amazon MQ** is a **managed message broker** service that supports **Apache ActiveMQ** and **RabbitMQ** APIs.
- It fits teams that want a **broker** with **protocols** and **patterns** familiar from **JMS**, **AMQP**, or **MQTT** workloads.

## Personal notes / memory hooks
- **Amazon MQ** and **Amazon SQS** are different products; an answer that says **MQ** for publishing but **Auto Scaling on SQS** depth (or **Lambda** “pulling from SQS” while the stem wired **MQ**) is usually **internally inconsistent** or **wrong** for the exam.
- **Practice (media processing question):** Prefer **SQS** when the keyed design is **standard queue**, **EC2** workers, and **queue-length** scaling without a **broker** requirement in the stem.

## When to use it
- Migrating **existing** **JMS** or **RabbitMQ** applications with **minimal** broker **replatform** changes.

## When NOT to use it
- The scenario only needs a **simple** **AWS-native** queue and **no** **ActiveMQ** or **RabbitMQ** compatibility story.

## Exam clues
- **Amazon MQ**, **ActiveMQ**, **RabbitMQ**, **message broker**, **JMS**.

## Comparison with nearby services
- **SQS:** **fully managed** queue without you running a **broker** cluster.
- **MQ:** **managed broker** with **open-source** engine compatibility.

## Links to related questions
- [Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/cost-effective-media-processing-sqs-ec2-s3.md)
