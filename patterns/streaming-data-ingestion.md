# Streaming data ingestion

## What it is
Continuous, high-volume data enters the system as a **stream** with producers, shards/partitions, and consumers—**Kinesis** or **MSK** are common anchors.

## When to use it
Clickstreams, logs, IoT, gaming telemetry, real-time aggregations, replay, multiple independent consumer applications.

## When NOT to use it
Low-volume business events between a few microservices—**EventBridge** or **SQS** may be simpler and cheaper.

## Exam clues
“Streaming,” “shards,” “producers and consumers,” “millions of records,” “Kinesis Data Analytics,” “replay.”

## Common distractors
Using **EventBridge** for firehose-scale telemetry—wrong tool for massive ordered stream processing.

## Related AWS services
Kinesis Data Streams, Firehose, Data Analytics, Lambda event source mapping, MSK, Flink.

## Comparison with nearby patterns
**Streaming ingestion** vs **event-driven integration**: streams emphasize volume/ordering/processing frameworks; events emphasize app decoupling.

## Example scenarios
Mobile app analytics pipeline: app → Kinesis → Lambda enrichment → S3/Redshift.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
Volume + continuous + analytics processing → **Kinesis** family.
