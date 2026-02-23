# AI-Code-Reviewer-Backend

Backend service for the **AI Code Reviewer** system. This application receives code review requests from the frontend, processes them with AI models, and returns structured review results.

## Overview

This project implements a **Java** backend using **Maven** to:

* Accept code submissions or review requests via HTTP API
* Communicate with AI providers (e.g., OpenAI) to generate review feedback
* Provide structured review responses to the frontend
* Store / log results (optional) for review history

This backend pairs with the frontend application in the **AI-Code-Reviewer-Frontend** repository.

## 🛠 Tech Stack

* **Java** (17+ recommended)
* **Spring Boot** (Web API framework)
* **Maven** (Build & dependency management)
* **HTTP Client** (for calling LLM APIs)
* **JSON** (API request/response format)

## 📁 Repository Structure

```
📦 AI-Code-Reviewer-Backend
 ┣ 📂 .mvn/
 ┣ 📂 src/
 ┃ ┣ 📂 main/
 ┃ ┃ ┣ 📂 java/              # Java application source
 ┃ ┃ ┣ 📂 resources/         # Spring Boot config & static resources
 ┃ ┗ 📂 test/                # Unit/integration tests
 ┣ .gitignore
 ┣ mvnw
 ┣ mvnw.cmd
 ┣ pom.xml
 ┗ README.md
```

## 🚀 Features (Expected)

* **REST API endpoints** for reviewing code
* **AI integration** (OpenAI, Anthropic, Gemini, etc.)
* Optional **review history** storage
* Request/response validation and error handling

## 📦 Prerequisites

Install the following to build and run this project:

* **Java 17+**
* **Maven**
* AI API keys for your provider (e.g., OpenAI)

## ⚙️ Setup

1. **Clone the repo**

   ```bash
   git clone https://github.com/FrostScythe/AI-Code-Reviewer-Backend.git
   ```

2. **Configure environment**

   Create a file `src/main/resources/application.properties` (or use environment variables):

   ```
   server.port=8080

   # Example provider configuration
   ai.provider=openai
   ai.openai.apiKey=YOUR_OPENAI_API_KEY
   ```

3. **Update `pom.xml` dependencies**

   Add libraries for Spring Boot Web, JSON processing, and your preferred HTTP client if not already present.

## 🧪 Build

From the root directory:

```bash
./mvnw clean package
```

This generates an executable JAR in the `target/` folder.

## 📡 Run

Run the backend with:

```bash
./mvnw spring-boot:run
```

Or using the packaged JAR:

```bash
java -jar target/ai-code-reviewer-backend-*.jar
```

By default the server runs on **[http://localhost:8080](http://localhost:8080)**.

## 📌 API Endpoints (Example)

Below are suggested API routes; adjust according to your implementation:

### Review Submission

`POST /api/review`

**Request**

```json
{
  "code": "string",
  "language": "string"
}
```

**Response**

```json
{
  "summary": "AI review summary",
  "issues": [
    {
      "line": 10,
      "message": "Description of issue",
      "severity": "warning"
    }
  ]
}
```

### Health Check

`GET /api/health`

**Response**

```json
{ "status": "ok" }
```

## 🔗 Frontend Integration

The frontend app should call the backend review API, for example with:

```js
await fetch(`${BACKEND_URL}/api/review`, {
  method: "POST",
  body: JSON.stringify({ code, language }),
  headers: { "Content-Type": "application/json" }
});
```

## 🛡 Security

* Store API keys securely (do not commit to repo)
* Validate user input before calling external APIs
* Implement rate-limiting if needed

## 💡 Deployment

Deploy this service to any Java hosting or container platform (Heroku, AWS Elastic Beanstalk, Docker, etc.) by packaging the app or containerizing it.

## 🤝 Contributing

Contributions are welcome:

1. Fork the repository
2. Create a branch (`git checkout -b feature/XYZ`)
3. Commit your changes
4. Open a pull request

## 📄 License

Specify your license (e.g., MIT, Apache-2.0). If not provided, add a `LICENSE` file.

---
For the frontend UI application, see the AI-Code-Reviewer-Frontend repository: https://github.com/FrostScythe/AI-Code-Reviewer-Frontend
