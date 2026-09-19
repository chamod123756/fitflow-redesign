# Activity 4 – High-Level System Architecture

## 1. Introduction

The proposed FitFlow architecture is designed to provide a scalable, secure, and maintainable fitness application across Android, iOS, and web platforms.

The architecture separates the frontend, main backend, AI/ML services, database, caching, and real-time communication components.

---

## 2. High-Level Architecture

The main components of the FitFlow system are:

- Flutter frontend
- Node.js / NestJS backend
- PostgreSQL database
- Python / FastAPI AI service
- Redis caching layer
- WebSockets / Firebase real-time services
- Authentication service
- External health and fitness integrations

### Architecture Flow

**Flutter Frontend → NestJS Backend → PostgreSQL**

**NestJS Backend → FastAPI AI Service**

**NestJS Backend → Redis**

**NestJS Backend → WebSockets / Firebase**

---

## 3. Frontend Layer

Flutter is used as the main frontend technology.

The frontend provides:

- User registration and login.
- Workout tracking.
- Personalized workout plans.
- Nutrition tracking.
- Fitness progress dashboards.
- Social features.
- Notifications.
- Profile and settings.
- Real-time updates.

Flutter allows most application code and UI components to be shared between Android, iOS, and web.

---

## 4. Backend Layer

Node.js with NestJS is used as the main backend framework.

The backend is responsible for:

- User management.
- Workout management.
- Nutrition management.
- Social features.
- Fitness progress.
- API communication.
- Authentication and authorization.
- Notification management.
- Communication with the AI service.

NestJS provides a modular architecture that makes the system easier to maintain and scale.

---

## 5. AI/ML Service

Python with FastAPI is used as a separate AI/ML microservice.

The AI service can provide:

- Personalized workout recommendations.
- Exercise recommendations.
- Nutrition recommendations.
- Fitness progress analysis.
- User behavior analysis.
- AI-generated fitness insights.

The NestJS backend communicates with the FastAPI service through secure APIs.

### Example Flow

**User → Flutter → NestJS → FastAPI → AI Model → NestJS → Flutter**

---

## 6. Database Layer

PostgreSQL is used as the primary database.

It stores structured information such as:

- User accounts.
- User profiles.
- Workout plans.
- Exercise records.
- Nutrition records.
- Fitness progress.
- Social interactions.
- Goals and achievements.

PostgreSQL provides strong consistency, relationships, transactions, indexing, and complex query support.

---

## 7. Caching Layer

Redis is used as the caching layer.

It can improve system performance by storing frequently accessed data such as:

- Popular workout plans.
- Frequently requested user information.
- Temporary session-related data.
- Frequently accessed recommendations.
- Real-time activity information.

Caching reduces unnecessary database queries and improves response times.

---

## 8. Real-Time Communication

WebSockets and Firebase can be used to support real-time functionality.

Possible features include:

- Live workout progress.
- Social activity updates.
- Friend interactions.
- Challenge updates.
- Notifications.
- Real-time fitness tracking.

The real-time layer allows users to receive updates without repeatedly refreshing the application.

---

# 9. Personalized Workout Data Flow

The personalized workout process can follow these steps:

1. The user enters fitness goals and preferences through Flutter.
2. Flutter sends the information to the NestJS backend.
3. NestJS validates and processes the request.
4. The backend sends relevant information to the FastAPI AI service.
5. The AI service generates a personalized workout recommendation.
6. The recommendation is returned to NestJS.
7. The workout plan is stored in PostgreSQL.
8. Frequently accessed recommendations can be cached using Redis.
9. The personalized plan is displayed in the Flutter application.

### Flow

**User → Flutter → NestJS → FastAPI → PostgreSQL/Redis → Flutter**

---

# 10. Social Sharing Data Flow

The social sharing process can work as follows:

