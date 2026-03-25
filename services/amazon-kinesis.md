# Amazon Kinesis

## What it is
Real-time **streaming data** platform (Data Streams, Data Firehose, Data Analytics, Video Streams) for ingest, processing, and delivery of continuous data.

## When to use it
High-volume **real-time** ingestion, clickstreams, IoT telemetry, log aggregation, stream processing (KDA/Flink), building custom consumers with shards.

## When NOT to use it
Loose **application integration** and business events between services—**EventBridge** or **SNS/SQS** often suffice; simple batch ETL schedules—**Glue** or **Step Functions** may fit.

## Exam clues
“Real-time streaming,” “shards,” “producers/consumers,” “clickstream,” “millions of events per second,” “Kinesis Data Analytics.”

## Common distractors
Choosing Kinesis when the exam wants **event bus** style routing between microservices without a streaming analytics requirement.

## Architecture patterns
Kinesis Data Streams → Lambda/KDA → S3/Redshift; Firehose → S3/OpenSearch/Redshift for delivery.

## Comparison with nearby services
**Kinesis** (streams) vs **MSK** (Kafka) vs **EventBridge** (events) vs **SQS** (queues).

## Example scenarios
Live dashboards, fraud detection on streams, centralized logging pipeline.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
“Real-time analytics” + **continuous ingest** → Kinesis is a strong signal (vs EventBridge for app integration).
