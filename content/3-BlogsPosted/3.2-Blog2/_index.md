---
title: "Blog 2"
date: 2026-10-12
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

# AWS LAMBDA WEB FUNCTIONS: RUN SERVERLESS HTTP WEB APPS DIRECTLY

AWS recently introduced **AWS Lambda Web Functions**, a new serverless compute model that allows standard HTTP web applications and backend APIs to run directly on AWS Lambda without rewriting code into traditional event handlers or relying on adapter layers. Alongside this launch, traditional event-driven Lambda functions are renamed **Lambda Event Functions** (a naming distinction only, requiring zero changes to existing workloads), allowing developers to keep a familiar web-server development experience on serverless infrastructure.

Key points to know:

- **Native support for popular web frameworks:** Code runs as a standard web server listening directly on an HTTP port (launching with the Node.js 24 runtime on Arm64 architecture), allowing immediate use of Express, Hono, Fastify, Next.js, or React Router without wrapper libraries or complex translation layers.
- **Concurrent request handling and reduced cold starts:** Unlike the single-request event execution model, a warm Web Function execution environment (provisioned with 2 vCPUs and 2 GB of memory at launch) can process multiple HTTP requests concurrently, significantly reducing cold starts.
- **Cost efficiency with Active Compute billing:** Instead of paying for idle I/O wait time (such as waiting on database queries or downstream API calls), you are billed only for actual active CPU processing time, separated from memory and request charges.
- **Native HTTP streaming support:** Enables streaming partial responses to clients as soon as chunks are ready rather than buffering the entire payload—ideal for real-time interfaces and Generative AI workloads.
- **Clear three-part resource model:** Structured around **Web Function** (core resource holding name and settings), **Revision** (immutable snapshot of code and configuration enabling fast rollbacks), and **Endpoint** (network entry point providing a unique public HTTPS domain, authentication settings, and traffic routing rules).
- **Multi-Region routing and Amazon VPC integration:** Supports deploying once across multiple AWS Regions to automatically route traffic to the Region closest to users for lower latency, while integrating natively with Amazon VPC to communicate securely with databases and internal resources.

This capability is particularly well suited for teams building modern web applications and backend APIs who want the simplicity of standard web frameworks alongside AWS Lambda's automatic scaling, zero server management, and active-compute pricing model.

**Image:**

![AWS Lambda Web Functions Architecture](/fcj-workshop-template/images/3-Blog/Blog02.png)

**Link**
- 
