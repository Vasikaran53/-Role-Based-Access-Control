# -Role-Based-Access-Control


This is a Spring Boot-based application designed for user role management. It demonstrates the use of Spring Security for password encoding, role-based access control, and data seeding using JPA repositories. The application also integrates MySQL for data storage.

## Prerequisites

Before running the project, make sure you have the following installed on your system:

- Java 17 or higher
- Maven
- MySQL database (or any other supported database)
- Spring Boot

## Setup Instructions

### 1. Clone the repository

Clone the repository to your local machine:

```bash
git clone  https://github.com/Vasikaran53/-Role-Based-Access-Control.git
cd assignment
```

### 2. Configure Database

Ensure that you have a MySQL database set up. You can create a database called `assignment_dbss` (or modify the `application.properties` to use another database).

```sql
CREATE DATABASE assignment_dba;
```

### 3. Update application.properties

In the `src/main/resources/application.properties` file, update the database connection details:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/assignment_dba
spring.datasource.username=root
spring.datasource.password=your-password
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.security.jwt.secret=yourSecretKey
spring.security.jwt.expiration=86400000
server.port=8090
```

### 4. Build the Project

You can build the project using Maven:

```bash
mvn clean install
```

### 5. Run the Application

To run the application, use the following command:

```bash
mvn spring-boot:run
```

Alternatively, you can run the `AssignmentApplication` class directly from your IDE.

### 6. Access the Application

Once the application is running, you can access the REST endpoints:

- **GET /test/users**: Fetches all users from the database.

#### Example:

```bash
curl http://localhost:8090/test/users
```

### 7. Seeding Roles and Users

The `DataSeeder` class will automatically seed the following roles if they do not exist:

- `ROLE_ADMIN`
- `ROLE_USER`
- `ROLE_MODERATOR`

Additionally, the `UserService` will create two users:

- **Admin User**: `admin` with password `adminPassword`
- **Moderator User**: `moderator` with password `moderator123`

These users are created with appropriate roles for testing purposes.

### 8. Accessing the H2 Database (Optional)

If you need to interact with the H2 database for debugging or testing, enable the console by adding the following to `application.properties`:

```properties
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

Now you can access the H2 console at:

```
http://localhost:8090/h2-console
```

Use the following credentials to log in:

- **JDBC URL**: `jdbc:h2:mem:testdb`
- **Username**: `sa`
- **Password**: `password`

## Folder Structure

- `com.example.assignment`: Root package
  - `controller`: Contains REST controller classes (e.g., `TestController`)
  - `models`: Contains JPA entity classes (e.g., `User`, `Role`)
  - `repositories`: Contains JPA repository interfaces (e.g., `UserRepository`, `RoleRepository`)
  - `services`: Contains service classes for business logic (e.g., `UserService`)
  - `config`: Contains configuration classes (e.g., `AppConfig`, `DataSeeder`)

## Dependencies

- Spring Boot Starter Web
- Spring Boot Starter Security
- Spring Boot Starter Data JPA
- Spring Boot Starter Validation
- MySQL Connector/J

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```

### Explanation of the Structure:

1. **Database Configuration**: Update `application.properties` with correct database credentials.
2. **Role and User Seeding**: `DataSeeder` ensures the necessary roles and users are created on application startup.
3. **Accessing REST API**: The application exposes an endpoint (`/test/users`) to fetch all users. You can test this using `curl` or Postman.
4. **H2 Console (Optional)**: If needed, you can enable the H2 console for debugging purposes.
