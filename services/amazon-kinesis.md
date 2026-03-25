# Amazon Kinesis

## What it is
- **Streaming:** Data Streams, Firehose, Data Analytics, Video—shards, producers, consumers.

## Personal notes / memory hooks
- High-volume continuous ingest—not default app integration bus.
- **Practice (serverless Q):** Kinesis + EKS+Fargate **but** provisioned Aurora+Redshift → wrong; stem demands **serverless** + EventBridge path.

## When to use it
- Clickstream, IoT, logs, KDA/Flink, replay, many consumers per shard.

## When NOT to use it
- Loose business events between few services—**EventBridge/SQS**.
- Nightly batch only—**Glue/Step Functions**.

## Exam clues
- Shards, producers/consumers, real-time streaming, KDA.

## Common distractors
- Kinesis chosen when stem wants **event bus** routing, low volume.

## Architecture patterns
- Streams → Lambda/KDA → S3/Redshift; Firehose → S3/OpenSearch.

## Comparison with nearby services
- **Kinesis** streams vs **MSK** (Kafka) vs **EventBridge** vs **SQS**.

## Example scenarios
- Live metrics; fraud on streams; central logging.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
