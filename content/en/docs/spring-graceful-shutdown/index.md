---
title: "Demo: Spring Boot Graceful Shutdown"
date: 2020-06-15
weight: 4
description: >
  Demo some pitfalls with graceful shutdown configuration in Spring Boot microservices deployt as a Docker container. <br/>
  [GitHub Repo](https://github.com/silverdonkey/k8s-spring-boot-graceful-shutdown)
---

## Description
Disposability is one of the principals described in ["The Twelve Factor App"](https://12factor.net/disposablity/) and it is a best practice for constructing cloud-native applications. It states that service instances should be disposable. And in order to achieve this, **fast startup** to increase scalability and **graceful shutdowns** to leave the system in a correct state should be favored.

This demo-project aims to demonstrate some pitfalls with graceful shutdown configuration in Spring Boot microservice deployt as a Docker container.
