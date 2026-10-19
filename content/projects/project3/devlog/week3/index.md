
+++
title = "Uge 3 – Databasedesign, ER-diagram og Domænemodel"
date = "2026-09-04"
draft = false
+++

## Uge 3 – Databasedesign, ER-diagram og Domænemodel

I denne uge har jeg arbejdet med at designe databasen til mit **Maler & Håndværk** REST API-projekt.

Fokus var på **Entities, relationer, ER-diagram og Domænemodel**.

### Databasedesign

Jeg har identificeret fire centrale Entities:

- **User** – Registrerede brugere og administratorer.
- **WorkRequest** – Kundernes arbejdsforespørgsler.
- **Service** – Virksomhedens ydelser.
- **Offer** – Tilbud til kunder.

### Relationer mellem Entities

Jeg har arbejdet med følgende relationer:

- **One-to-Many:** En User kan have flere WorkRequests.
- **Many-to-Many:** En WorkRequest kan indeholde flere Services.
- **One-to-Many:** En WorkRequest kan have flere Offers.

Jeg har også planlagt, at kunder kan sende arbejdsforespørgsler uden at oprette en bruger.

### ER-diagram 

Jeg har arbejdet med ER-diagram, som viser databasetabeller, nøgler og relationer.

### Primary Key og Foreign Key

Jeg har lært forskellen mellem:

- **Primary Key (PK)** – Identificerer en række i databasen.
- **Foreign Key (FK)** – Forbinder data mellem tabeller.

Jeg har også arbejdet med databasenormalisering for at undgå unødvendige gentagelser af data.

### Forberedelse til JPA og Hibernate

Jeg har planlagt, hvordan Entities og relationer senere skal implementeres med JPA-annotationer som:

`@Entity`, `@Id`, `@OneToMany`, `@ManyToOne` og `@ManyToMany`.

### Domænemodel

Jeg har arbejdet med en domænemodel, som viser systemets vigtigste begreber: **User, WorkRequest, Service og Offer**.

Modellen viser, hvordan en bruger kan have flere arbejdsforespørgsler, 
og hvordan en arbejdsforespørgsel kan indeholde flere ydelser og have flere tilbud.

### Hvad har jeg lært?

Jeg har lært at designe en relationel database og beskrive relationerne mellem systemets vigtigste objekter.

Jeg har også udarbejdet et ER-diagram og en domænemodel, som jeg har indsat i projektrapporten.

Arbejdet har givet mig et godt grundlag for at implementere JPA Entities og PostgreSQL i næste uge.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
