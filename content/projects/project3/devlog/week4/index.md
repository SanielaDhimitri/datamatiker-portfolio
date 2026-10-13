+++
title = "Uge 37 – Service Layer og Menu"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg videre med **Maler & Håndværk** og fokuserede på programmets struktur.

Jeg begyndte at arbejde med **Service Layer**, som ligger mellem Menu-klasserne og DAO-klasserne.

Service-klasserne håndterer programmets logik og bruger DAO-klasserne, når der skal hentes eller gemmes data i databasen.

## Menu-system

Jeg oprettede forskellige Menu-klasser for at gøre programmet mere overskueligt og brugervenligt i konsollen.

Jeg arbejdede blandt andet med:

- `MainMenu`
- `PersonMenu`
- `BookingMenu`
- `WorkRequestMenu`
- `OfferMenu`

`MainMenu` fungerer som programmets hovedmenu, hvor brugeren kan vælge, hvilken del af systemet der skal bruges.

De andre Menu-klasser håndterer funktionaliteten for deres eget område.

## Programmets struktur

Projektet er nu opdelt i forskellige lag:

`Menu → Service → DAO → JPA/Hibernate → PostgreSQL`

- **Menu** – Håndterer brugerens input og valg.
- **Service** – Håndterer programmets logik.
- **DAO** – Håndterer kommunikationen med databasen.
- **JPA/Hibernate** – Mapper Java-objekter til databasen.
- **PostgreSQL** – Gemmer programmets data.

## Resultat

Denne struktur gør programmet mere overskueligt, fordi de forskellige klasser har forskellige ansvarsområder.

Det gør det også lettere at arbejde videre med funktioner som Booking, WorkRequest, Offer og Person.

---

[Back to DevLog](/datamatiker-portfolio/projects/project3/devlog/)