+++
title = "Uge 35 – Database Design og JPA"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg videre med **Maler & Håndværk** og begyndte at opbygge databasen til projektet.

Jeg arbejdede med **PostgreSQL** som database og brugte **JPA/Hibernate** til at forbinde Java-programmet med databasen.

Jeg begyndte at oprette de vigtigste **entities**, som repræsenterer data i systemet.

Jeg arbejdede blandt andet med:

- `Person`
- `Bruger`
- `Admin`
- `Medarbejder`
- `Service`
- `Booking`
- `WorkRequest`

Jeg begyndte også at arbejde med relationerne mellem de forskellige entities. For eksempel skal en booking kunne være forbundet med en bruger og en service.

## Hvad jeg arbejdede med

- **PostgreSQL** – Bruges som database til projektet.
- **JPA/Hibernate** – Bruges til kommunikationen mellem Java og databasen.
- **Entities** – Oprettede de første klasser, som repræsenterer data i databasen.
- **Relationships** – Arbejdede med relationer mellem entities.
- **Database Design** – Arbejdede videre med strukturen af databasen.

## JPA

Jeg brugte forskellige JPA-annotations, blandt andet:

- `@Entity`
- `@Id`
- `@GeneratedValue`
- `@ManyToOne`
- `@OneToMany`

JPA gør det muligt at arbejde med Java-objekter, mens Hibernate håndterer kommunikationen med databasen.

## Projektets struktur

I denne uge begyndte projektet at gå fra planlægning og diagrammer til en rigtig Java-applikation med database og entities.

---

[Back to DevLog](/datamatiker-portfolio/projects/project3/devlog/)