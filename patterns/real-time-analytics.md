# Real-time analytics

## What it is
- You analyze data with **low latency** from **ingestion** to **insight**: **dashboards**, **alerts**, **fraud** scoring, or **operational metrics** as data **arrives**, not only in **nightly** batches.

## When to use it
- **Live operations** dashboards, **streaming KPIs**, **anomaly detection** on **streams**, or **near-real-time personalization** within a clear **SLA**.

## When NOT to use it
- **Historical reporting** can tolerate **hours** of delay—**batch** jobs on **AWS Glue** or **Amazon EMR**, or **scheduled** **Redshift** loads, may **cost less** and stay simpler.

## Exam clues
- **Real-time**, **streaming**, **sub-minute**, **continuous ingest**, **live dashboard**, and **high-volume** **clickstream** or **IoT** language.

## Common distractors
- Confusing **EventBridge** (**application integration**) with **Kinesis** (**high-throughput stream analytics**)—match **volume** and **processing** model to the stem.
- **Practice (serverless modernization question):** **Real-time analytics** makes **Kinesis** tempting, but another option may still win on **serverless data planes** plus an **event bus**—**Redshift Serverless** with **EventBridge** can still satisfy **analytics** intent without forcing **Kinesis** into the **keyed** answer.

## Related AWS services
- **Kinesis** (Data Streams, Data Firehose, Data Analytics), **Amazon MSK**, **Lambda**, **Amazon OpenSearch Service**, **Amazon Redshift** (including **streaming ingestion** patterns), **Amazon QuickSight**.

## Comparison with nearby patterns
- **Real-time analytics** overlaps with **event-driven** workflows, but **analytics** stresses **aggregate** and **query** paths on **continuous** data.

## Example scenarios
- **Kinesis** to **Lambda** or **Kinesis Data Analytics** to **OpenSearch** or **Redshift** for **live** sales and **inventory** metrics.

## Links to related questions
- [Serverless modernization & multi-cloud](../questions/serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- **Streaming plus analytics** → **Kinesis** or **MSK** family; **business events between apps** → **EventBridge**.
