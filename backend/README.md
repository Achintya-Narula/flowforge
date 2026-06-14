# FlowForge Backend

## Prerequisites

- Git
- Java Development Kit (JDK) 21
- A terminal such as Windows PowerShell, Command Prompt, Terminal, or Bash

Maven is provided through the Maven Wrapper in the `backend` directory, so a separate Maven installation is not required.

## Required Java Version

The backend is configured for Java 21. Confirm your local version before running the app:

```sh
java -version
javac -version
```

Both commands should report version 21.

## Enter The Backend Directory

From the repository root:

```sh
cd backend
```

## Run Tests

On Windows:

```powershell
.\mvnw.cmd test
```

On macOS/Linux:

```sh
./mvnw test
```

## Start The Backend

On Windows:

```powershell
.\mvnw.cmd spring-boot:run
```

On macOS/Linux:

```sh
./mvnw spring-boot:run
```

By default, the backend starts on port `8080`.

## Continuous Integration

GitHub Actions runs backend CI for relevant pull requests and pushes to `main` when backend files or the workflow file change. The workflow can also be run manually from GitHub Actions.

CI executes the backend test suite with:

```sh
./mvnw --batch-mode --no-transfer-progress test
```

Developers should run the backend tests locally before pushing changes.

## Test The Health Endpoint

After starting the backend, call:

```text
GET http://localhost:8080/api/health
```

On Windows PowerShell:

```powershell
Invoke-RestMethod http://localhost:8080/api/health
```

On macOS/Linux:

```sh
curl http://localhost:8080/api/health
```

Expected response:

```json
{
  "status": "UP",
  "service": "flowforge-backend"
}
```
