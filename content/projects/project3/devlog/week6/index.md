+++
title = "Uge 39 – Geoapify API og Integration"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg med **API-integration** i projektet **Maler & Håndværk**.

Jeg ville gøre det muligt for brugeren at søge efter og vælge en rigtig adresse, når der oprettes en `WorkRequest`.

Jeg arbejdede med adresseintegration og endte med at bruge **Geoapify API**, som fungerer som den nuværende løsning i projektet.

## Geoapify API

Når brugeren indtaster en adresse, sender programmet en HTTP request til Geoapify.

Geoapify returnerer adressedata som **JSON**, som derefter behandles i Java.

Processen kan beskrives sådan:

`Adresse → Geoapify API → HTTP Request → JSON → Jackson → AdresseDTO → WorkRequestMenu`

## Implementering

Jeg arbejdede blandt andet med:

- `GeoapifyApi`
- `GeoapifyService`
- `AdresseDTO`
- `WorkRequestMenu`
- HTTP requests
- JSON
- Jackson
- Environment variables

`GeoapifyApi` sender HTTP requests til Geoapify API.

`GeoapifyService` behandler de JSON-data, som API'et returnerer.

**Jackson** bruges til at konvertere JSON-data til Java-objekter, og de nødvendige adressedata gemmes i `AdresseDTO`.

`WorkRequestMenu` bruger derefter dataene til at vise adresseforslag til brugeren.

## Adresseforslag

Når brugeren opretter en arbejdsforespørgsel, kan brugeren skrive en adresse.

Programmet:

1. Sender adressen til Geoapify.
2. Modtager adressedata som JSON.
3. Konverterer JSON-data med Jackson.
4. Viser op til 5 adresseforslag.
5. Lader brugeren vælge den korrekte adresse.
6. Gemmer den valgte adresse i `WorkRequest`.

## API Key

Geoapify kræver en API key.

For at undgå at gemme API-nøglen direkte i kildekoden, gemmer jeg den som en **environment variable**:

`GEOAPIFY_API_KEY`

I Java hentes den med:

```java
System.getenv("GEOAPIFY_API_KEY");
```

På denne måde ligger API-nøglen ikke direkte i kildekoden.

## Resultat

Efter implementeringen kan brugeren indtaste en adresse og få op til 5 relevante adresseforslag fra Geoapify.

Brugeren kan derefter vælge den korrekte adresse, som gemmes sammen med arbejdsforespørgslen.

Jeg har gennem denne funktion arbejdet praktisk med **REST API, HTTP requests, JSON, Jackson, DTO og environment variables**.

---

[← Tilbage til DevLog](/datamatiker-portfolio/projects/project3/devlog/)