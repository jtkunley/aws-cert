# SQS queue depth with EC2 for long jobs

## What it is
- This pattern uses **Amazon SQS** as a **durable backlog** between upload or web tiers and **worker** compute.
- **Amazon EC2 Auto Scaling** can scale **consumer** instances using **queue depth** (or related **CloudWatch** metrics) so capacity rises during **business-hour** spikes and falls when the backlog clears.

## Personal notes / memory hooks
- When a single job can run **longer than AWS Lambda’s maximum timeout**, the worker tier usually needs **EC2**, **containers**, or another **long-running** runtime—not **Lambda** as the processor in the option text.
- For **bulk media** outputs, **Amazon S3** is usually **more cost-effective** than **Amazon EFS** when the stem stresses **cost** and **object**-style storage fits.

## When to use it
- **Bursty** queues, **minutes-long** processing, and a goal to **pay for fewer idle workers** by scaling on **backlog**.

## When NOT to use it
- The stem requires **sub-minute** functions only and **no** EC2—then compare **Lambda**, **Fargate**, or **Step Functions** patterns.

## Exam clues
- **SQS**, **queue length**, **Auto Scaling**, **30 minutes** (or similar) **processing time**, **most cost-effective**.

## Links to related questions
- [Cost-effective media processing with SQS and EC2 Auto Scaling](../questions/cost-effective-media-processing-sqs-ec2-s3.md)
