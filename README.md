# GarageDesk — Vehicle Service Job Card and Bay Scheduling System

A Spring Boot + JPA + H2 REST backend with a browser dashboard for a vehicle service garage.

## Features
- Create, view, update and delete job cards.
- Manage mechanics and service bays with CRUD APIs.
- Assign a mechanic and service bay to a vehicle job.
- Schedule jobs using start/end time.
- Prevent overlapping bookings for the same bay.
- Prevent overlapping bookings for the same mechanic.
- Track job status: WAITING → SCHEDULED → IN_PROGRESS → COMPLETED (or CANCELLED).
- Dashboard counts for jobs, active bays and available mechanics.
- H2 database with persistent file storage under `./data`.
- Centralized validation and error handling.
- Simple frontend served by the same Spring Boot application.

## Requirements
- JDK 17 or newer
- Maven 3.9+ (or an IDE with Maven support)

## Run in IntelliJ / Eclipse / VS Code
1. Open this folder as a Maven project.
2. Let Maven download dependencies.
3. Run `com.garagedesk.GarageDeskApplication`.
4. Open http://localhost:8080

## Run from terminal
```bash
mvn spring-boot:run
```

Or build a jar:
```bash
mvn clean package
java -jar target/garage-desk-1.0.0.jar
```

## H2 Console
Open http://localhost:8080/h2-console
- JDBC URL: `jdbc:h2:file:./data/garagedeskdb`
- User: `sa`
- Password: leave empty

## Postman quick test
1. `GET http://localhost:8080/api/jobs/dashboard/summary`
2. `GET http://localhost:8080/api/jobs`
3. `GET http://localhost:8080/api/mechanics`
4. `GET http://localhost:8080/api/bays`
5. `POST http://localhost:8080/api/jobs` using the JSON in `docs/API-REFERENCE.md`.

## Project structure
`controller` → REST endpoints
`service` → business logic and conflict checking
`repository` → database access
`entity` → JPA database models
`exception` → centralized error responses
`config` → demo data initialization
`static` → browser dashboard
`docs` → API, database, architecture and UML material
