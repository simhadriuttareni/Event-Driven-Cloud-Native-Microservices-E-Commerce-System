# Event-Driven Microservices Platform

A production-style event-driven microservices platform built using Spring Boot, Apache Kafka, Redis, and Docker, focusing on asynchronous communication, fault tolerance, distributed processing, and scalable backend architecture.

This project demonstrates real-world backend engineering practices used in modern distributed systems where services communicate through events rather than direct synchronous calls.

---

## 🚀 Architecture Overview

The system follows an event-driven microservices architecture where business workflows are coordinated through Kafka events.

### Core Services

* **Order Service** – Creates and manages customer orders
* **Inventory Service** – Validates and updates product stock
* **Payment Service** – Handles payment processing and transaction status
* **Apache Kafka** – Event streaming platform for asynchronous communication
* **Redis** – Distributed caching layer for frequently accessed data
* **Docker** – Containerized deployment for consistency across environments

---

## 🧱 Tech Stack

* Java 17
* Spring Boot 3
* Spring Data JPA
* Apache Kafka
* Redis
* PostgreSQL
* Docker
* Maven
* Git & GitHub

---

## 🔄 Event-Driven Workflow

### Order Placement Flow

1. Customer places an order.
2. Order Service publishes an `OrderCreated` event.
3. Inventory Service consumes the event and validates stock availability.
4. Inventory Service publishes an `InventoryReserved` event.
5. Payment Service consumes the event and processes payment.
6. Payment Service publishes either:

   * `PaymentCompleted`
   * `PaymentFailed`
7. Order Service updates final order status accordingly.

This asynchronous workflow removes tight coupling between services and improves scalability.

---

## ⚡ Kafka Event Architecture

### Published Events

* OrderCreated
* InventoryReserved
* InventoryRejected
* PaymentCompleted
* PaymentFailed

### Kafka Features Implemented

* Event Producers
* Event Consumers
* Consumer Groups
* Topic-Based Messaging
* Event Serialization
* Asynchronous Processing

---

## 🛡 Fault Tolerance Features

### Retry Mechanism

Implemented retry handling for transient failures during event consumption.

### Idempotency Handling

Duplicate events are safely ignored to prevent:

* Duplicate payments
* Duplicate inventory updates
* Inconsistent order states

### Reliable Event Processing

Designed to ensure eventual consistency across distributed services.

---

## ⚡ Redis Caching

Redis is used to improve API performance by caching frequently accessed data such as:

* Product information
* Inventory availability
* Order lookup results

### Benefits

* Reduced database load
* Faster API response times
* Improved scalability

---

## 🐳 Docker Containerization

All services are containerized using Docker.

### Benefits

* Consistent deployment environments
* Simplified service startup
* Easy scaling and orchestration readiness
* Local development parity with production

---

## 🗄 Database Design

### Database-per-Service Pattern

Each microservice maintains its own data ownership.

#### Order Database

* Orders
* Order Status

#### Inventory Database

* Products
* Stock Quantities

#### Payment Database

* Transactions
* Payment Status

### Persistence Layer

* Spring Data JPA
* Hibernate ORM
* PostgreSQL

---

## ⚙️ How to Run the Project

### Prerequisites

* Java 17
* Maven
* Docker
* PostgreSQL
* Apache Kafka
* Redis

### Start Infrastructure

```bash
docker-compose up -d
```

### Start Services

```bash
cd order-service
mvn spring-boot:run
```

```bash
cd inventory-service
mvn spring-boot:run
```

```bash
cd payment-service
mvn spring-boot:run
```

---

## 🔍 Sample Event Flow

```text
Order Created
      │
      ▼
Kafka Topic
      │
      ▼
Inventory Service
      │
      ▼
Inventory Reserved
      │
      ▼
Kafka Topic
      │
      ▼
Payment Service
      │
      ▼
Payment Completed
      │
      ▼
Order Status Updated
```

---

## 🧠 Key Engineering Highlights

* Event-Driven Architecture
* Apache Kafka Messaging
* Distributed Microservices Design
* Retry Mechanisms
* Idempotent Event Processing
* Eventual Consistency Pattern
* Redis Caching
* Docker Containerization
* Database-per-Service Architecture
* Production-Ready Project Structure

---

## 📌 Future Enhancements

* API Gateway
* Eureka Service Discovery
* Spring Cloud Config
* Circuit Breaker (Resilience4j)
* Distributed Tracing (Zipkin)
* JWT Authentication
* Kubernetes Deployment
* AWS Deployment Pipeline
* Saga Pattern Implementation

---

## 👨‍💻 Author

**Simhadri Uttareni**
Backend Engineer | Java | Spring Boot | Microservices | Kafka

GitHub: https://github.com/simhadriuttareni

---

⭐ If you find this project useful, feel free to star the repository.
