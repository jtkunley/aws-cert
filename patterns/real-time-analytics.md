# Real-time analytics

## What it is
- Low-latency ingest → insight: dashboards, alerts, stream aggregates.

## When to use it
- Live KPIs; fraud on streams; ops telemetry at speed.

## When NOT to use it
- Hourly/daily batch enough—scheduled ETL cheaper.

## Exam clues
- Real-time, streaming, sub-minute, live dashboard, clickstream volume.

## Common distractors
- **EventBridge** for firehose-scale telemetry.
- **Practice (serverless Q):** **Kinesis** distractor; keyed path still **serverless** + **EventBridge** + **Redshift Serverless**.

## Related AWS services
- Kinesis, MSK, Lambda, OpenSearch, Redshift, Firehose, QuickSight.

## Comparison with nearby patterns
- **Analytics on streams** vs **app integration events** (EventBridge).

## Example scenarios
- Kinesis → KDA → OpenSearch/Redshift for live sales view.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
- “Streaming analytics” → Kinesis/MSK; “business events between services” → EventBridge.
