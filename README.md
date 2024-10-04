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
