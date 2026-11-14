# SysForge
## System Design Document

**Version:** 0.1  
**Status:** Initial Architecture Proposal  
**Backend:** Java + Spring Boot  
**Architecture Style:** Modular Monolith

---

## 1. Overview

SysForge will initially be developed as a modular monolithic application.

The application will provide REST APIs through Spring Boot and use an independent Java simulation engine to execute user-defined system architectures.

The simulation engine will be responsible for interpreting architecture graphs, processing simulated events and calculating performance metrics.

The core simulation logic must remain independent of HTTP controllers, database persistence and frontend implementation.

## 2. High-Level Architecture

The platform consists of the following layers:

### 2.1 Presentation Layer
- React frontend.
- Architecture graph editor.
- Simulation configuration interface.
- Metrics visualisation.
- Learning and interview interfaces.

### 2.2 Application Layer
- Spring Boot REST controllers.
- Request validation.
- Application services.
- Simulation orchestration.
- User and project management.

### 2.3 Domain Layer
- Architecture graph.
- Nodes and edges.
- Component definitions.
- Simulation configuration.
- Simulation events.
- Metrics and evaluation models.

### 2.4 Simulation Engine
- Virtual clock.
- Event scheduler.
- Priority queue.
- Workload generator.
- Component behaviour models.
- Request lifecycle management.
- Metrics calculation.

### 2.5 Persistence Layer
- PostgreSQL.
- Spring Data JPA.
- Architecture storage.
- User and project information.
- Simulation history.

## 3. Core Backend Modules

### 3.1 Architecture Management

Responsibilities:
- Create architectures.
- Update architectures.
- Add and remove nodes.
- Add and remove connections.
- Validate graph structure.
- Store architecture configurations.

### 3.2 Simulation Management

Responsibilities:
- Accept simulation requests.
- Validate simulation configuration.
- Start simulation execution.
- Coordinate the simulation engine.
- Return simulation results.
- Manage simulation history.

### 3.3 Simulation Engine

Responsibilities:
- Execute discrete events.
- Maintain virtual simulation time.
- Schedule events.
- Process incoming requests.
- Route requests between components.
- Track component state.
- Handle simulated failures.

The engine should be independently testable without starting the Spring Boot application.

### 3.4 Component Behaviour Library

Initial components:

- Client
- Load Balancer
- Application Server
- Request Queue
- Cache
- Database

Each component must define its configuration, behaviour, inputs, outputs and failure conditions.

### 3.5 Workload Generator

Responsibilities:
- Generate incoming requests.
- Configure request arrival rates.
- Define request distributions.
- Support controlled traffic patterns.

### 3.6 Metrics Engine

Responsibilities:
- Calculate average latency.
- Calculate p50, p95 and p99 latency.
- Calculate throughput.
- Calculate error rate.
- Track queue depth.
- Track resource utilisation.
- Calculate cache hit ratio.

### 3.7 User and Project Management

Responsibilities:
- Manage users.
- Create projects.
- Save architectures.
- Retrieve previous architectures.
- Maintain simulation history.

## 4. Architecture Graph Model

Every user-created system will be represented as a directed graph.

The graph consists of:

### Nodes

Nodes represent architectural components.

Examples:
- Load Balancer
- Application Server
- Cache
- Database
- Message Queue

Each node contains:
- Unique identifier.
- Component type.
- Configuration.
- Position for visualisation.

### Edges

Edges represent communication paths between components.

Each edge contains:
- Unique identifier.
- Source node.
- Destination node.
- Connection properties.

The graph represents the architecture that the simulation engine will interpret.

Visual positioning must not directly affect simulation behaviour.

## 5. Simulation Execution Flow

The initial simulation lifecycle:

1. User creates an architecture.
2. Architecture is submitted to the backend.
3. Graph structure is validated.
4. Simulation configuration is validated.
5. Workload generation begins.
6. Events are scheduled using virtual time.
7. The event scheduler processes events chronologically.
8. Component behaviour models process requests.
9. Metrics are collected.
10. Simulation results are returned.

## 6. Initial Request Lifecycle

Example request flow:

Client → Load Balancer → Application Server → Database

The simulation engine will model:
- Request arrival.
- Routing decisions.
- Queue waiting time.
- Processing time.
- Downstream operations.
- Response completion.

The engine will use a virtual clock rather than relying on real network execution time.

## 7. Initial Technology Stack

| Layer | Technology |
|---|---|
| Language | Java |
| Backend | Spring Boot |
| API | Spring Web |
| Validation | Jakarta Bean Validation |
| ORM | Spring Data JPA |
| Database | PostgreSQL |
| Migrations | Flyway |
| Testing | JUnit 5, Mockito |
| Frontend | React |
| Architecture Editor | React Flow |
| Build Tool | Maven |
| Containerisation | Docker |

## 8. Architectural Principles

1. Use a modular monolithic architecture initially.
2. Keep simulation logic independent of Spring Boot.
3. Prefer composition and clearly defined interfaces for component behaviour.
4. Keep graph validation separate from simulation execution.
5. Use deterministic simulation scenarios for testing.
6. Avoid premature microservice decomposition.
7. Introduce infrastructure technologies only when justified by requirements.

## 9. Open Design Questions

- How should simulation events be represented?
- How should the priority queue schedule events?
- How should virtual time advance?
- How should concurrent requests be modelled?
- How should components communicate during simulation?
- How should failures propagate?
- How should large simulation workloads be handled?
- How should simulation results be persisted?

---

**End of System Design Document — Version 0.1**
