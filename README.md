# AI Project Blueprint

A Spring Boot application template for AI projects with support for multiple AI providers.

## Features

- Spring Boot 3.3.0
- REST API with Swagger/OpenAPI documentation
- Spring AI integration with multiple providers
- Support for OpenAI and Ollama models
- Configurable AI model selection using qualifiers
- Clean project structure with AI service abstractions
- Gradle build system

## Getting Started

### Prerequisites

- Java 17 or higher
- Gradle (or use the included wrapper)
- OpenAI API key (optional, for OpenAI integration)
- Ollama installed and running (optional, for Ollama integration)

### Configuration

Before running the application, configure your AI providers:

1. **For OpenAI**: Set your API key as an environment variable:
   ```bash
   export OPENAI_API_KEY=your_openai_api_key_here
   ```

2. **For Ollama**: Make sure Ollama is installed and the model is available:
   ```bash
   ollama pull qwen2.5:7b
   ```

### Running the Application

```bash
./gradlew bootRun
```

### API Endpoints

- `GET /api/hello` - Hello World endpoint
- `GET /api/hello?name=YourName` - Personalized greeting
- `GET /api/health` - Health check endpoint
- AI Service endpoints (available through AIService implementation)

### Swagger UI

Once the application is running, visit:
http://localhost:8080/swagger-ui.html

## Project Structure

```
src/
├── main/
│   ├── java/com/example/
│   │   ├── Application.java          # Main application class
│   │   ├── config/
│   │   │   ├── ChatModelConfig.java  # AI model configuration
│   │   │   └── SwaggerConfiguration.java
│   │   ├── controller/               # REST controllers
│   │   └── service/
│   │       ├── ai/
│   │       │   ├── AIService.java    # AI service interface
│   │       │   ├── AbstractAIService.java # Abstract AI service
│   │       │   └── AIServiceImpl.java # AI service implementation
│   │       └── HelloService.java
│   └── resources/
│       └── application.properties    # Application configuration
└── test/
    └── java/com/example/
        └── ApplicationTests.java     # Test classes
```

## AI Model Configuration

The application supports multiple AI providers through Spring AI:

### Switching Between AI Models

To use a specific AI model, add the `@Qualifier` annotation to your constructor parameter:

```java
@Autowired
public AIServiceImpl(@Qualifier("openAiModel") ChatModel chatModel) {
    this.chatModel = chatModel;
}
```

Available qualifiers:
- `"openAiModel"` - Uses OpenAI ChatGPT models
- `"ollamaModel"` - Uses Ollama local models (default/primary)

### Configuration Properties

Update `application.properties` to configure your AI providers:

```properties
# OpenAI Configuration
spring.ai.openai.api-key=${OPENAI_API_KEY}

# Ollama Configuration  
spring.ai.ollama.chat.model=qwen2.5:7b
```

## Customization

1. Update the package name from `com.example` to your desired package
2. Rename the main `Application.java` class if needed
3. Add your specific dependencies to `build.gradle.kts`
4. Configure AI providers in `application.properties`
5. Implement your AI service logic by extending `AbstractAIService`
6. Add your business logic to services and controllers