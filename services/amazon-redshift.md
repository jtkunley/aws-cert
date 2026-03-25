# Amazon Redshift

## What it is
- **Amazon Redshift** is a **cloud data warehouse** for **analytics** workloads.
- It stores data in a **columnar** format, runs **massively parallel processing (MPP)** SQL queries, and connects to the **data lake** (for example **Redshift Spectrum**). **Amazon Redshift Serverless** lets you run warehouse queries **without managing a provisioned cluster** in the classic sense.

## Personal notes / memory hooks
- If the stem describes an **analytics database**, **business intelligence**, or **large historical reporting**, think **Redshift** family.
- If the stem describes **online order rows** and **transactional** lookups, that belongs on **OLTP** services such as **Aurora**, not Redshift.
- **Practice (serverless modernization question):** Watch for **Redshift** **without** the word **Serverless** next to **Redshift Serverless** when the question explicitly demands a **serverless architecture**.

## When to use it
- **Business intelligence**, **dashboards**, and **large aggregations** over **historical** data.
- You need a **warehouse** that integrates with **Amazon S3** and your **lake** patterns.

## When NOT to use it
- Primary **OLTP** for a web storefront (**row-by-row** transactional access)—use **Aurora**, **RDS**, or **DynamoDB** instead.
- **Low-latency single-row** lookups for user-facing apps.

## Exam clues
- **Data warehouse**, **analytics**, **BI**, **Redshift Spectrum**, **Serverless** workgroups, **PostgreSQL wire protocol** (compatibility note: still **warehouse** semantics, not OLTP).

## Common distractors
- Placing the **e-commerce transactional** database in **Redshift** because the word **PostgreSQL** appeared for **analytics**.
- **Practice (serverless modernization question):** **PostgreSQL on EC2 used for analytics** should move toward **Redshift Serverless** (or the warehouse path the answers offer), not a mistaken **Aurora PostgreSQL-only** consolidation.

## Architecture patterns
- **ETL/ELT** from **S3**, **Kinesis**, or **Firehose** into **Redshift**.
- **Redshift Serverless** **workgroups** for variable analytics demand.
- **Data sharing** between clusters or accounts where applicable.

## Comparison with nearby services
- **Redshift:** **warehouse** SQL at scale.
- **Athena:** **ad hoc** SQL over **S3** without loading into a cluster.
- **OpenSearch:** **search** and **log analytics** use cases.
- **Aurora:** **OLTP** relational.

## Example scenarios
- Migrating **analytics PostgreSQL on EC2** into **Redshift Serverless** for **sales and inventory** reporting.
- **Practice (serverless modernization question):** The **analytics** role stays on the **warehouse** side; **OLTP** stays on **Aurora Serverless MySQL** in the keyed answer pattern.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
