---
title: "Solution Concept: docToolchain Integration"
date: 2021-05-24
weight: 2
description: >
  API Management, Service Catalogue (aka API Developer Portal) <br/>
  [GitHub Repo](https://github.com/silverdonkey/spring-boot-openapi-doctoolchain)
---

{{% pageinfo %}}
Solution concept and PoC for docToolchain integration
{{% /pageinfo %}}

## Problem Description

### Requirements and Context

* SwaggerHub is the tool used for API design, development and documentation (e.g. Service Catalogue).
* Confluence is the single source of truth for any type of documentation
including software architecture documentation, design decisions, module specifications, developer how-tos, user guides, meeting notes, etc.
* Goal: follow the [Doc-as-Code](https://www.writethedocs.org/guide/docs-as-code/) approach for documentation
  * Use the same tools and workflows as development teams
* Goal: fully integrated API Management: connect Publisher Portal, Developer Portal and API Gateway

* General Requirements:
  1. Publish all API related documentation (interfaces, implementations, OpenAP definitions) to Confluence.
  2. Sources should be automatically synced with Confluence
  3. Define page structure and page hierarchy for each document type: Separate spaces for general software architecture, software module specs and API definitions
  4. Integration in the build and deployment pipelines

## Solution (PoC)
[docToolchain](http://doctoolchain.org/) integration in the software build pipeline

Solution Overview

{{< imgproc doctoolchain-build-pipeline-integration Resize "1200x" >}}
{{< /imgproc >}}
