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

```xml
dependencies {
    implementation 'mysql:mysql-connector-java:8.0.33'
}
```
## Step 3: Configure application.properties or application.yml

Spring Boot requires a database configuration to connect to MySQL. Add the following details in your src/main/resources/application.properties file:

### Using application.properties

```
# MySQL Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
spring.datasource.username=your_username
spring.datasource.password=your_password

# Hibernate Dialect for MySQL
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# Hibernate DDL auto configuration
spring.jpa.hibernate.ddl-auto=update

# Optional: Show SQL queries in console
spring.jpa.show-sql=true
```
### Using application.yml
Alternatively, you can use application.yml:

```
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
