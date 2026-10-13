+++
title = "Uge 41 – REST API, Dokumentation og LLM"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg videre med projektet **Maler & Håndværk**.

Jeg arbejdede blandt andet med **REST API, endpoints, API-dokumentation, HTTP-tests, logging og integration af et LLM med Google Gemini API**.

## REST API og endpoints

Jeg arbejdede videre med mit REST API i Javalin.

Jeg har endpoints til **Bookings, Offers og Work Requests**.

### Bookings

- `GET /api/bookings`
- `GET /api/bookings/{id}`
- `POST /api/bookings`
- `PUT /api/bookings/{id}`
- `DELETE /api/bookings/{id}`

### Offers

- `GET /api/offers`
- `GET /api/offers/{id}`
- `POST /api/offers`
- `PUT /api/offers/{id}`
- `DELETE /api/offers/{id}`

### Work Requests

- `GET /api/workrequests`
- `GET /api/workrequests/{id}`
- `POST /api/workrequests`
- `PUT /api/workrequests/{id}/status`
- `DELETE /api/workrequests/{id}`

Mine routes er samlet i en `Routes`-klasse, som forbinder endpoints med de forskellige controllers.

Processen kan beskrives sådan:

`HTTP Request → Route → Controller → DAO → Database`

## API Documentation

Jeg dokumenterede mit REST API i README-filen.

Dokumentationen viser:

- HTTP method
- Endpoint
- Beskrivelse
- HTTP status codes

Jeg dokumenterede blandt andet følgende statuskoder:

| Status | Betydning |
|---|---|
| `200 OK` | Request successful |
| `201 Created` | Resource created |
| `204 No Content` | Resource deleted |
| `400 Bad Request` | Invalid request |
| `404 Not Found` | Resource not found |
| `500 Internal Server Error` | Server error |

## HTTP Testing

Jeg bruger `.http`-filer i IntelliJ til at teste mine endpoints.

Jeg har blandt andet:

- `bookings.http`
- `offers.http`
- `workrequests.http`
- `email.http`
- `chat.http`

Her kan jeg sende HTTP requests direkte fra IntelliJ og kontrollere response og statuskode.

## API Testing

Jeg har også arbejdet med test af REST API'et.

Jeg bruger:

- JUnit
- REST Assured
- Hamcrest

Jeg tester blandt andet:

- GET
- POST
- PUT
- DELETE
- 404 Not Found

## Logging

Applikationen bruger **SLF4J og Logback** til logging.

Jeg logger blandt andet:

- HTTP request method
- Request path
- Request body
- HTTP response status
- Response time
- Exceptions

Logs vises i konsollen og gemmes også i en logfil.

## LLM – Large Language Model

Jeg arbejdede også med **LLM**.

LLM betyder **Large Language Model**.

I mit projekt bruger jeg **Google Gemini** som LLM.

Jeg integrerede Gemini i min Java backend, så kunder kan stille spørgsmål om **DH Maler & Byggeservice**.

## Gemini API Key

For at kommunikere med Gemini API oprettede jeg en API key.

API key'en gemmes som en environment variable:

```text
GEMINI_API_KEY
```

I Java hentes den med:

```java
String geminiApiKey =
        System.getenv("GEMINI_API_KEY");
```

På denne måde ligger API key'en ikke direkte i kildekoden.

## GeminiApi

Jeg lavede klassen `GeminiApi`, som står for kommunikationen med Google Gemini API.

Klassen bruger blandt andet:

- `HttpClient`
- `HttpRequest`
- `HttpResponse`
- `ObjectMapper`

Et spørgsmål sendes til Gemini som en HTTP POST request.

## Business Prompt

Jeg lavede et business prompt med regler, så Gemini fungerer som kundeservice for **DH Maler & Byggeservice**.

Gemini får information om, at virksomheden tilbyder:

- Malerarbejde
- VVS-arbejde
- Elektrikerarbejde
- Reparationer i hus og lejlighed
- Montering af køkkener
- Montering af skabe
- Slibning og behandling af parketgulve
- Arbejde med vinduer

Gemini skal svare på dansk og være venlig og professionel.

Gemini må ikke opfinde priser eller ydelser.

Hvis kunden spørger om en pris, skal Gemini forklare, at prisen afhænger af opgaven, og at kunden kan sende en arbejdsforespørgsel for at få et tilbud.

## Gemini Response

Gemini returnerer sit svar som JSON.

Jeg lavede Java records, som passer til strukturen i Gemini-response:

`GeminiResponse → Candidate → Content → Part → text`

De forskellige records gør det muligt for Jackson at konvertere JSON-response fra Gemini til Java-objekter.

Derefter kan jeg hente selve svaret:

```java
String answer =
        geminiResponse
                .candidates()
                .get(0)
                .content()
                .parts()
                .get(0)
                .text();
```

## ChatService

Jeg lavede en `ChatService`, som ligger mellem `ChatController` og `GeminiApi`.

Strukturen er:

`ChatController → ChatService → GeminiApi`

`ChatService` håndterer logikken for chatfunktionen, mens `GeminiApi` har ansvaret for kommunikationen med det eksterne API.

## ChatController

Jeg lavede en `ChatController`, som modtager kundens spørgsmål fra HTTP-requesten.

Controlleren sender spørgsmålet videre til `ChatService`.

Når svaret kommer tilbage, returnerer controlleren svaret til klienten som JSON.

## Chat Endpoint

Jeg oprettede et nyt REST endpoint:

```text
POST /api/chat/
```

Hele processen kan beskrives sådan:

`Client → Route → ChatController → ChatService → GeminiApi → Gemini LLM → Response`

## Test af Chat API

Jeg tester chatfunktionen i `chat.http`.

Eksempel:

```http
POST http://localhost:7072/api/chat/
Content-Type: application/json

{
  "question": "Kan I hjælpe med VVS arbejde?"
}
```

API'et returnerer:

```text
HTTP/1.1 200 OK
```

og et JSON-response med Geminis svar.

## Hvad jeg arbejdede med

- REST API
- Javalin Routes
- GET, POST, PUT og DELETE
- HTTP status codes
- API documentation
- HTTP testing
- JUnit
- REST Assured
- Hamcrest
- Logging med SLF4J og Logback
- LLM (Large Language Model)
- Google Gemini API
- API key
- Environment variables
- JSON
- Jackson ObjectMapper
- Gemini response records
- Business prompt
- ChatController
- ChatService
- Eksternt API

## Resultat

I denne uge arbejdede jeg videre med at gøre **Maler & Håndværk** til en mere komplet backend-applikation.

Jeg arbejdede med REST endpoints, API-dokumentation, HTTP-tests og logging.

Derudover integrerede jeg **Google Gemini som LLM** og lavede et nyt chat-endpoint, hvor kunder kan stille spørgsmål om virksomhedens ydelser.

Det har givet mig praktisk erfaring med **REST API-udvikling, dokumentation, test, JSON, eksterne API'er og LLM-integration i Java**.

---

[Back to DevLog](/datamatiker-portfolio/projects/project3/devlog/)