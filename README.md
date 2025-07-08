# Product Setup Documentation

This document provides comprehensive setup instructions for all microservices and frontend components required to run the complete product ecosystem. The architecture consists of multiple specialized services that work together to provide a complete learning management system with event management, attendance tracking, and notification capabilities.

## Architecture Overview

The product follows a microservices architecture with the following key components:

- **Interface Service**: Middleware layer between frontend and microservices
- **User Service**: Multi-tenancy and user management with Keycloak integration
- **Knowlg & InQuiry**: Content and assessment management (DPG services)
- **Tracking Service**: Learning progress and certification tracking
- **Event Service**: Online/offline event management
- **Attendance Service**: Attendance tracking with location capabilities
- **Notification Service**: Multi-channel notification system
- **Frontend**: Micro-frontend architecture for modular UI components

### Overall Architecture Diagram

![Overall Architecture](architecture-diagram.png)

*The overall architecture diagram shows the complete ecosystem with all microservices, their interactions, and the frontend components. The diagram illustrates how the Interface Service acts as a middleware layer, connecting the frontend to various specialized services including user management, content management, tracking, events, attendance, and notifications.*

### Frontend Architecture Diagram

![Frontend Architecture](frontend-architecture-diagram.png)

*The frontend architecture diagram demonstrates the micro-frontend (MFE) structure using Docker containers and Node.js modules. It shows how different workspaces handle specific functionalities like user management, content creation, course consumption, login/registration, attendance, and events. The architecture uses both dynamic routing and iframe-based component integration, with a shared library containing common components and structures.*

## Prerequisites

Before setting up the services, ensure you have the following installed:

- Docker and Docker Compose
- Node.js (version 14 or higher)
- PostgreSQL
- Redis
- Keycloak (for authentication)

## Service Setup Instructions

### 1. Interface Service Setup

The Interface Service acts as middleware between the frontend and microservices, handling API routing and request management.

