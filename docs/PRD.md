# System Design Playground

## Product Requirements Document (PRD)

**Version:** 0.1
**Status:** Updated — Technology Direction Confirmed
**Product Type:** Interactive System Design Learning and Simulation Platform

---

## 1. Product Overview

System Design Playground is an interactive platform that helps software engineering students and developers learn, practice and understand system design through hands-on experimentation.

Users can construct system architectures, configure components, simulate workloads, introduce failures and observe the consequences of their architectural decisions.

The platform consists of three primary modes:

1. Learn
2. Build
3. Interview

The central objective is to connect theoretical system design knowledge with practical architectural decision-making.

## 2. Problem Statement

Traditional system design learning often relies on theoretical explanations, static diagrams and architecture walkthroughs.

These methods do not always allow learners to experiment with architecture or understand the consequences of changing individual components.

Examples of questions the platform should help users investigate:

- What happens when a database becomes a bottleneck?
- How does adding Redis affect database traffic?
- What happens when an application server fails?
- How does a message queue handle traffic spikes?
- What trade-offs are introduced by database replication?

System Design Playground addresses this gap through interactive architecture construction and simulation.

## 3. Target Users

### Primary Users

- Computer science students.
- Fresh graduates preparing for software engineering interviews.
- Developers learning backend engineering and distributed systems.

### Secondary Users

- Software engineers exploring architectural alternatives.
- Technical interview candidates practising system design.

## 4. Product Modes

### 4.1 Learn Mode

**Purpose:** Help users understand system design concepts and architectural components.

Each learning topic should cover:

- Definition and introduction.
- Why the concept is required.
- Internal working.
- Practical use cases.
- Advantages and disadvantages.
- Architectural trade-offs.
- Real-world examples.
- Common interview questions.

Interactive mini-experiments and quizzes can be introduced to connect theory with practice.

### 4.2 Build Mode

**Purpose:** Allow users to construct architectures and experiment with design decisions.

Two experiences are planned.

**Guided Challenges**

Users receive a system design problem with requirements, constraints and optional hints. They construct an architecture, configure components and run simulations.

**Free Architecture Builder**

Users start with a blank canvas and independently construct an architecture using the component library.

Core capabilities:

- Add and remove architecture components.
- Connect components.
- Configure component properties.
- Generate simulated workloads.
- Execute simulations.
- Introduce failures.
- Observe performance metrics.
- Compare architecture versions.
- Understand the consequences of architectural changes.

The initial implementation will prioritise guided challenges, followed by free-form architecture building.

### 4.3 Interview Mode

**Purpose:** Simulate a system design interview.

Users receive an interview question and independently design the proposed system.

Expected activities:

1. Clarify requirements.
2. Identify functional requirements.
3. Identify non-functional requirements.
4. Estimate traffic and system scale.
5. Identify APIs and data models.
6. Construct the high-level architecture.
7. Identify bottlenecks.
8. Discuss failure handling.
9. Explain design decisions and trade-offs.

The platform should evaluate both architecture quality and the reasoning behind design decisions.

## 5. Architecture Component Library

The platform should eventually support components across these categories.

### Networking and Traffic Management

- API Gateway
- Load Balancer
- DNS
- CDN
- Reverse Proxy
- Rate Limiter
- Firewall

### Compute and Application Layer

- Application Server
- Web Server
- Microservice
- Background Worker
- Serverless Function
- Container

### Databases and Storage

- SQL Database
- NoSQL Database
- Cache
- Read Replica
- Object Storage
- Database Sharding
- Database Partitioning
- Connection Pool

### Messaging and Asynchronous Processing

- Message Queue
- Publish/Subscribe
- Event Broker
- Event Streaming
- Dead Letter Queue
- Consumer Groups

### Reliability and Distributed Systems

- Circuit Breaker
- Retry Mechanism
- Timeout
- Health Check
- Service Discovery
- Failover
- Distributed Lock
- Idempotency

### Observability and Security

- Logging
- Metrics
- Distributed Tracing
- Authentication
- Authorization
- Secrets Management

Each component must have defined behaviour, configurable properties, inputs, outputs and failure conditions.

## 6. Simulation Requirements

The simulation engine is a central platform capability.

It should allow users to:

- Generate configurable request workloads.
- Route requests between components.
- Model component processing times and capacities.
- Simulate queues and asynchronous processing.
- Model cache hits and misses.
- Simulate database operations.
- Introduce failures and latency spikes.
- Observe the propagation of failures.
- Compare different architectural configurations.

The initial implementation will use discrete-event simulation with virtual time and event scheduling.

