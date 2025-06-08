# 🏥 Java Spring Microservices - Clinic Management System

This project demonstrates a real-world microservices architecture using **Java** and **Spring Boot**. The system is modeled around a healthcare clinic, covering key functionalities like patient management, billing, authentication, analytics, and notifications.

## 🚀 Overview

This microservices-based project includes:

- **API Gateway** – Single entry point for all services
- **Authentication Service** – User registration/login with JWT tokens
- **Patient Service** – Handles patient records and publishes events
- **Billing Service** – Communicates with patient service via gRPC
- **Analytics Service** – Consumes Kafka events to perform analytics
- **Notification Service** – Listens to Kafka events and sends alerts
- **Integration Tests** – Tests for end-to-end scenarios
- **Infrastructure** – Docker-based setup with Kafka, PostgreSQL, etc.

---

## 🧰 Tech Stack

- **Java 17**
- **Spring Boot**
- **Spring Security + JWT**
- **gRPC** – Communication between services
- **Kafka** – Event streaming
- **PostgreSQL** – Database for each service
- **Docker & Docker Compose** – Container orchestration
- **Protocol Buffers** – For gRPC messages
- **JUnit/Testcontainers** – Integration testing

---

## 🧱 Architecture

```text
                       +------------------------+
                       |     API Gateway        |
                       +-----------+------------+
                                   |
      +----------------------------+-----------------------------+
      |                            |                             |
+-----v-----+            +---------v--------+           +--------v--------+
|  Auth     |            |   Patient        |           |    Billing       |
|  Service  |            |   Service        |<--gRPC--->|    Service       |
+-----------+            +--------+---------+           +-----------------+
                                  |
                             Kafka Event
                                  v
                    +---------------------------+
                    |  Notification Service     |
                    +---------------------------+
                                  |
                    +---------------------------+
                    |  Analytics Service        |
                    +---------------------------+
