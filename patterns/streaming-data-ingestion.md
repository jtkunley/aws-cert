# Streaming data ingestion

## What it is
- Data enters the system **continuously** and at **high volume** as a **stream** with **producers**, **shards** or **partitions**, and **consumers**.
- **Amazon Kinesis** and **Amazon MSK** are common **anchors** for this pattern on **AWS**.

## When to use it
- **Clickstreams**, **logs**, **IoT** telemetry, **gaming** events, **real-time aggregations**, **replay**, or **multiple independent consumer** applications.

## When NOT to use it
- **Low-volume business events** between a **few microservices**—**EventBridge** or **SQS** is often **simpler** and **cheaper**.

## Exam clues
- **Streaming**, **shards**, **producers and consumers**, **millions of records**, **Kinesis Data Analytics**, and **replay**.

## Common distractors
- Using **EventBridge** for **firehose-scale telemetry** when the stem clearly wants **ordered**, **high-throughput** stream processing.

## Related AWS services
- **Kinesis Data Streams**, **Kinesis Data Firehose**, **Kinesis Data Analytics**, **Lambda** event source mappings, **MSK**, **Apache Flink** on **AWS**.

## Comparison with nearby patterns
- **Streaming ingestion** stresses **volume**, **ordering**, and **processing frameworks**; **event-driven integration** stresses **decoupling** between **applications**.

## Example scenarios
- **Mobile** app analytics: app → **Kinesis** → **Lambda** enrichment → **S3** or **Redshift**.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- **Volume**, **continuous**, and **analytics processing** together point to the **Kinesis** family.
- **Practice (serverless modernization question):** **Kinesis** paired with **provisioned Aurora** and **provisioned Redshift** is a **trap** when the stem insists on **serverless** and **EventBridge**-style **integration**.
