# ArtSpark

[![GitHub license](https://img.shields.io/github/license/decagondev/art-spark)](https://github.com/decagondev/art-spark/blob/main/LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/decagondev/art-spark)](https://github.com/decagondev/art-spark/issues)

## Introduction

ArtSpark is an innovative AI-powered web application designed to ignite creativity for digital artists and entrepreneurs in the art industry. By leveraging advanced AI models, ArtSpark generates personalized art project ideas based on user preferences, current market trends, and competitive analysis. Whether you're a freelance artist seeking inspiration to overcome creative blocks or a business owner looking to capitalize on emerging art styles, ArtSpark provides tailored suggestions complete with descriptions, inspirations, and trend insights.

The platform addresses key challenges in the digital art space, such as idea generation, staying updated with trends, and market positioning. Built with a user-centric approach, it features intuitive interfaces for inputting preferences, viewing ideas, managing profiles, and analyzing markets. ArtSpark aims to foster innovation in a rapidly growing industry projected to reach $1.4 trillion globally by 2025.

For detailed project requirements, tasks, API docs, and code examples, refer to the files in the `/docs` folder:
- [PRD.md](/docs/PRD.md): Comprehensive Product Requirements Document.
- [TASKS.md](/docs/TASKS.md): Development tasks broken down into epics, PRs, and commits.
- [API.md](/docs/API.md): API documentation with endpoints and examples.
- [CODE-SNIPPETS.md](/docs/CODE-SNIPPETS.md): Key code snippets for implementation.

## Features

- **AI-Powered Idea Generation**: Input your art style, theme, and preferences to receive customized project ideas.
- **Project Display**: View detailed ideas with inspirations and trending styles.
- **User Profile Management**: Save favorite ideas and preferences for quick access.
- **Market Analysis**: Gain insights into art trends, competition, and demand to inform your projects.
- **RESTful API**: Expose endpoints for integration and extensibility.

## Tech Stack

- **Backend**: Spring Boot with Java 17
- **Database**: MongoDB 5.0
- **AI Integration**: Deeplearning4j with TensorFlow models
- **Security**: Spring Security for authentication
- **Build Tool**: Gradle
- **Frontend**: Thymeleaf templates (with potential for expansion to React or similar)

## Setup Instructions

### Prerequisites

- Java 17 (JDK)
- Gradle 8+
- MongoDB 5.0+ (running locally or via Docker)
- Git

### Installation

1. **Clone the Repository**:
   ```
   git clone https://github.com/decagondev/art-spark.git
   cd art-spark
   ```

2. **Set Up MongoDB**:
   - Install and start MongoDB locally: `mongod --dbpath /path/to/db` (or use Docker: `docker run -d -p 27017:27017 mongo`).
   - Update `src/main/resources/application.yml` with your MongoDB URI if needed (default: `mongodb://localhost:27017/artsparkdb`).

3. **Build the Project**:
```
./gradlew clean build
```

4. **Run the Application**:
```
./gradlew bootRun
```
   - The app will start on `http://localhost:8080`.
   - Access the input form at `/input`, API at `/api` endpoints.

5. **AI Model Setup**:
   - Place the pre-trained model file `artstylemodel.zip` in the root or resources directory (as per code snippets).
- Ensure Deeplearning4j dependencies are resolved via Gradle.

6. **Testing**:
- Run unit/integration tests: `./gradlew test`.
   - Use tools like Postman to test API endpoints (see `/docs/API.md` for details).

### Docker Setup (Optional)

1. Build the Docker image:
   ```
   docker build -t artspark .
   ```

2. Run with Docker Compose (for app + MongoDB):
   - Create `docker-compose.yml` (example in code snippets).
   ```
   docker-compose up
   ```

## Usage

- Visit `http://localhost:8080/input` to submit preferences and generate ideas.
- Use the API for programmatic access (e.g., POST `/api/generate-ideas`).
- Save favorites via profile endpoints (requires authentication).

For development tasks and code examples, check `/docs/TASKS.md` and `/docs/CODE-SNIPPETS.md`.

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/YourFeature`).
3. Commit your changes (`git commit -m 'Add YourFeature'`).
4. Push to the branch (`git push origin feature/YourFeature`).
5. Open a Pull Request.

See `/docs/TASKS.md` for ongoing epics and tasks.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or feedback, open an issue on GitHub or contact the maintainers at decagondev.
