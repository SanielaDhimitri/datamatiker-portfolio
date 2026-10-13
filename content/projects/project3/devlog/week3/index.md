+++
title = "Uge 36 – DAO og CRUD Operations"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg videre med **Maler & Håndværk** og begyndte at implementere **DAO-laget**.

DAO står for **Data Access Object** og bruges til at håndtere kommunikationen mellem Java-programmet og databasen.

Jeg oprettede DAO-klasser til de forskellige dele af systemet, så databasekoden er adskilt fra resten af programmet.

## Hvad jeg arbejdede med

Jeg arbejdede blandt andet med:

- `BookingDAO`
- `PersonDAO`
- `ServiceDAO`
- `WorkRequestDAO`
- `OfferDAO`

Jeg implementerede også **CRUD-operationer**.

CRUD står for:

- **Create** – Oprette nye data.
- **Read** – Hente data fra databasen.
- **Update** – Opdatere eksisterende data.
- **Delete** – Slette data.

## Databasekommunikation

DAO-klasserne bruger **JPA/Hibernate** til at kommunikere med PostgreSQL-databasen.

Jeg arbejdede med `EntityManager` og transactions til at gemme, hente, ændre og slette data.

Strukturen begynder derfor at blive:

`Java Application → DAO → JPA/Hibernate → PostgreSQL`

## Resultat

Efter denne uge kunne programmet begynde at arbejde med data i databasen gennem DAO-klasserne.

Det gav en bedre struktur i projektet, fordi databasekommunikationen blev samlet i sit eget lag.

---

[Back to DevLog](/datamatiker-portfolio/projects/project3/devlog/)