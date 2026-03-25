# Amazon EC2

## What it is
Virtual servers in the cloud: you choose instance types, AMIs, and run full OS-level control over the machine.

## When to use it
Lift-and-shift, strict OS/kernel needs, software not supported on managed platforms, long-running steady workloads where reserved capacity is cheaper, or when you need instance store or very specific hardware.

## When NOT to use it
When the exam asks for **serverless**, minimal ops, or automatic scale-to-zero; prefer Fargate, Lambda, or managed services unless EC2 is explicitly required.

## Exam clues
“Instances,” “SSH,” “AMI,” “instance store,” “Dedicated Hosts,” “placement groups,” legacy apps on “servers.” Stems that start on **EC2 across multiple regions** before modernization → baseline is legacy scale-out, not serverless.

## Common distractors
Choosing EC2 + ASG when the requirement is **serverless** or **no server management**; confusing EC2 with container hosts when Fargate removes that layer.

## Architecture patterns
Multi-tier web apps, bastion hosts, batch workers on fixed fleets, hybrid with on-prem via Direct Connect/VPN.

## Comparison with nearby services
**EC2** = you manage the VM; **Fargate** = no EC2 management for containers; **Lambda** = function-level, short executions; **Elastic Beanstalk** = PaaS abstraction over EC2.

## Example scenarios
Legacy monolith on Linux, license-bound software, GPU workloads, custom kernel modules.

## Links to related questions
- [Q: Serverless modernization & multi-cloud](../questions/q-serverless-modernization-multicloud.md)

## Personal notes / memory hooks
EC2 = “I own the box.” If the stem screams serverless, EC2 is usually wrong.