**Repository**: [interface-service](https://github.com/tekdi/interface-service)

#### Installation Steps:

```bash
# Clone the repository
git clone https://github.com/tekdi/interface-service.git
cd interface-service

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Edit .env file with your configuration

# Start the service
npm start
```

#### Key Features:
- API gateway functionality
- Request routing to appropriate microservices
- Authentication middleware
- Rate limiting and security features

For detailed setup instructions, refer to the [Interface Service README](https://github.com/tekdi/interface-service).

### 2. User Service Setup

The User Service manages multi-tenancy, user authorization through Keycloak, user-tenant role mapping, and cohort/group management.

**Documentation**: [User Service Documentation](https://tekdi.github.io/docs/category/user-service)

#### Key Features:
- Multi-tenant architecture support
- Keycloak integration for authentication and authorization
- User role and permission management
- Cohort and group management functionality
- Tenant-specific user data isolation

#### Installation:
Follow the comprehensive setup guide in the [User Service Documentation](https://tekdi.github.io/docs/category/user-service) for detailed installation steps, configuration options, and API documentation.

### 3. Knowlg & InQuiry Services Setup

These Digital Public Goods (DPG) services provide comprehensive content management and assessment capabilities, forming the core of the LMS functionality.

#### Knowlg Service
**Documentation**: [Knowlg Documentation](https://knowlg.sunbird.org/)

Knowlg handles:
- Content creation and management
- Course authoring and publishing
- Content metadata and taxonomy
- Digital asset management

#### InQuiry Service  
**Documentation**: [InQuiry Documentation](https://inquiry.sunbird.org/)

InQuiry manages:
- Question and question set creation
- Assessment and quiz functionality
- Question bank management
- Assessment analytics

#### Installation:
Both services are part of the Sunbird ecosystem. Follow the official documentation links above for:
- System requirements
- Installation procedures
- Configuration guidelines
- API documentation

### 4. Tracking Service Setup

The Tracking Service monitors user interactions with courses, content, questions, and question sets, providing learning analytics and certification tracking.

**Repository**: [tracking-microservice](https://github.com/tekdi/tracking-microservice)

#### Key Features:
- Course progress tracking
- Content consumption analytics
- Question and assessment completion tracking
- Certification management
- Learning path analytics

#### Installation:
```bash
# Clone the repository
git clone https://github.com/tekdi/tracking-microservice.git
cd tracking-microservice

# Follow the setup instructions in the repository README
```

### 5. Event Service Setup

The Event Service manages both online and offline events, supporting various video conferencing platforms and recurring event capabilities.

**Repository**: [event-management-service](https://github.com/tekdi/event-management-service)  
**Documentation**: [Event Service Documentation](https://tekdi.github.io/docs/category/event-service)

#### Key Features:
- Online and offline event creation
- Zoom and Google Meet integration
- Extensible provider interface for new platforms
- Recurring event support
- Event participant management
- Calendar integration

#### Installation:
```bash
# Clone the repository
git clone https://github.com/tekdi/event-management-service.git
cd event-management-service

# Follow setup instructions in README and documentation
```

### 6. Attendance Service Setup

The Attendance Service provides flexible attendance tracking with location capture capabilities for various use cases.

**Repository**: [attendance-microservice](https://github.com/tekdi/attendance-microservice)  
**Documentation**: [Attendance Service Documentation](https://tekdi.github.io/docs/category/attendance-service)

#### Key Features:
- Entity-agnostic attendance tracking
- Location-based attendance verification
- Classroom attendance management
- Event/session attendance tracking
- Attendance analytics and reporting

#### Installation:
```bash
# Clone the repository
git clone https://github.com/tekdi/attendance-microservice.git
cd attendance-microservice

# Follow setup instructions in README and documentation
```

### 7. Notification Service Setup

The Notification Service provides horizontal notification capabilities across multiple channels with template management.

**Repository**: [notification-microservice](https://github.com/tekdi/notification-microservice)  
**Documentation**: [Notification Service Documentation](https://tekdi.github.io/docs/category/attendance-service)

#### Key Features:
- Multi-channel notifications (Email, WhatsApp, SMS, Push)
- Template management system
- Notification scheduling
- Delivery tracking and analytics
- Admin dashboard for template creation

#### Installation:
```bash
# Clone the repository
git clone https://github.com/tekdi/notification-microservice.git
cd notification-microservice

# Follow setup instructions in README and documentation
```

### 8. Frontend Setup (Micro-Frontend Architecture)

The frontend uses a micro-frontend architecture allowing modular deployment of UI components based on required functionality.

**Repository**: [shiksha-mfe](https://github.com/tekdi/shiksha-mfe)

#### Key Features:
- Modular micro-frontend architecture
- Configurable component deployment
- Responsive design
- Integration with all backend services
- Role-based UI rendering

#### Installation:
```bash
# Clone the repository
git clone https://github.com/tekdi/shiksha-mfe.git
cd shiksha-mfe

# Install dependencies
npm install

# Configure micro-frontends as needed
# Follow repository README for detailed setup
```

## Configuration and Integration

### Environment Variables

Each service requires specific environment variables for configuration. Common variables include:

- Database connection strings
- Redis configuration
- Keycloak server details
- Service URLs and ports
- API keys for external services

### Service Communication

Services communicate through:
- REST APIs via the Interface Service
- Direct service-to-service calls where appropriate
- Event-driven communication for async operations

### Database Setup

Most services require PostgreSQL databases. Create separate databases for each service to maintain data isolation.

## Deployment Considerations

### Docker Deployment

Each service includes Docker configuration for containerized deployment:

```bash
# Build and run services using Docker Compose
docker-compose up -d
```

### Kubernetes Deployment

For production deployments, consider using Kubernetes for:
- Service orchestration
- Load balancing
- Auto-scaling
- Health monitoring

### Monitoring and Logging

Implement monitoring solutions for:
- Service health checks
- Performance metrics
- Error tracking
- Log aggregation

## Support and Documentation

For detailed setup instructions, API documentation, and troubleshooting:

- Check individual service repositories
- Review service-specific documentation links
- Refer to the main project documentation
- Contact the development team for support

## Contributing

Please refer to individual service repositories for contribution guidelines and development setup instructions.

---

This documentation provides a high-level overview of the product setup. For detailed technical implementation, refer to the individual service repositories and documentation links provided above.