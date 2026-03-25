# Streaming data ingestion

## What it is
- Continuous high-volume **streams**: shards/partitions, many consumers—**Kinesis/MSK**.

## When to use it
- Clickstream, IoT, logs, replay, parallel consumers.

## When NOT to use it
- Low-volume app events—**EventBridge/SQS**.

## Exam clues
- Shards, producers/consumers, millions/sec, KDA.

## Common distractors
- **EventBridge** for massive ordered telemetry.

## Related AWS services
- Kinesis Data Streams, Firehose, Data Analytics, MSK, Lambda consumers.

## Comparison with nearby patterns
- **Streams:** volume + ordering + processors.
- **Events:** integration between apps.

## Example scenarios
- App → Kinesis → enrich → S3/Redshift.
- **Practice (serverless Q):** Kinesis in distractor; check **serverless** + **EventBridge** fit.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- Huge continuous ingest → Kinesis family.
