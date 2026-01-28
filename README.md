# Ecommerce Project

Spring Boot backend for a simple e-commerce catalog (products and categories), plus starter assets for the UI and database setup.

## Repository structure

- `01-starter-files/`
  - `db-scripts/` – MySQL schema + sample data
  - `spring-boot-properties/` – sample application properties
  - `angular-image-assets/` – image assets for a UI
- `02-backend/spring-boot-ecommerce/` – Spring Boot API (Maven project)
- `03-frontend/angualr-ecommerce/` – reserved for the Angular UI (empty in this snapshot)

## Tech stack

- Java 17 + Spring Boot 3
- Spring Data JPA + Spring Data REST
- MySQL 8

## Getting started

### Prerequisites

- Java 17
- MySQL 8
- Maven (or use the included `./mvnw`)
- Node.js/Angular CLI (only if you add a UI)

### Database setup

1. Create the database user and schema:
   ```bash
   mysql -u root -p < 01-starter-files/db-scripts/01-create-user.sql
   mysql -u root -p < 01-starter-files/db-scripts/02-create-products.sql
   ```
2. Update credentials as needed in:
   - `02-backend/spring-boot-ecommerce/src/main/resources/application.properties`

### Run the backend

```bash
cd 02-backend/spring-boot-ecommerce
./mvnw spring-boot:run
```

The API base path is configured as `/api`. Sample endpoints:

- `GET http://localhost:8080/api/products`
- `GET http://localhost:8080/api/product-category`

### Run tests

```bash
cd 02-backend/spring-boot-ecommerce
./mvnw test
```

> Note: tests expect a running MySQL instance with the schema from the scripts above.

## Frontend notes

The `03-frontend/angualr-ecommerce` directory is reserved for the Angular app. If you scaffold a UI there, update CORS origins in:

- `02-backend/spring-boot-ecommerce/src/main/java/com/mee632/ecommerce/dao/ProductRepository.java`
- `02-backend/spring-boot-ecommerce/src/main/java/com/mee632/ecommerce/dao/ProductCategoryRepository.java`

## Troubleshooting

- **Database connection refused** – confirm MySQL is running and the credentials in `application.properties` match your local setup.
