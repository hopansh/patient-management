# Patient Management System

## Overview

The Patient Management System is a modern, microservices-based healthcare application designed to manage patient data, billing information, and analytics. Built with enterprise-grade technologies, this system demonstrates a robust architecture that emphasizes scalability, security, and maintainability.

## Architecture

This project follows a microservices architecture with the following components:

### Core Services

- **API Gateway**: Entry point for all client requests, handles routing, load balancing, and authentication
- **Auth Service**: Manages user authentication and authorization
- **Patient Service**: Handles patient registration, updates, and information retrieval
- **Billing Service**: Manages invoicing, payments, and financial transactions
- **Analytics Service**: Provides insights and reports on patient data and system usage

### Technical Components

- **Integration Tests**: Comprehensive test suite using JUnit Jupiter and REST-Assured to validate API functionality
- **gRPC Communication**: Efficient service-to-service communication using Protocol Buffers
- **Database Layer**: Persistent storage for patient records and system data
- **API Requests Collection**: Pre-configured API requests for testing and development

## Technology Stack

- **Backend**: Java 21, Spring Boot
- **API Documentation**: OpenAPI/Swagger
- **Database**: PostgreSQL (containerized via Docker)
- **Service Communication**: gRPC with Protocol Buffers
- **Testing**: JUnit Jupiter, REST-Assured
- **Build Tool**: Maven
- **Containerization**: Docker
- **API Gateway**: Spring Cloud Gateway

## Key Features

- **Secure Authentication**: JWT-based authentication system
- **Patient Data Management**: Complete CRUD operations for patient records
- **Event-Driven Architecture**: Using Protocol Buffers for efficient event propagation
- **Billing and Payment Processing**: Comprehensive financial management
- **Analytics and Reporting**: Data-driven insights for healthcare providers
- **Scalable Infrastructure**: Designed for horizontal scaling through containerization

## Project Structure
```
    patient-management
    ├── api-gateway/ # API Gateway service
    ├── auth-service/ # Authentication service
    ├── patient-service/ # Patient data management service
    ├── billing-service/ # Billing and payment processing service
    ├── analytics-service/ # Analytics and reporting service
    ├── integration-tests/ # End-to-end test suite 
    ├── grpc-request/ # gRPC communication definitions
    ├── api-requests/ # API request collections
    └── db_volumes/ # Database persistence layer
```

## Getting Started

### Prerequisites

- Java 21 or higher
- Maven
- Docker and Docker Compose
- Git

### Installation

1. Clone the repository:
   ```
   git clone https://github.com/yourusername/patient-management.git
   cd patient-management
   ```

2. Start the services using Docker Compose:
   ```
   docker-compose up -d
   ```

3. Access the API documentation:
   ```
   http://localhost:8080/api-docs
   ```

## Development Workflow

### Building Services

Each service can be built individually:
    ```
    cd service-name mvn clean install
    ```

### Running Tests

Integration tests can be executed to verify system functionality:
    ```
    cd integration-tests mvn test
    ```

### API Development

The system uses Protocol Buffers for data contract definition. The `patient-event.proto` file defines the contract for patient-related events:
    ```
    protobuf syntax = "proto3";
    package patient.events;
    option java_multiple_files = true;
    message PatientEvent{ string patientId = 1; string name = 2; string email = 3; string event_type = 4; }
    ```


## Architecture Highlights

### Event-Driven Communication

The system uses an event-driven approach for inter-service communication. Patient events (such as registration, updates) are propagated using Protocol Buffers for efficient serialization and deserialization.

### Security Implementation

The API Gateway authenticates all incoming requests and passes authenticated requests to the appropriate microservices, ensuring secure communication.

### Database Isolation

Each service maintains its own database schema, adhering to microservice best practices for data isolation and service autonomy.

## Future Enhancements

- **Kubernetes Deployment**: Migration to Kubernetes for improved orchestration
- **Observability Stack**: Integration with Prometheus and Grafana for monitoring
- **Event Sourcing**: Implementation of event sourcing for improved data reliability
- **Machine Learning Integration**: Predictive analytics for patient outcomes

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.