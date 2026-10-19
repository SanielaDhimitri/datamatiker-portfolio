
+++
title = "Uge 4 – JPA, Entities, Relationer og PostgreSQL"
date = "2026-09-11"
draft = false
+++

## Uge 4 – JPA, Entities, Relationer og PostgreSQL

I denne uge har jeg arbejdet med **JPA, Hibernate og PostgreSQL** i mit Maler & Håndværk-projekt.

Fokus var på at oprette Entities, implementere relationer og teste databasen.

### JPA og Hibernate

Jeg har lært, hvordan JPA og Hibernate bruges til at gemme Java-objekter i en relationel database.

Jeg har arbejdet med annotationer som:

- `@Entity` – Definerer en database-entity.
- `@Id` – Angiver Primary Key.
- `@GeneratedValue` – Genererer ID automatisk.
- `@Enumerated` – Gemmer enum-værdier.

### Entities og Enums

Jeg har arbejdet med fire centrale Entities:

- **User** – Registrerede brugere.
- **WorkRequest** – Kundernes arbejdsforespørgsler.
- **Service** – Virksomhedens ydelser.
- **Offer** – Tilbud til arbejdsforespørgsler.

Jeg har også brugt `EnumType.STRING` til at gemme statusværdier som tekst.

```java
@Enumerated(EnumType.STRING)
private WorkRequestStatus status;
```

### JPA-relationer

Jeg har arbejdet med:

- **One-to-Many** – En WorkRequest kan have flere Offers.
- **Many-to-One** – Et Offer tilhører én WorkRequest.
- **Many-to-Many** – En WorkRequest kan have flere Services.

Jeg har også arbejdet med en valgfri relation mellem User og WorkRequest, så besøgende kan sende forespørgsler uden login.

### PostgreSQL og EntityManager

Jeg har arbejdet med at forbinde Java-applikationen til PostgreSQL og bruge `EntityManager` til databaseoperationer.

Jeg har lært at bruge transaktioner med `begin()` og `commit()`.

### Database Testing

Jeg har arbejdet med **JUnit og Testcontainers** til at teste databaseoperationer.

Testene omfatter oprettelse, hentning, opdatering og sletning af data samt JPA-relationer.

### Git og GitHub

Jeg har brugt Git og GitHub til at gemme ændringer, oprette commits og pushe projektet til repository.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan **Java Entities, JPA-relationer og PostgreSQL** arbejder sammen.

Jeg har også lært at teste databaseoperationer og bruge Git til versionsstyring.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