### Initial Metrics

- Average latency.
- p50, p95 and p99 latency.
- Throughput.
- Error rate.
- Queue depth.
- Queue lag.
- Resource utilisation.
- Cache hit ratio.
- Estimated infrastructure cost.

Simulation results must be calculated from configured workloads and component behaviour. Results must not be hardcoded.

## 7. Architecture Evaluation

The platform should evaluate architectures against defined requirements and constraints.

Evaluation dimensions:

- Performance.
- Scalability.
- Availability.
- Reliability.
- Consistency.
- Infrastructure cost.
- Operational complexity.

The platform should identify bottlenecks, explain trade-offs and suggest possible improvements.

It should not claim that one architecture is universally optimal. Evaluation must consider the specific workload and requirements.

## 8. Initial Case Studies

### Foundational Systems

- URL Shortener.
- Rate Limiter.
- Pastebin.
- Notification System.

### Intermediate Systems

- Chat Application.
- News Feed.
- File Storage.
- Video Streaming.

### Advanced Systems

- Food Delivery Platform.
- Ride-Hailing Platform.
- E-commerce Platform.
- Ticket Booking System.

**First validation system:** URL Shortener.

**First major capstone system:** Food Delivery Platform inspired by systems such as Swiggy and Zomato.

These are educational case studies, not claims about the actual internal architecture of those companies.

## 9. Technology Stack

### Backend

- **Language:** Java.
- **Framework:** Spring Boot.
- **API:** Spring Web / REST APIs.
- **Validation:** Jakarta Bean Validation.
- **Persistence:** Spring Data JPA.
- **Database:** PostgreSQL.
- **Database Migrations:** Flyway.

### Simulation Engine

- Java-based simulation engine.
- Discrete-event simulation.
- Virtual clock.
- Priority queue-based event scheduling.
- Independent core simulation module.

The simulation engine should not depend directly on Spring Boot, HTTP controllers or database persistence. It must be independently testable.

### Frontend

- React.
- React Flow for architecture graph visualisation.

### Testing

- JUnit 5.
- Mockito.
- Spring Boot Test.
- Integration testing.

### Development and Infrastructure

- Git and GitHub.
- Maven.
- Docker.
- Docker Compose.

### Architectural Approach

The initial backend will use a **modular monolithic architecture**.

We will not introduce microservices prematurely.

The simulation engine will remain a separate module with clearly defined interfaces. Spring Boot will coordinate application operations and expose APIs to the frontend.

## 10. Initial Backend Module Structure

The proposed logical modules are:

1. Architecture Management
2. Simulation Engine
3. Component Behaviour Models
4. Workload Generation
5. Failure Simulation
6. Metrics Calculation
7. Architecture Evaluation
8. Learning Content
9. Interview Challenges
10. User and Project Management

The exact Java package and Maven module structure will be defined in the System Design document.

## 11. Initial MVP Scope

The first MVP should prioritise:

1. Architecture graph representation.
2. Component definitions.
3. Discrete-event simulation engine.
4. Client and server simulation.
5. Request routing.
6. Load balancing.
7. Request queues.
8. Basic database simulation.
9. Metrics calculation.
10. One guided URL Shortener challenge.

A minimal architecture-building interface will be added after the simulation engine has a reliable foundation.

## 12. Non-Goals for the Initial MVP

The following are deliberately deferred:

- Production-grade distributed infrastructure.
- Real Swiggy or Zomato production integrations.
- Full Kubernetes orchestration.
- A production-scale Kafka cluster.
- A complete catalogue of every architecture component.
- Advanced AI-generated architecture recommendations.
- A fully featured collaborative editor.
- A polished frontend before the simulation engine works.

## 13. Success Criteria

The MVP will be considered successful when a user can:

1. Construct a supported architecture.
2. Configure its components.
3. Submit a workload.
4. Execute a deterministic simulation.
5. Obtain meaningful performance metrics.
6. Introduce a supported failure.
7. Observe and explain the impact.
8. Compare two architecture configurations.

The simulation engine must have automated tests verifying expected behaviour under controlled scenarios.

## 14. Open Engineering Decisions

The following decisions require further design work:

- How detailed should each component's behaviour model be?
- How should request routing and communication be represented?
- How should simulation time and event scheduling work?
- How should concurrent requests be modelled?
- How should component failures propagate?
- How should architecture versions be stored and compared?
- What level of accuracy should simulation metrics promise?
- How should interview evaluation be scored?
- How should the simulation engine handle large workloads efficiently?

---

**End of PRD — Version 0.2**
