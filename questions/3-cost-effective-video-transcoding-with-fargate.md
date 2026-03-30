# 3. Cost-effective video transcoding with Fargate

## Original question
A global streaming company uses a Java application on an Amazon EC2 instance to transcode videos for its platform. The application starts processing the videos to different resolutions every time they are uploaded to an Amazon S3 bucket. It takes approximately 40 minutes to transcode each video. The application keeps track of the transcoded videos and only process each file once.

Upon reviewing Amazon CloudWatch metrics, a solutions architect noted that the EC2 instance is idle for 35% of the time on average. The solutions architect is required to make the workload highly available and scalable, and reduce management overhead.

What should the architect recommend for the MOST cost-effective solution?

**Option A:** Create an Amazon Simple Queue Service (Amazon SQS) queue and configure Amazon S3 to send event notifications to the SQS queue. Set up an EC2 Auto Scaling group with a minimum size of one instance. Modify the video transcoding application to continuously poll the SQS queue, and start transcoding the files in S3 that the SQS message links to.

**Option B:** Create an equivalent script of the application workflow and deploy it as an AWS Lambda function. Use an S3 event notification to start the processing when a new video is uploaded.

**Option C:** Build a container image out of the video transcoding application. Deploy and run the container image on Amazon Elastic Container Service (Amazon ECS) on AWS Fargate. Create an AWS Lambda function that calls the Fargate RunTask API operation when the S3 bucket receives the file upload event notification.

**Option D:** Build a container image out of the video transcoding application. Deploy and run the container image on an EC2 instance. Configure the container to continuously poll the S3 bucket for new videos and start to transcode the files.

## Correct answer
- **Option C** is the best fit.
- It runs long transcoding jobs as on-demand container tasks on **Amazon ECS with AWS Fargate**, then triggers each task from **Amazon S3** upload events through **AWS Lambda**.

## Why it is correct
- The workload runs for about **40 minutes per video**, which fits container tasks better than a single **AWS Lambda** invocation.
- **Fargate** removes EC2 worker management, so operations are lower than instance-based designs.
- Event-driven task launch from **S3** means compute runs when new files arrive, which reduces idle capacity cost.
- ECS services and tasks can scale horizontally as upload volume changes, supporting high availability and scalability.

## Why the other options are wrong
- **Option A:** This improves decoupling with **SQS**, but it still keeps an **EC2 Auto Scaling** baseline with a minimum instance and continuous polling, so management overhead and idle cost remain higher than on-demand Fargate tasks.
- **Option B:** A single **AWS Lambda** invocation cannot run for 40 minutes, so this does not satisfy the runtime requirement without a different architecture than the option states.
- **Option D:** Containerizing on **EC2** still keeps instance management and continuous polling, so it does not reduce management overhead or idle cost as effectively as event-triggered Fargate tasks.

## Trap type
- **Runtime limit mismatch:** Choosing Lambda for a per-item job that runs longer than the Lambda maximum duration.
- **Partial modernization:** Keeping EC2 and polling after adding queues or containers.
- **Wrong cost model:** Paying for always-on workers when work is bursty and event-driven.

## Services involved
- [Amazon EC2](../services/amazon-ec2.md)
- [EC2 Auto Scaling](../services/amazon-ec2-auto-scaling.md)
- [Amazon S3](../services/amazon-s3.md)
- [Amazon SQS](../services/amazon-sqs.md)
- [AWS Lambda](../services/aws-lambda.md)
- [Amazon ECS](../services/amazon-ecs.md)
- [AWS Fargate](../services/aws-fargate.md)

## Pattern tags
- [Serverless architecture](../patterns/serverless-architecture.md)
- [Event-driven architecture](../patterns/event-driven-architecture.md)
- [Legacy EC2 data tier](../patterns/legacy-ec2-data-tier.md)
- [Long-running container tasks](../patterns/long-running-container-tasks.md)
- [S3 event-triggered processing](../patterns/s3-event-triggered-processing.md)

## Question Seed

- Scenario summary: A video platform currently transcodes uploads on one EC2-based Java worker, each item takes about 40 minutes, and metrics show meaningful idle time; the architecture must become more available, scalable, and cheaper to run.
- Primary driver: The per-video runtime is too long for Lambda and the workload should avoid always-on EC2 workers.
- Decision focus: Select an event-driven compute model that launches long-running jobs on demand with low operational overhead.
- Correct answer pattern: S3 upload events trigger orchestration that starts serverless container tasks for each file, so compute scales per job and stops when work is done.

- Key services:
  - Amazon S3
  - AWS Lambda
  - Amazon ECS
  - AWS Fargate

- Common distractor services:
  - Amazon EC2
  - EC2 Auto Scaling groups
  - Amazon SQS
  - AWS Lambda (as the main transcoder)

- Key signals:
  - 40-minute processing time
  - uploaded to Amazon S3
  - EC2 idle 35 percent
  - high availability and scalability
  - reduce management overhead
  - most cost-effective

- Constraints:
  - The processing unit must support long-running jobs that exceed Lambda duration limits.
  - The design should avoid continuous polling workers and minimize always-on compute cost.
  - The architecture should scale automatically with upload events and keep operations low.

- Common traps:
  - Using Lambda directly for full transcoding jobs.
  - Keeping EC2 workers as the main execution layer with polling.
  - Adding queues but still requiring a minimum always-on instance fleet.

- Why traps are wrong:
  - Lambda-only transcoding → violates the long-running processing constraint because 40-minute jobs exceed Lambda runtime limits.
  - EC2 polling workers → violates the low-operations and cost-efficiency constraints by keeping managed instances and idle capacity.
  - SQS plus minimum EC2 Auto Scaling baseline → violates the on-demand compute constraint because baseline instances still run when demand is low.

- Pattern tags:
  - #event-driven-processing
  - #serverless-containers
  - #long-running-jobs
  - #ec2-to-fargate-modernization
  - #cost-efficient-elastic-compute
