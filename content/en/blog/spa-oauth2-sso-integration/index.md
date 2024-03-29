---
title: "Solution Concept: SSO for SPA using OAuth2 "
date: 2019-11-10
weight: 5
description: >
  Web Application Security, Cloud Security, SSO, Active Directory, OAuth2, SPA <br/>
---

## Problem Description

### Requirements and Context

1. Users and roles management: define roles and rights, including the ability to maintain users according to the company's policies.
2. Authentication: provide seamless login (Single-Sign-On) functionality to the SPA for Data Developers, Data Managers and other SMEs.
3. Authorization: only authorized users should be allowed to access the application's functionality according to the specified role and granted privileges(Principle of Least Privilege)
4. Architecture decision for
    * Identity and Access Management (Keycloak vs company's Active Directory)
    * Authentication and Authorization protocols (SAML, OpenID Connect, OAuth2)

## Solution

### System Architecture (Component Diagram and Deployment View)

{{< imgproc architecture-overview-components-deployment-view Resize "1200x" >}}
{{< /imgproc >}}

### Single-Sign-On Integration using OAuth2-Code-Flow (Sequence Diagram)

{{< imgproc sso-oauth2-code-flow-sequence-diagram Resize "1200x" >}}
{{< /imgproc >}}
