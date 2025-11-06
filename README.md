# E-Commerce Full Stack Application

A full-stack e-commerce application built with Spring Boot and Angular. This project provides a RESTful API backend for managing products and categories, with database persistence using MySQL.

## 🚀 Features

- Product catalog management
- Product categories
- RESTful API endpoints
- MySQL database integration
- JPA/Hibernate ORM
- Spring Data REST
- Entity relationships (Product-Category)
- Automatic timestamp tracking

## 🛠️ Technology Stack

### Backend
- **Java 17**
- **Spring Boot 3.5.6**
- **Spring Data JPA** - Database operations
- **Spring Data REST** - RESTful API endpoints
- **MySQL** - Database
- **Lombok** - Reduce boilerplate code
- **Maven** - Build tool

### Frontend
- **Angular** (planned/in development)
- **Bootstrap 5.2.0**
- **Font Awesome 1.1.8**

## 📋 Prerequisites

Before running this application, ensure you have the following installed:

- Java Development Kit (JDK) 17 or higher
- Maven 3.6+
- MySQL 8.0+
- Node.js and npm (for frontend development)

## 🗄️ Database Setup

1. **Create MySQL User**
   ```bash
   mysql -u root -p
   ```
   
   Run the user creation script:
   ```bash
   source 01-starter-files/db-scripts/01-create-user.sql
   ```

2. **Create Database and Tables**
   ```bash
   source 01-starter-files/db-scripts/02-create-products.sql
   ```

   This will create:
   - Database: `full-stack-ecommerce`
   - Table: `product_category`
   - Table: `product`
   - Sample data with book products

## ⚙️ Backend Configuration

1. **Navigate to backend directory**
   ```bash
   cd 02-backend/spring-boot-ecommerce
   ```

2. **Configure application properties**
   
   Copy the properties file from starter files:
   ```bash
   cp ../../01-starter-files/spring-boot-properties/application.properties src/main/resources/
   ```

   Default configuration:
   - Database URL: `jdbc:mysql://localhost:3306/full-stack-ecommerce`
   - Username: `ecommerceapp`
   - Password: `ecommerceapp`
   - Base API Path: `/api`

3. **Build the application**
   ```bash
   ./mvnw clean install
   ```

4. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```

   The application will start on `http://localhost:8080`

## 🌐 API Endpoints

The application exposes RESTful endpoints via Spring Data REST:

- **Products**: `http://localhost:8080/api/products`
- **Product Categories**: `http://localhost:8080/api/product-category`

### Example Requests

Get all products:
```bash
curl http://localhost:8080/api/products
```

Get all categories:
```bash
curl http://localhost:8080/api/product-category
```

## 📁 Project Structure

```
ecommerce-project/
├── 01-starter-files/          # Starter files and assets
│   ├── angular-image-assets/  # Image assets for frontend
│   ├── db-scripts/            # Database setup scripts
│   └── spring-boot-properties/ # Configuration files
├── 02-backend/                # Backend application
│   └── spring-boot-ecommerce/ # Spring Boot project
│       ├── src/
│       │   ├── main/java/com/mee632/ecommerce/
│       │   │   ├── config/    # Configuration classes
│       │   │   ├── dao/       # Repository interfaces
│       │   │   ├── entity/    # JPA entities
│       │   │   └── SpringBootEcommerceApplication.java
│       │   └── resources/
│       └── pom.xml
└── 03-frontend/               # Frontend application (Angular)
    └── angualr-ecommerce/     # Angular project
```

## 📦 Database Schema

### Product Category
- `id` (Primary Key)
- `category_name`

### Product
- `id` (Primary Key)
- `sku`
- `name`
- `description`
- `unit_price`
- `image_url`
- `active`
- `units_in_stock`
- `date_created`
- `last_updated`
- `category_id` (Foreign Key)

## 🔧 Development

### Running Tests
```bash
cd 02-backend/spring-boot-ecommerce
./mvnw test
```

### Building for Production
```bash
cd 02-backend/spring-boot-ecommerce
./mvnw clean package
```

The JAR file will be created in the `target/` directory.

## 🚧 Frontend Setup (In Development)

The Angular frontend is currently in development. Once available, instructions will be provided here.

## 📝 Notes

- The application uses Lombok annotations (@Data, @Getter, @Setter) to reduce boilerplate code
- Automatic timestamp tracking is enabled for products (creation and update times)
- The API base path is configured as `/api`
- Cross-Origin Resource Sharing (CORS) may need to be configured for frontend integration

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is available for educational and personal use.

## 👤 Author

**Mee632**

## 🙏 Acknowledgments

- Spring Boot Documentation
- Angular Documentation
- MySQL Documentation
