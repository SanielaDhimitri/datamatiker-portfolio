+++
title = "Technologies"
draft = false

[build]
list = "never"
+++

The **Villa Room Booking System** is developed using several technologies for the backend, database, persistence and project management.

These technologies help keep the application structured, maintainable and connected to the database.

## Technology Stack

![Technology Stack](/images/technology-stack.png)

The project uses a combination of **Java, JPA/Hibernate, PostgreSQL, Maven and Git/GitHub**.

### Java

**Java** is the main programming language used to develop the application.

It is used to create the classes, entities, business logic and functionality of the Villa Room Booking System.

### JPA and Hibernate

**JPA (Jakarta Persistence API)** is used to manage the communication between Java objects and the relational database.

**Hibernate** is used as the JPA implementation and helps map Java entities to database tables.

This makes it possible to store, retrieve, update and delete data using Java objects.

### PostgreSQL

**PostgreSQL** is the relational database used by the application.

It stores the data needed by the booking system, such as rooms, users and bookings.

### Maven

**Maven** is used for project management and dependencies.

The `pom.xml` file contains the libraries and dependencies required by the application.

### Git and GitHub

**Git** is used for version control during development.

**GitHub** is used to store the project repository and keep track of changes to the source code.

## System Architecture

![System Architecture](/images/system-architecture.png)

The application is organized into different layers so that each part of the system has a clear responsibility.

The **entities** represent the data in the application, while the **DAO layer** handles communication with the database.

The **service and business logic** manage the rules and functionality of the system, while the user interface allows users to interact with the application.

This separation makes the project easier to understand, test and maintain.

---

[← Back](/projects/project1/)