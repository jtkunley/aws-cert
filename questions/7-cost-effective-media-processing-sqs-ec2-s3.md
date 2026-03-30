# 7. Cost-effective media processing with SQS and EC2 Auto Scaling

## Original question
A company offers a service that allows users to upload media files through a web portal. The web servers accept the media files and are directly uploaded to the on-premises Network Attached Storage (NAS server). For each uploaded media file, a corresponding message is sent to the message queue. A processing server picks up each message and processes each media file, which can take up to 30 minutes to process. The company noticed that the number of media files waiting in the processing queue is significantly higher during business hours, but the processing server quickly catches up after business hours. To save costs, the company hired a Solutions Architect to improve the media processing by migrating the workload to AWS Cloud.

Which of the following options is the most cost-effective solution?

**Option A:** Reconfigure the existing web servers to publish messages to a standard queue on Amazon SQS. Create an AWS Lambda function that will pull requests from the SQS queue and process the media files. Invoke the Lambda function every time a new message is sent to the queue. Send the processed media files to an Amazon S3 bucket.

**Option B:** Reconfigure the existing web servers to publish messages to a queue in Amazon MQ. Create an Auto Scaling group of Amazon EC2 instances that will pull requests from the queue and process the media files. Configure the Auto Scaling group to scale based on the length of the Amazon SQS queue. Send the processed media files to an Amazon EFS mount point and shut down the EC2 instances after processing is complete.

**Option C:** Reconfigure the existing web servers to publish messages to a queue in Amazon MQ. Create an AWS Lambda function that will pull requests from the Amazon SQS queue and process the media files. Invoke the Lambda function every time a new message is sent to the queue. Send the processed media files to an Amazon EFS volume.

**Option D:** Reconfigure the existing web servers to publish messages to a standard queue on Amazon SQS. Create an Auto Scaling group of Amazon EC2 instances that will pull requests from the queue and process the media files. Configure the Auto Scaling group to scale based on the length of the SQS queue. Send the processed media files to an Amazon S3 bucket.

## Correct answer
- **Option D** is the best fit.
- **Amazon SQS** holds work items, **EC2** instances in an **Auto Scaling group** scale with **queue depth** so capacity follows **business-hour** backlog, and **Amazon S3** stores processed **media** cost-effectively.

## Why it is correct
- Processing can take **up to 30 minutes**, which exceeds **AWS Lambda’s** maximum **timeout**, so **EC2**-based workers fit the runtime requirement.
- **Auto Scaling** on **SQS** backlog matches the pattern where the queue is deep in **business hours** and shallow later, which supports **cost savings** through scale-down.
- **S3** fits **object** storage for **media** outputs and is typically **more cost-effective** than **EFS** for this workload class in exam-style answers.

## Why the other options are wrong
- **Option A:** **Lambda** cannot run a single invocation long enough for **30-minute** jobs, so this violates the processing-time constraint.
- **Option B:** The option mixes **Amazon MQ** with scaling on **Amazon SQS** queue length, which is an inconsistent queue story. It also steers output to **EFS** and describes **shutting down** instances in a way that fights a clean **Auto Scaling** consumer pattern compared with **S3**.
- **Option C:** It again mixes **Amazon MQ** with **Lambda** consuming **SQS**, which is internally inconsistent, and **Lambda** still fails the **30-minute** runtime requirement. **EFS** is also a weaker **cost** fit than **S3** for typical processed **media** storage in this framing.

## Trap type
- **Lambda duration limit:** Using **Lambda** as the processor for **tens of minutes** of work per message.
- **Queue product confusion:** **Amazon MQ** in the narrative paired with **SQS** scaling or **SQS** consumption wording.
- **Storage economics:** Choosing **EFS** when **S3** matches **media** objects and **cost** emphasis.

## Services involved
- [Amazon SQS](../services/amazon-sqs.md)
- [Amazon EC2](../services/amazon-ec2.md)
- [Amazon EC2 Auto Scaling](../services/amazon-ec2-auto-scaling.md)
- [Amazon S3](../services/amazon-s3.md)
- [AWS Lambda](../services/aws-lambda.md)
- [Amazon MQ](../services/amazon-mq.md)
- [Amazon Elastic File System (EFS)](../services/amazon-efs.md)

## Pattern tags
- [SQS queue depth with EC2 for long jobs](../patterns/sqs-queue-depth-ec2-long-jobs.md)
- [Event-driven architecture](../patterns/event-driven-architecture.md)

## Question Seed

- Scenario summary: A web portal uploads media to on-premises NAS and enqueues work; a single worker processes messages with jobs up to 30 minutes; the queue is much deeper during business hours and drains overnight; the goal is a more cost-effective AWS design.
- Primary driver: Long-running per-message work rules out Lambda for the processor tier, and the architecture should scale workers with queue backlog while keeping storage economical for media outputs.
- Decision focus: Pick a consistent queue plus worker scaling story and object storage that fits bursty backlog and the 30-minute runtime.
- Correct answer pattern: Standard SQS queue, EC2 Auto Scaling scaled on SQS backlog, and processed media stored in Amazon S3.

- Key services:
  - Amazon SQS
  - Amazon EC2
  - Amazon EC2 Auto Scaling
  - Amazon S3

- Common distractor services:
  - AWS Lambda
  - Amazon MQ
  - Amazon Elastic File System (EFS)

- Key signals:
  - up to 30 minutes to process
  - message queue
  - higher backlog during business hours
  - most cost-effective
  - media files

- Constraints:
  - Each processing job must support runtimes longer than AWS Lambda’s maximum execution timeout.
  - The solution should scale processing capacity with queue depth to reduce idle cost after hours.
  - Processed media storage should favor cost-effective object storage for this exam framing.

- Common traps:
  - Using Lambda to process each queued media job end-to-end.
  - Mixing Amazon MQ publishing with Amazon SQS metrics or consumption language in the same option.
  - Sending processed media to Amazon EFS when Amazon S3 fits object-style outputs and cost emphasis.

- Why traps are wrong:
  - Lambda as the media processor → violates the long-running job constraint because 30-minute work exceeds Lambda’s timeout limit.
  - Amazon MQ paired with SQS scaling or SQS pull wording → violates a coherent queue architecture constraint for the exam answer.
  - EFS for processed media in this stem → violates the cost-effective object-storage fit that Amazon S3 provides for media outputs.

- Pattern tags:
  - #sqs-backlog-scaling
  - #ec2-auto-scaling
  - #long-running-workers
  - #lambda-duration-limit
  - #s3-media-storage
