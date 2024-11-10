# bookbrew-docs
Official documentation of the BookBrew solution architecture. This repository contains diagrams, data flows, detailed explanations of the microservices, BFFs (web and mobile), and instructions for local setup and technologies used.<br><br>

# Overview
<br>

## E-commerce: "Book & Brew"

### 1. Concept
An e-commerce platform offering a curated selection of books, perfumes, coffees, and beverages, with personalized recommendations based on user profile data gathered through a questionnaire.<br><br>

### 2. Basic Features
1. **Home Page**: Displays featured products, promotions, and categories (perfume, book, coffee, and beverages).
2. **User Registration**: Allows users to register and log in.
3. **Product Catalog**: Shows a list of products with images, descriptions, and prices.
4. **Filter and Search**: Enables users to filter products by category and search by name.
5. **Product Details**: Each product has a dedicated page with detailed information, reviews, and an "Add to Cart" button.
6. **Shopping Cart**: Users can add products, view the cart, and modify quantities.
7. **Checkout**: Offers payment options like credit card, PayPal, etc., processing payments (which may be simulated) and collecting shipping information.
8. **Order History**: Users can view their previous orders.<br><br>

### 3. Profile Questionnaire
1. An interactive questionnaire analyzing literary tastes, coffee, and beverage preferences (such as teas or cocktails).
2. Based on the responses, the system generates a profile and recommends products.<br><br>

### 4. Personalized Recommendations
1. **A "Recommendations for You" section** showcasing books, coffees, and beverages that align with the user profile.
2. **Suggestions based on behavior analysis**, including previous purchases and reviews.<br><br>

### 5. Additional Features
1. **Product Reviews**: Users can leave reviews and comments on products.
2. **Wishlist**: Allows users to save products for later purchase.
3. **Admin Interface**: A backend interface for managing products, categories, and orders.
4. **Email Notifications**: Sends order confirmation emails and status updates.
5. **Blog**: A section with articles on literature, coffee tips, and beverage pairings, promoting engagement.
6. **Subscription Clubs**: Offers monthly subscription plans featuring curated selections of books, coffees, and beverages based on the user profile.
7. **Virtual Events**: Webinars or live events with authors, baristas, or beverage experts to engage the community.
8. **Gamification**: Rewards or points for interactions (such as reviews, shares, etc.) that can be redeemed for discounts or products.<br><br>

### 6. Suggested Technologies
1. **Frontend**: React, Vue.js, or Angular.
2. **Backend**: Node.js with Express or Django.
3. **Database**: MongoDB or PostgreSQL.
4. **API**: RESTful or GraphQL for frontend-backend communication.
5. **Authentication**: JWT (JSON Web Tokens) for user authentication.<br><br>

### 7. Testing Scenarios
1. **API Testing**: Test all API routes to ensure they return correct data.
2. **UI Testing with Selenium**: Verify that the user interface behaves as expected (navigation, cart addition, etc.).
3. **Mobile Testing**: Use Appium or similar tools to test the responsive e-commerce version.
4. **Performance Testing**: Use tools like JMeter or Gatling to simulate system load.
5. **CI/CD**: Set up a pipeline on GitHub Actions or GitLab CI for automated testing and deployment.
6. **Cloud Deployment**: Use services like Heroku, AWS, or DigitalOcean for hosting.<br><br>

### 8. Documentation
1. **Provide clear documentation** on how to run, test, and contribute to the project. Include diagrams to clarify the architecture.<br><br>

### 9. Deliverables List
1. **Solution Documentation**
   - Business Story Specification
   - Design and UX: Include wireframes or mockups of key screens.
2. **Database Documentation**
   - Data Model: ER (Entity-Relationship) Diagram displaying tables, relationships, and attributes.
   - Table Specifications: Detail each table (columns, data types, constraints).
3. **Diagrams**
   - Use Case Diagram: Shows interactions between users and the system.
   - Flow Diagram: Visual representation of user flow (e.g., how a user navigates the site).
   - Sequence Diagram: Illustrates interactions among system components during specific actions (such as checkout).
4. **Architecture Documentation**
   - Architecture Diagram: Shows the system's overall architecture (frontend, backend, database, APIs, third-party services).
   - Technologies Used: List tools and technologies in each layer (e.g., React, Node.js, MongoDB).
5. **Testing Scenarios**
   - Test Plan: List objectives and test strategies.
   - Test Cases: Specify test cases for functionality, performance, and security.
   - Automated Tests: Examples of automated tests with Selenium, API tests with Postman or test frameworks.
6. **Development**
   - Source Code: Organize the GitHub repository with a clear folder structure.
   - Readme.md: Include a well-written README file with installation, usage, features, and an overview of the project.
   - Demo: If possible, provide a live demo of the project or video recordings of the functionality.
7. **DevOps Practices**
   - CI/CD: Document how continuous integration and delivery are implemented, with configuration examples (e.g., GitHub Actions).
   - Cloud Deployment: Explain how the project was hosted and any cloud configuration (e.g., AWS, Heroku).
8. **Feedback and Iteration**
   - Results and Metrics: If possible, provide metrics indicating project success (e.g., user count, simulated sales).
9. **Visual Presentation**
   - Screenshots: Show the user interface and main features.
10. **Final Reflection**
    - Lessons Learned: Share what you learned during project development.<br><br>

### 10. AI Options for Curated Recommendations Based on Provided Characteristics
1. **Hugging Face Transformers**
   - **Description**: Hugging Face offers a library of pre-trained models, including recommendation and natural language processing (NLP) models.
   - **Use**: Models like BERT can analyze characteristics and generate recommendations.
   - **Cost**: The library is free, though there may be costs if using large-scale models via API.
2. **OpenAI GPT-2**
   - **Description**: Predecessor to GPT-3, it is more accessible and can be run locally.
   - **Use**: Useful for generating text and recommendations based on specific inputs.
   - **Cost**: Free for local use; requires computing resources.
3. **Recommender Systems with Scikit-learn**
   - **Description**: Scikit-learn enables simple recommendation systems like collaborative filtering or content-based systems.
   - **Use**: With product feature data and user preferences, a recommendation model can be created.
   - **Cost**: Free, provided you have quality data.
4. **Spotify API**
   - **Description**: For recommendations (music pairings with beverages), the Spotify API allows for personalized suggestions.
   - **Use**: Mainly music-focused, but adaptable for this project.
   - **Cost**: Free, though usage limits apply.
5. **GitHub Repositories**
   - **Description**: Numerous GitHub repositories offer recommendation projects that can be adapted.
   - **Use**: Search for "recommendation system" to find customizable implementations.
   - **Cost**: Free if using available code.<br><br>

### 11. Considerations
   - **Customization**: Depending on your choice, some customization or implementation work may be required to tailor AI for your needs.
   - **Infrastructure**: Some options may require computing infrastructure, especially for running larger models.
   - **Data**: Ensure quality data on products and user preferences for training and validating your recommendation system.<br><br>


# Software Architecture Document
<br>

## Project: Personalized Curation E-commerce for Books, Perfumes, Coffee, and Beverages.

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

