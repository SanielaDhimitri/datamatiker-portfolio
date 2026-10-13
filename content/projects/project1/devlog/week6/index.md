+++
title = "Uge 39 – Geoapify API og Integration"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg med **API-integration** i projektet **Maler & Håndværk**.

Jeg ville gøre det muligt for brugeren at søge efter og vælge en rigtig adresse, når der oprettes en `WorkRequest`.

Jeg arbejdede først med adresseintegration og endte med at bruge **Geoapify API**, som fungerer som den nuværende løsning i projektet.

## Geoapify API

Når brugeren indtaster en adresse, sender programmet en HTTP request til Geoapify.

Geoapify returnerer adressedata som **JSON**, som derefter behandles i Java.

Processen er:

`Geoapify → HTTP Request → JSON → Jackson → AdresseDTO → WorkRequestMenu`

## Hvad jeg arbejdede med

Jeg arbejdede blandt andet med:

- `GeoapifyApi`
- `GeoapifyService`
- `AdresseDTO`
- `WorkRequestMenu`
- HTTP requests
- JSON
- Jackson
- Environment variables

`GeoapifyApi` sender requests til Geoapify API.

`GeoapifyService` behandler de JSON-data, som API'et returnerer, og Jackson bruges til at konvertere data til Java-objekter.

De nødvendige adressedata gemmes i `AdresseDTO`.

## Adresseforslag

Når brugeren opretter en arbejdsforespørgsel, kan brugeren skrive en adresse.

Programmet:

1. Sender adressen til Geoapify.
2. Modtager relevante adresser.
3. Viser op til 5 adresseforslag.
4. Lader brugeren vælge den korrekte adresse.
5. Gemmer den valgte adresse i WorkRequest.

## API Key

Geoapify kræver en API key.

For at undgå at gemme API-nøglen direkte i kildekoden, gemmer jeg den som en environment variable:

`GEOAPIFY_API_KEY`

I Java hentes den med:

```java
System.getenv("GEOAPIFY_API_KEY");