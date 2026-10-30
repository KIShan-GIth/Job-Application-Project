# Cloud-Native Microservices Job Application Platform

An enterprise-grade, distributed microservices platform built using **Java**, **Spring Boot**, **Spring Cloud**, **Docker**, and **Kubernetes**. The application evolved from a monolithic architecture into a fully decoupled, fault-tolerant, and event-driven microservices system.

---

## 🏗️ Architecture Overview

The platform isolates domain concerns into dedicated services running independent PostgreSQL instances, communicating seamlessly via service discovery, dynamic API routing, and asynchronous messaging queues.

```text
                               ┌───────────────────────────┐
                               │   Spring Cloud Gateway    │ (API Gateway: Port 8084)
                               └─────────────┬─────────────┘
                                             │
               ┌─────────────────────────────┼─────────────────────────────┐
               │                             │                             │
               ▼                             ▼                             ▼
    ┌────────────────────┐        ┌────────────────────┐        ┌────────────────────┐
    │    Job Service     │        │  Company Service   │        │   Review Service   │
    │  (Spring Boot/JPA) │        │  (Spring Boot/JPA) │        │  (Spring Boot/JPA) │
    └──────────┬─────────┘        └──────────┬─────────┘        └──────────┬─────────┘
               │                             │                             │
               ▼                             ▼                             ▼
    ┌────────────────────┐        ┌────────────────────┐        ┌────────────────────┐
    │  Job DB (Postgres) │        │ Company DB(Postgres│        │ Review DB(Postgres)│
    └────────────────────┘        └────────────────────┘        └────────────────────┘
