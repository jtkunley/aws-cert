# Amazon Kinesis

## What it is
- **Amazon Kinesis** is a family of services for **real-time streaming data**.
- Common pieces include **Kinesis Data Streams** (durable streams with **shards**), **Kinesis Data Firehose** (delivery to data stores), **Kinesis Data Analytics** (stream processing with SQL or Apache Flink), and **Kinesis Video Streams**.

## Personal notes / memory hooks
- When a stem stresses **huge continuous ingest** and **many consumers** reading the same stream, **Kinesis** is a strong signal.
- For **low-volume business events** between a handful of microservices, **EventBridge** or **SQS** is often simpler.
- **Practice (serverless modernization question):** An answer may add **Kinesis** because the stem mentions **real-time analytics**, but if that same answer keeps **provisioned Aurora** and **provisioned Redshift**, it can still **fail** a **serverless architecture** requirement compared with **Aurora Serverless**, **Redshift Serverless**, and **EventBridge**.

## When to use it
- **Clickstreams**, **IoT telemetry**, **application logs**, **gaming** events, or other **high-volume** streams.
- You need **replay**, **multiple independent consumers**, or **stream analytics** (for example **Kinesis Data Analytics**).

## When NOT to use it
- The workload is mainly **application integration** with modest volume—**EventBridge** or **SNS/SQS** may be enough and easier to operate.
- The job is a **simple scheduled batch**—**AWS Glue** or **Step Functions** might fit better.

## Exam clues
- **Shards**, **producers and consumers**, **real-time streaming**, **millions of events per second**, **Kinesis Data Analytics**.

## Common distractors
- Choosing **Kinesis** when the exam really wants **EventBridge-style routing** between a few services **without** streaming-scale requirements.
- **Practice (serverless modernization question):** **Real-time analytics** in the stem can still be satisfied with **Redshift Serverless** plus ingestion paths; do not pick **Kinesis** if that forces you to **drop serverless** from the **data tier** when the question insists on **serverless**.

## Architecture patterns
- **Kinesis Data Streams** → **Lambda** or **Kinesis Data Analytics** → **Amazon S3** or **Amazon Redshift**.
- **Kinesis Data Firehose** → **S3**, **Amazon OpenSearch Service**, or **Redshift** for **delivery**.

## Comparison with nearby services
- **Kinesis:** AWS-native **streaming** with **shards**.
- **MSK (Managed Streaming for Apache Kafka):** **Kafka** compatibility.
- **EventBridge:** **event bus** for integration, not shard-based streaming at the same scale story.
- **SQS:** **queue**, different consumption model.

## Example scenarios
- **Live dashboards**, **fraud detection** on streams, or a **central logging** pipeline.
- **Practice (serverless modernization question):** Read **serverless** and **integration** requirements together before you lock onto **Kinesis** alone.

## Links to related questions
- [1. Serverless modernization & multi-cloud](../questions/1-serverless-modernization-multicloud.md)
