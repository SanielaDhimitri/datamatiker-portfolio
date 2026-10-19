+++
title = "Uge 6 – DAO, CRUD, DTO, Mapper og Service"
date = "2026-09-25"
draft = false
+++

## Uge 6 – DAO, CRUD, DTO, Mapper og Service

I denne uge har jeg arbejdet med at organisere backendkoden i mit **Maler & Håndværk**-projekt.

### DAO og CRUD

Jeg har arbejdet med DAO-laget, som kommunikerer med PostgreSQL gennem JPA/Hibernate.

Jeg har brugt EntityManager til CRUD-operationer:

- **Create** – Oprette data med `persist()`.
- **Read** – Hente data med `find()`.
- **Update** – Opdatere data med `merge()` eller ændre en managed entity.
- **Delete** – Slette data med `remove()`.

### DTO og Mapper

Jeg har arbejdet med DTO’er til at modtage og returnere data gennem REST API’et.

En Mapper konverterer mellem Entities og DTO’er, så databaseobjekterne holdes adskilt fra API’ets requests og responses.

### Service-laget

Service-laget indeholder forretningslogik og validering.
Det forbinder Controller-laget med DAO-laget.

Projektets struktur er:

**Klient → Routes → Controller → Service → DAO → PostgreSQL**

Jeg har også arbejdet med at give klasser deres afhængigheder gennem konstruktører, så de bliver lettere at teste.

### Concurrency

Jeg har arbejdet videre med concurrency og undersøgt, 
hvordan flere requests kan behandles samtidigt.
Jeg har især haft fokus på problemer, der kan opstå,
når flere threads ændrer fælles data.

### Test

Jeg har arbejdet med DAO-tests til databaseoperationer 
og Service-tests til forretningslogikken.
JUnit og Mockito bruges til at teste de enkelte dele.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af ansvarsfordelingen mellem DAO,
DTO, Mapper, Service og Controller. 
Det gør koden mere overskuelig og lettere at vedligeholde og teste.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)