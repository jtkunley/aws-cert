# Amazon EC2

## What it is
- Virtual machines: pick instance type, AMI, full OS control.

## Personal notes / memory hooks
- You patch and scale the VM.
- Stem says **serverless** → EC2 is usually wrong.
- **Practice (serverless Q):** legacy baseline = EC2 **multi-region**; target = serverless compute/data.

## When to use it
- Lift-and-shift, custom kernel, instance store, GPU, license tied to dedicated hardware.
- Steady 24/7 load where Reserved Instances win on cost.

## When NOT to use it
- Stem requires **serverless** or zero server ops → Fargate/Lambda/managed.

## Exam clues
- Keywords: instance, AMI, SSH, placement group, Dedicated Host.
- **Multi-region EC2** before “modernize” → legacy baseline, not serverless.
- **Practice (serverless Q):** e-commerce web/mobile on EC2; sales, inventory, orders, shipping.

## Common distractors
- ASG + EC2 sold as **serverless** → false.
- **Practice (serverless Q):** answers must move to Fargate/managed, not grow EC2.

## Architecture patterns
- ALB → ASG web tier; bastion; batch on fixed fleet; hybrid via DX/VPN.
- **Practice (serverless Q):** same domain split → microservices in answer choices.

## Comparison with nearby services
- **EC2:** you run the VM.
- **Fargate:** no worker-node ops for containers.
- **Lambda:** short invocations, not arbitrary long-lived servers.
- **Elastic Beanstalk:** PaaS over EC2.

## Example scenarios
- Monolith on Linux; licensed software; GPU.
- **Practice (serverless Q):** EC2 apps + **MySQL + PostgreSQL on EC2** (OLTP + analytics DB on boxes).
- **Practice (serverless Q):** tie to pattern [Legacy EC2 data tier](../patterns/legacy-ec2-data-tier.md).

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)
