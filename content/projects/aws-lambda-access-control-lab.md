+++
title = "AWS Lambda Access Control Lab"
date = 2026-03-14T10:00:00-05:00
draft = false
description = "A serverless showcase comparing a public Lambda Function URL, a shared-secret Lambda gate, and an API Gateway IAM-authorized path to show how the trust boundary changes."
summary = "A technical showcase of the same Lambda workload exposed through three serverless access patterns, highlighting how the security boundary shifts from a public function URL to API Gateway with IAM authorization."
image = "/images/projects/aws-lambda-access-control-lab.svg"
hideFeaturedImage = true
showInHome = true
toc = true
tags = ["AWS", "Lambda", "API Gateway", "IAM", "Serverless", "Security"]
badges = ["AWS Lambda", "Function URL", "API Gateway", "IAM", "Node.js"]
[[links]]
icon = "fab fa-github"
url = "https://github.com/acanave/aws-lambda-access-control-lab"
+++

This showcase is based on the lab repository at [acanave/aws-lambda-access-control-lab](https://github.com/acanave/aws-lambda-access-control-lab). The implementation keeps the Lambda response intentionally simple so the real comparison stays focused on **how the function is exposed and where access control is enforced**.

## Why this project is worth showcasing

Many Lambda demos stop after proving that a handler executes. This lab goes one level deeper and compares three ways to expose the same function:

| Version | Front Door | Access Model | What it demonstrates |
| --- | --- | --- | --- |
| 1 | Lambda Function URL | Public HTTPS endpoint | Fastest path to exposure, but no identity boundary |
| 2 | Lambda Function URL | Shared secret checked in the handler | Lightweight gating inside application code |
| 3 | API Gateway HTTP API | IAM authorization with SigV4 | Access control enforced before Lambda runs |

That progression makes the repo useful as a portfolio piece because it shows architectural judgment, not just Lambda syntax.

## Architecture progression

![Overview diagram for the Lambda access control lab](/images/projects/aws-lambda-access-control-lab.svg)

The same workload sits behind three different entry paths:

1. A direct Lambda Function URL for a fully public endpoint.
2. A second Lambda Function URL path that validates an `x-api-key` shared secret inside the function.
3. An API Gateway HTTP API in front of Lambda with IAM authorization at the gateway layer.

The function output stays nearly the same across versions. The real change is the security posture around the function.

## What changes from one version to the next

### Version 1: Public function URL

This is the thinnest architecture. TLS protects the transport, but anyone with the URL can invoke the function. That makes it useful for demos or intentionally public content, but weak for anything that needs caller identity or enforceable permissions.

### Version 2: Header-based shared secret

This version adds a light control by validating a shared secret in the request header. It is better than a fully open endpoint, but the security decision still lives inside application code. The function now owns both business logic and request validation.

### Version 3: API Gateway with IAM authorization

This is the strongest pattern in the lab. API Gateway validates a SigV4-signed request and checks IAM authorization before Lambda is invoked. Unauthorized traffic is rejected at the edge, which creates a cleaner separation between access enforcement and compute.

## Trust boundary shift

![Trust boundary comparison diagram for the Lambda access control lab](/images/projects/aws-lambda-trust-boundary.svg)

The most important lesson in the repo is not the HTML response or the handler code. It is the movement of the trust boundary:

- In version 1, Lambda is the public edge.
- In version 2, Lambda is still public and also responsible for request validation.
- In version 3, the trust boundary moves in front of Lambda and becomes infrastructure-enforced.

That is the kind of serverless design decision that matters in real environments, especially when moving from an internal proof of concept to a production-facing service.

## Why this is a strong portfolio artifact

- It compares three realistic exposure patterns against the same workload, which makes the tradeoffs easy to see.
- It shows security thinking at the architecture boundary, not just inside the function body.
- It demonstrates where simple controls are acceptable and where stronger AWS-native enforcement is the better choice.
- It creates a clear narrative for discussions about Lambda, API Gateway, IAM, and trust boundaries in interviews or technical reviews.

## Repository

- GitHub: [aws-lambda-access-control-lab](https://github.com/acanave/aws-lambda-access-control-lab)
- README: [Project overview and architecture notes](https://github.com/acanave/aws-lambda-access-control-lab/blob/main/README.md)

## Key takeaway

The core lesson from this lab is that serverless security is often defined less by the handler implementation and more by the access layer in front of it. The function can stay almost identical while the operational risk and control model change significantly.