1. A user creates a social post or shares a fitness achievement.
2. Flutter sends the information to NestJS.
3. NestJS validates and stores the information.
4. PostgreSQL stores the social activity.
5. WebSockets/Firebase sends real-time updates to relevant users.
6. Other users receive the updated social content.

### Flow

**User → Flutter → NestJS → PostgreSQL → WebSockets/Firebase → Other Users**

---

# 11. Nutrition Tracking Data Flow

The nutrition tracking process can work as follows:

1. The user records a meal through Flutter.
2. The data is sent to the NestJS backend.
3. NestJS validates and stores the information.
4. PostgreSQL stores the nutrition record.
5. The FastAPI AI service can analyze the nutrition information.
6. AI-generated recommendations are returned to the user.
7. The results are displayed through Flutter.

### Flow

**User → Flutter → NestJS → PostgreSQL → FastAPI AI → Flutter**

---

# 12. Security Architecture

Security is a major requirement because FitFlow handles personal and fitness-related information.

Security measures include:

- HTTPS/TLS for network communication.
- Secure authentication using Supabase Auth.
- JWT/OAuth-based token management.
- Role-based access control.
- Encryption of sensitive information.
- Secure API endpoints.
- Input validation and sanitization.
- API rate limiting.
- Audit logging.
- Secure storage of API keys and secrets.
- Regular dependency and security updates.

Privacy requirements such as GDPR should also be considered where applicable.

Using a particular technology does not automatically make the system HIPAA or GDPR compliant. Compliance depends on the complete technical, organizational, and data-management processes.

---

# 13. Scalability

The architecture is designed to support future growth.

Scalability can be achieved through:

- Containerized backend services.
- Load balancing.
- Horizontal scaling.
- Redis caching.
- Database indexing.
- Database read replicas when required.
- Independent scaling of the AI service.
- Cloud-based auto-scaling.
- CDN usage for static resources.
- Monitoring and logging.

The AI service can be scaled independently from the main backend when AI workloads increase.

---

# 14. External Integrations

FitFlow can integrate with external services such as:

- Apple Health.
- Google Fit / Health Connect.
- Payment gateways.
- Firebase Cloud Messaging.
- Email and SMS services.
- AI/ML services.
- Wearable fitness devices.

These integrations can extend the functionality of FitFlow without significantly changing the core architecture.

---

# 15. Architecture Decision Record (ADR)

## ADR-001: Technology Stack Selection

**Status:** Accepted

### Decision

The FitFlow redesign will use:

- Flutter for the frontend.
- Node.js / NestJS for the main backend.
- PostgreSQL as the primary database.
- Supabase Auth for authentication.
- Python / FastAPI for AI/ML services.
- Redis for caching.
- WebSockets / Firebase for real-time functionality.

### Rationale

This technology combination provides:

- Cross-platform development.
- High performance.
- Code reusability.
- Scalable backend services.
- Strong structured data management.
- Secure authentication.
- AI/ML capabilities.
- Real-time functionality.
- Easier long-term maintenance.

### Consequences

The architecture contains multiple technologies and services, which increases initial development complexity.

However, separating the AI service, backend, database, and real-time components allows each service to be developed, maintained, and scaled independently.

---

# 16. Architecture Diagram

The architecture diagram illustrates the relationship between:

- Flutter frontend.
- NestJS backend.
- PostgreSQL.
- FastAPI AI service.
- Redis.
- WebSockets / Firebase.
- External integrations.
- Security and scalability components.

The architecture supports personalized workouts, social sharing, nutrition tracking, AI/ML functionality, and real-time communication.

**Architecture Diagram:** `architecture-diagram.png`

---

# 17. Conclusion

The proposed FitFlow architecture provides a scalable and maintainable foundation for a modern fitness application.

The combination of Flutter, NestJS, PostgreSQL, FastAPI, Redis, and real-time services provides a balance between performance, cross-platform support, AI capabilities, security, and future scalability.

The modular architecture also allows new features and external integrations to be added without significantly affecting the existing system.
