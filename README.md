# Documentations
# Connecting MySQL with Spring Boot

This document explains how to connect a Spring Boot application with a MySQL database.

## Prerequisites

- **JDK** (Java Development Kit) version 8 or higher
- **Spring Boot** (2.0 or higher recommended)
- **MySQL** installed on your local machine or accessible remotely
- **Maven** or **Gradle** for managing dependencies
- **MySQL Connector** dependency added to the project

## Step 1: Add MySQL Dependency

In your `pom.xml` (for Maven) or `build.gradle` (for Gradle), add the MySQL connector dependency.

### Maven

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>
```

For Gradle, add the dependency in your build.gradle:

### Gradle

```gradle
dependencies {
    implementation 'mysql:mysql-connector-java:8.0.33'
}
```
## Step 3: Configure application.properties or application.yml

Spring Boot requires a database configuration to connect to MySQL. Add the following details in your src/main/resources/application.properties file:

### Using application.properties

```PROPERTIES
# MySQL Database Configuration
server.port = 8181
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password

# Hibernate Dialect for MySQL
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQLDialect

# Hibernate DDL auto configuration
spring.jpa.hibernate.ddl-auto=update

spring.datasource.driver-class-name=com.mysql.jdbc.Driver

# Optional: Show SQL queries in console
spring.jpa.show-sql=true
```
### Using application.yml
Alternatively, you can use application.yml:

```yml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/your_database_name
    username: your_username
    password: your_password
  jpa:
    hibernate:
      ddl-auto: update
    properties:
      hibernate:
        dialect: org.hibernate.dialect.MySQL8Dialect
    show-sql: true
```
Replace your_database_name, your_username, and your_password with your actual MySQL database name and credentials.

## Step 4: Create the Database
Ensure that you create the database that you mentioned in the configuration. You can do this using the MySQL command line or a GUI tool like MySQL Workbench.

```SQL
CREATE DATABASE your_database_name;
```

## Step 5: Spring Boot Entity Configuration
Define your entity classes and annotate them with @Entity. Spring Boot will automatically map these to tables in your MySQL database.
### Entity
```JAVA
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;

@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String email;

    // Getters and Setters

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }
}
```

## Step 6: Create a Repository Interface
Create a repository interface to handle database operations for your entity.

### Repository

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
}
```
