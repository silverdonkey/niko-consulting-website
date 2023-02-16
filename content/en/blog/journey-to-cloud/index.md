---
title: "Solution Concept: Mastering the journey to the Cloud"
date: 2023-02-14
weight: 1
description: >
  Cloud migration and modernization strategies<br/>
---

{{% pageinfo %}}
Solution concept and PoC for Cloud Migration
{{% /pageinfo %}}

## Project Context and Goals
- Establish a workflow and best practices for
  - Migration (and modernization) of existing Web apps to the Cloud
  - Development of new Web apps for the Cloud - "Cloud first"
- Code base and version control (GitHub)
- Use Docker for local development and in production (Containerization)
- Automate build and deployment: CI/CD Pipeline to build, test and deploy in the Cloud (GitHub Actions, AWS CodeBuild)
  - Evaluate Rolling Deployment vs Blue-Green Deployment
- Use Cloud native technologies and tools
- No vendor lock-in

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
- Produce a cloud-native reference application on [AWS Cloud](https://aws.amazon.com/) to showcase using Laravel, Docker, GitHub and Cloud managed services to build a simplistic *minimal* php based application.

---
### Existing Monolitic Web App
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
### Reference Web App
TODO:
- add screenshot of the app
- add link to the GitHub repo
#### Basic Features
- Sign in
- Sign out
- Register an account
- Review and Edit user's profile

#### Non-Functional Requirements of the Reference App
- High avalability
- (Optional) Scale out and in automatically to meet increased traffic
- Support an agile development process, including CI/CD
- For simplicity: support *only* traditional Web front ends (no SPA, no mobile clients)
- The design should support cross-platform development and cross-platform hosting (no cloud vendor lock-in)

#### Evaluated and leveraged technologies and tools
- GitHub-Actions, CodeBuild
- S3 Service (storage, configuration, container images)
- Secrets Manager (SSM)
- Container Registry - private registry / ECR
- Container Orchestrator and Clustering - EKS/ECS
- Load Balancing (ELB)
- Data stores: MySql/MariaDB (RDS)
- Caching, Session management, Queueing (MemoryDB Cluster for Redis)

### Reference GitHub Repo
