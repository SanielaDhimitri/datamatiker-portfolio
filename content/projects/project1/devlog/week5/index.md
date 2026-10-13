+++
title = "Uge 38 – Funktionalitet og Tests"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg videre med funktionaliteten i **Maler & Håndværk**.

Jeg fokuserede på at få de forskellige dele af programmet til at fungere sammen og testede kommunikationen mellem Java-programmet og databasen.

## Funktionalitet

Jeg arbejdede videre med flere af projektets centrale funktioner:

- `Booking`
- `WorkRequest`
- `Offer`
- `Person`
- `Service`

Jeg arbejdede blandt andet med at oprette, hente og ændre data gennem Menu-, Service- og DAO-lagene.

Jeg arbejdede også med **validation og error handling**, så programmet bedre kan håndtere ugyldige input og fejl.

## Tests

Jeg lavede tests til mine DAO-klasser for at kontrollere, at kommunikationen med databasen fungerer korrekt.

Jeg testede blandt andet:

- `BookingDAO`
- `OfferDAO`
- `PersonDAO`
- `ServiceDAO`
- `WorkRequestDAO`

Testene bruges til at kontrollere, at data kan oprettes, hentes, opdateres og slettes korrekt i databasen.

## Debugging

Under arbejdet fandt jeg også forskellige fejl i programmet.

Jeg brugte debugging og fejlmeddelelser til at finde årsagen til problemerne og rette dem.

Det hjalp mig med at forstå bedre, hvordan de forskellige lag i programmet arbejder sammen.

## Resultat

Efter denne uge var flere af projektets centrale funktioner forbundet med databasen og testet.

Projektets struktur var nu:

`Menu → Service → DAO → JPA/Hibernate → PostgreSQL`

---

[← Tilbage](/projects/project1/devlog/)