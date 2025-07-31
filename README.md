# AI Project Blueprint

A generic Spring Boot application template for AI projects.

## Features

- Spring Boot 3.3.0
- REST API with Swagger/OpenAPI documentation
- Basic Hello World example
- Clean project structure
- Gradle build system

## Getting Started

### Prerequisites

- Java 17 or higher
- Gradle (or use the included wrapper)

### Running the Application

```bash
./gradlew bootRun
```

### API Endpoints

- `GET /api/hello` - Hello World endpoint
- `GET /api/hello?name=YourName` - Personalized greeting
- `GET /api/health` - Health check endpoint

### Swagger UI

Once the application is running, visit:
http://localhost:8080/swagger-ui.html

## Project Structure

```
src/
├── main/
│   ├── java/com/example/
│   │   ├── Application.java          # Main application class
│   │   ├── config/                   # Configuration classes
│   │   ├── controller/               # REST controllers
│   │   └── service/                  # Business logic services
│   └── resources/
│       └── application.properties    # Application configuration
└── test/
    └── java/com/example/
        └── ApplicationTests.java     # Test classes
```

## Customization

1. Update the package name from `com.example` to your desired package
2. Rename the main `Application.java` class if needed
3. Add your specific dependencies to `build.gradle.kts`
4. Configure application properties as needed
5. Add your business logic to services and controllers