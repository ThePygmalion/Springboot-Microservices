# Spring Boot Microservices Architecture

This project demonstrates a microservices architecture using Spring Boot, with various services that interact with each other through a central API Gateway. It includes services for authentication, expense tracking, and notifications, all of which are monitored using Grafana and deployed in Docker containers.

## Table of Contents

- [Architecture Overview](#architecture-overview)
- [Microservices](#microservices)
- [Technologies Used](#technologies-used)
- [Setup and Installation](#setup-and-installation)
- [Endpoints](#endpoints)
- [Monitoring](#monitoring)

## Architecture Overview

The system consists of multiple microservices with a centralized API Gateway to route requests. Here's a high-level description of the components:

- **Angular Frontend**: Serves as the client-side interface for interacting with the microservices.
- **Spring Cloud API Gateway**: Acts as an entry point for all incoming requests, handling routing and load balancing.
- **Eureka Server**: Service registry that allows the microservices to locate and communicate with each other.
- **Authorization/Authentication Server**: Manages user authentication and authorization.
- **Expense Tracking Service**: Handles the operations related to expense management.
- **Notification Service**: Sends notifications based on different events or triggers.
- **Grafana**: Provides monitoring and metrics for the services.
- **Docker**: Used to containerize the application for easy deployment and scaling.

## Microservices

1. **API Gateway**: 
   - Handles routing and security for the microservices.
   - Configured using Spring Cloud Gateway.

2. **Eureka Server**:
   - Acts as a service registry for discovery and registration of microservices.
   - Ensures load balancing and resilience of services.

3. **Authorization/Authentication Service**:
   - Responsible for user authentication (login and registration).
   - Manages access tokens and secures APIs.

4. **Expense Tracking Service**:
   - Manages CRUD operations for expenses.
   - Stores data in a relational database.

5. **Notification Service**:
   - Sends notifications for events like successful authentication, new expense entries, etc.

## Technologies Used

- **Spring Boot**: Microservices, Eureka, Gateway, and Security.
- **Angular**: Frontend framework.
- **Grafana**: Monitoring and analytics.
- **Docker**: Containerization.
- **MySQL/PostgreSQL** (or any relational database): Data persistence.
- **gRPC/REST**: Communication protocols.

## Setup and Installation

### Prerequisites

- Java 17 or above
- Docker and Docker Compose
- Node.js (for Angular frontend)

### Clone the Repository

```bash
git clone https://github.com/ThePygmalion/Springboot-Microservices.git
cd spring-boot-microservices-project
```

### Build and Run the Services

1. **Start Eureka Server**:
   ```bash
   cd eureka-server
   ./mvnw spring-boot:run
   ```

2. **Start API Gateway**:
   ```bash
   cd api-gateway
   ./mvnw spring-boot:run
   ```

3. **Start Authorization/Authentication Server**:
   ```bash
   cd auth-service
   ./mvnw spring-boot:run
   ```

4. **Start Expense Tracking Service**:
   ```bash
   cd expense-service
   ./mvnw spring-boot:run
   ```

5. **Start Notification Service**:
   ```bash
   cd notification-service
   ./mvnw spring-boot:run
   ```

### Running with Docker Compose

To simplify deployment, use Docker Compose to bring up all services.

```bash
docker-compose up -d
```

### Setting Up the Frontend

1. Navigate to the `frontend` directory.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the Angular application:
   ```bash
   ng serve
   ```

## Endpoints

| Service                      | Endpoint                      | Description                           |
|------------------------------|-------------------------------|---------------------------------------|
| API Gateway                  | `/api/**`                     | Routes requests to services          |
| Authorization Service        | `/auth/login`, `/auth/signup`| User login and registration          |
| Expense Tracking Service     | `/expenses/**`                | CRUD operations for expenses         |
| Notification Service         | `/notifications/**`           | Triggers notifications               |

## Monitoring

Grafana is set up to monitor the health and metrics of the microservices. Access Grafana at `http://localhost:3000` (default credentials are `admin/admin`).

