---
title: "Solution Concept: Mastering the journey to the Cloud"
date: 2023-02-14
weight: 1
description: >
  Cloud migration and modernization strategies, Cloud native<br/>
---

{{% pageinfo %}}
Solution concept and PoC for Cloud Migration
{{% /pageinfo %}}

## Project Context and Goals
- Establish a DevOps workflow and best practices for
  - Migration (and modernization) of existing Web apps to the Cloud
  - Development of new Web apps for the Cloud - "Cloud first approach"
- Establish an end-to-end DevOps environment that supports Continuous Integration/Continuous Deployment (CI/CD)
  - CI/CD Pipeline to build, test and deploy in the Cloud
  - Evaluate GitHub Actions, AWS CodeBuild
  - Evaluate Rolling Deployment vs Blue-Green Deployment
- Use Cloud native technologies and tools
  - no vendor lock-in
- Proof of concept

> What is Cloud native?
>
> Cloud native technologies empower organizations bo build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds.
> Containers, service meshes, microservices, immutable infrastructure, and decllarative APIs exemplify this approach.
>
> These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.*
>
> Source: [Cloud Native Computing Foundation](https://www.cncf.io/)

## Cloud Migration Strategies

{{< imgproc cloud-migration-strategies Resize "1200x" >}}
Strategies for migrating legacy (monolitic) apps
{{< /imgproc >}}

1. Strategy: Cloud Ready Migration (aka "Lift-and-Shift" or "Rehost")
  - No code changes
  - IaaS model
  - Cloud providers usually provide migration tools like the [AWS MigrationHub](<https://aws.amazon.com/de/migration-hub/>) or [Azure Migrate](https://azure.microsoft.com/de-de/products/azure-migrate/#product-overview)
  - Quick and therefore cheap, yet does not levareges most of the benefits of Cloud Computing
2. Strategy: Cloud Optimized Migration
  - Requires minimal code changes
  - PaaS model
  - Containerization of the App and deployment to a Container Orchestration
  - Decomposition into Microservices
    - Data-Driven Microservices (CRUD)
  - Consuming Cloud managed services like Databases, Caching, Monitoring, Message Queues
  - Deployment optimizations that enable key cloud services without changing the core architecture
  - Higher costs and overhead, yet better scalability and performance, levareges most of the benefits of Cloud Computing
3. Strategy: Cloud Native Migration
  - Requires rearchitecting and rewriting code
  - Microservices Architecture (Decomposition into Microservices and Containerization)
    - Data-Driven Microservices (CRUD)
    - Domain-Driven Microservices (CQRS, Event Sourcing)
  - Serverless Architecture
  - Event-Driven Architecture
  - API-Management, API-Gateway
  - Highest costs, yet future-proof investment (fine-grained scalability, improved system resiliency, performance and operations), all benefits of Cloud Computing

## Proof of Concept Goals
- Migrate an existing Web-based application to the Cloud using the 2. Migration Strategy - "Cloud Optimized Migration"
- Produce a cloud native reference application on [AWS Cloud](https://aws.amazon.com/) to showcase using Laravel, Docker, GitHub, Cloud managed services and CI/CD pipeline to build a simplistic *minimal* php based application.

### Migration of a (monolitic) Web App
Architecture Overview
{{< imgproc monolitic-web-app-architecture Resize "1200x" >}}
Monolitic Web App Architecture, deployt on-premises
{{< /imgproc >}}

Cloud Optimized Architecture - Development/Staging Environment
{{< imgproc cloud-opt-web-app-architecture-dev Resize "1200x" >}}
Cloud Optimized Web App Architecture (local develepment and staging)<br />
*Service Aggregator Pattern / API Gateway
{{< /imgproc >}}


Cloud Optimized Architecture - Production Environment
{{< imgproc cloud-opt-web-app-architecture-prod Resize "1200x" >}}
Cloud Optimized Web App Architecture (production)<br />
*Service Aggregator Pattern / API Gateway
{{< /imgproc >}}

---

### Summary and Outlook
How would a Cloud-native architecture look like? Here are some recommendations.

{{< imgproc cloud-native-web-app-architecture Resize "1200x" >}}
Cloud-native Web App Architecture<br />
Microservices, Event-Driven Architecture, API Gateway
{{< /imgproc >}}

- Topics not touched: Security, backup services, monitoring
- Should be required in the future that multiple front-end clients must be supported (SPA, mobile clients) and/or exposing many complex APIs
  - Introduce an API Gateway or even API Management
- If appropriate - move from "single/shared database" model to "share nothing" model where each microservice owns its data
- Event Driven Architecture: use events for communication between microservices, in a decoupled, reliable and asynchronous manner
  - For local development RabbitMQ can be used as a Message Broker
  - In the AWS Cloud use a fully managed integration message broker - [Amazon MQ](https://aws.amazon.com/de/amazon-mq/) (supports Active MQ and RabbitMQ)
- Serverless: consider using a single function where sufficient (not customer-facing, single operation) instead of developing and maintaining a full microservice
- Configure centralized logging - CloudWatch

### Reference Web App

TODO:

- add screenshot of the app
- add link to the GitHub repo

#### Basic Features

- Sign in and out
- Registration flow
- Password reset flows
- Review and Edit user's profile

#### Non-Functional Requirements of the Reference App

- High availability
- (Optional) Scale out and in automatically to meet increased traffic
- Support an agile development process, including CI/CD
- For simplicity, support *only* traditional Web front ends (no SPA, no mobile clients)
- The design should support
  - cross-platform development (no platform lock-in) and
  - cross-platform hosting (no cloud vendor lock-in)

#### Evaluated and leveraged technologies and tools

- CI/CD: GitHub-Actions, CodeBuild
- Centralized configuration: S3 Service (storage, configuration)
- Secure Credentials: Secrets Manager (SSM)
- Container Registry: private registry (S3-based) / ECR
- Container Orchestrator and Clustering - EKS/ECS
- Load Balancing (ELB)
- Data stores: MySql/MariaDB (RDS)
- Caching, Session management, Queueing (MemoryDB Cluster for Redis)

#### DevOps Workflow for Dockerized Web Apps

Local Development Workflow
{{< imgproc local-dev-workflow-docker Resize "1200x" >}}
Local Dev Workflow
{{< /imgproc >}}

DevOps Workflow on AWS
{{< imgproc devops-workflow-cloud Resize "1200x" >}}
DevOps Workflow
{{< /imgproc >}}
