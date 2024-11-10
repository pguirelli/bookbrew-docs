# bookbrew-docs
Official documentation of the BookBrew solution architecture. This repository contains diagrams, data flows, detailed explanations of the microservices, BFFs (web and mobile), and instructions for local setup and technologies used.<br><br>

## Software Architecture Document
**Project:** Personalized Curation E-commerce for Books, Perfumes, Coffee, and Beverages.<br><br>

### 1. Introduction
- **Objective:** This document describes the software architecture of the personalized curation e-commerce project. The solution aims to offer customized product recommendations based on user preferences, using a combination of questionnaires and AI.
- **Scope:** This document covers the backend, frontend, and BFF (Backend for Frontend) service architectures, detailing each component and how they interact to provide a personalized user experience.<br><br>

### 2. Architecture Overview
- The system architecture is based on microservices, with an intermediary BFF service tailored to each client type (web and mobile). Each microservice is responsible for a specific functionality, allowing scalability, independence, and flexibility for future growth. Data storage is divided among three databases: MySQL, MongoDB, and Redis, each serving a specific purpose.<br><br>

### 3. Architecture Components
- #### 3.1. Presentation Layer (Frontend)
  - **Web App:** User interface for web access, developed in React or Angular.
  - **App Mobile:** Interface for mobile devices, built with frameworks like React Native or Flutter.
  - **Responsibilities:** Interacts with the BFF to retrieve data on products, carts, profiles, and recommendations, adapting the presentation for each platform.

- #### 3.2. Backend for Frontend (BFF) Services
  - The BFF services serve as intermediaries between the frontend and backend microservices, providing a client-specific layer:
    - **BFF Web:** Serves the needs of the web client, aggregating and transforming data from backend services to provide formatted, optimized responses.
    - **BFF Mobile:** Serves the mobile client, optimizing responses to save data and improve performance on mobile devices.
    - **BFF Justification:**
      - Reduces frontend complexity by centralizing data aggregation logic.
      - Adapts responses for each platform, offering a personalized experience.

- #### 3.3. Backend Microservices
  - Each microservice is responsible for a specific function and communicates with the BFF or other services via RESTful APIs or gRPC:
    1. Product Registration Service
        - **Function:** Manages product information, including name, description, category, price, and stock.
        - **Database:** MySQL (structured, relational data).
    2. Customer Registration Service
        - **Function:** Manages customer data, such as personal information, purchase history, and preferences.
        - **Database:** MySQL (structured, relational data).
    3. Questionnaire and Curation Service
        - **Function:** Collects profile questionnaire responses, feeding the AI service for recommendations.
        - **Database:** MongoDB, due to flexibility with semi-structured data.
    4. AI Curation Service
        - **Function:** Processes behavioral data and questionnaire responses to provide personalized recommendations.
        - **Technology:** TensorFlow Serving or PyTorch.
        - **Database:** MongoDB, for flexible, high-volume preference data storage.
    5. Cart and Order Service
        - **Function:** Manages the shopping cart and checkout flow.
        - **Database:** Redis (temporary cart storage) and MySQL for order data.
    6. Payment Service
        - **Function:** Processes financial transactions with providers like Stripe or PayPal.
        - **Security Considerations:** Implements multi-factor authentication (MFA) and encryption.
    7. Notification Service
        - **Function:** Sends notifications to customers via email, SMS, or push notifications.
        - **Technology:** Twilio for SMS and push notifications, Amazon SES for emails.
    8. Reporting and Analysis Service
        - **Function:** Generates user behavior and sales reports.
        - **Database:** MySQL for basic data and integration with analytics tools as needed.<br><br>

### 4. Data Layer
  - Databases Used
    - **MySQL:**
      - **Use:** Storage of structured and relational data, such as customer registration, order information, and structured product data.
      - **Justification:** MySQL is efficient for relational data and facilitates complex queries.
    - **MongoDB:**
      - **Use:** Storage of flexible and semi-structured data, such as questionnaire responses and user preferences.
      - **Justification:** MongoDB offers flexibility in unstructured data storage and horizontal scalability.
    - **Redis:**
      - **Use:** Cache for temporary data and fast access to shopping cart data.
      - **Justification:** Redis is ideal for cache storage, temporary sessions, and high-frequency data, reducing the load on MySQL and MongoDB.<br><br>

### 5. Communication and Messaging Flow
  - To ensure efficient, decoupled communication between microservices, a messaging system is used:
    - **Message Queue (RabbitMQ or Kafka):** Facilitates asynchronous processing between services, such as sending notifications or updating inventory.
    - **Events:** Purchase event notifications, inventory updates, and payment notifications.<br><br>

### 6. Security and Authentication
  - To ensure data security and privacy:
    - **Authentication and Authorization:** JWT and OAuth 2.0 for secure API access.
    - **Encryption:** Sensitive data encrypted both in transit and at rest.
    - **Access Monitoring:** Access logs and alerting systems.<br><br>

### 7. Continuous Integration and Deployment (CI/CD) Pipeline
  - To accelerate the development cycle and improve code quality, CI/CD pipelines are recommended:
    - **Continuous Integration:** Automated testing and build automation with GitHub Actions or GitLab CI.
    - **Continuous Deployment:** Kubernetes or Docker Swarm for container management, with configured auto-scaling.<br><br>

### 8. Monitoring and Observability
  - To ensure high availability and quickly identify issues:
    - **Centralized Logging:** ELK Stack (Elasticsearch, Logstash, Kibana) for log monitoring.
    - **Tracing:** Tracing tools like Jaeger for distributed monitoring.
    - **Alerts and Dashboards:** Grafana and Prometheus for real-time alerting.<br><br>

### 9. Data Flow and Use Case Examples
  - Personalized Recommendation Flow Example:
    1. The user completes the questionnaire.
    2. The Questionnaire Service sends responses to the AI Service.
    3. The AI Service processes the responses and logs a list of recommendations.
    4. The BFF, when displaying the homepage, queries the AI Service to display personalized recommendations.<br><br>

### 10. Conclusion
  - The architecture with MySQL, MongoDB, and Redis provides an efficient combination to store and process data optimally, allowing flexibility for personalized data, reliable relational storage, and high-performance caching. The microservices structure enables modular project growth, allowing new features to be integrated with minimal impact on the existing architecture.

