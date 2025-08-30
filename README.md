# Messaging App

This is a real-time messaging application, similar to WhatsApp, with a frontend built using Angular and a backend powered by Spring Boot.

## Architecture

The application follows a client-server architecture:

*   **Frontend:** A single-page application (SPA) built with Angular.
*   **Backend:** A RESTful API built with Spring Boot, with WebSocket support for real-time communication.

The project is structured as a monorepo, with the frontend and backend as separate Git submodules. Docker is used for containerization, allowing for easy setup and deployment.

### Real-time Communication

For real-time messaging, the application uses WebSockets. The backend uses Spring WebSocket with a STOMP message broker, and the frontend uses `sockjs-client` and `stompjs` to communicate with the server.

### Authentication

Authentication is handled using Keycloak. The frontend uses the `keycloak-js` library to authenticate users, and the backend uses Spring Security with OAuth2 to validate access tokens.

## Technologies Used

### Backend (`messaging-app-api`)

*   **Java 17**
*   **Spring Boot:** Core application framework
*   **Spring Data JPA:** Database interaction
*   **Spring Security (OAuth2):** Authentication and authorization
*   **Spring Web:** REST API development
*   **Spring WebSocket:** Real-time communication
*   **PostgreSQL:** Database
*   **Flyway:** Database migrations
*   **Lombok:** Boilerplate code reduction
*   **SpringDoc OpenAPI:** API documentation

### Frontend (`messaging-app-ui`)

*   **Angular:** Core framework
*   **Bootstrap:** UI styling
*   **Keycloak-js:** Authentication
*   **SockJS & STOMPjs:** WebSocket communication
*   **ng-openapi-gen:** API client generation

## Getting Started

To run this application, you will need to have Docker and Docker Compose installed.

1.  **Clone the repository:**

    ```bash
    git clone --recurse-submodules https://github.com/your-username/messaging-app.git
    ```

2.  **Start the application:**

    ```bash
    docker-compose up -d
    ```

This will start the following services:

*   `messaging-app-api`: The backend API server on port 8080.
*   `messaging-app-ui`: The frontend Angular application on port 4200.
*   `postgres`: The PostgreSQL database.
*   `keycloak`: The Keycloak authentication server.

You can then access the application at `http://localhost:4200`.

## API Documentation

The backend API is documented using OpenAPI. You can access the OpenAPI documentation at `http://localhost:8080/swagger-ui.html`.

The frontend API client is generated from the `openapi.json` file located in the `messaging-app-ui/src/openapi` directory. To regenerate the client, run the following command in the `messaging-app-ui` directory:

```bash
npm run api-gen
```
