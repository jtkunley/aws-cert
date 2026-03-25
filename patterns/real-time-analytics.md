# Real-time analytics

## What it is
Analyzing data with **low latency** from ingestion to insight: dashboards, alerts, fraud scoring, operational metrics as data arrives—not only nightly batches.

## When to use it
Live ops dashboards, streaming KPIs, anomaly detection on streams, near-real-time personalization within SLA.

## When NOT to use it
Historical reporting tolerating hours delay—batch **Glue/EMR** or scheduled Redshift loads may suffice and cost less.

## Exam clues
“Real-time,” “streaming,” “sub-minute,” “continuous ingest,” “live dashboard,” clickstream/IoT volume.

## Common distractors
**EventBridge** for app integration vs **Kinesis** for high-throughput stream analytics—match the stem’s volume and processing model.

## Related AWS services
Kinesis (Streams, Firehose, Data Analytics), MSK, Lambda, OpenSearch, Redshift (including streaming ingestion patterns), QuickSight.

## Comparison with nearby patterns
**Real-time analytics** vs **event-driven workflows**: overlap but analytics stresses **aggregate/query** paths on continuous data.

## Example scenarios
Kinesis → Lambda/KDA → OpenSearch/Redshift for live sales and inventory metrics.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
“Streaming + analytics” → Kinesis/MSK family; “business events between apps” → EventBridge.
