
+++
title = "Uge 9 – Concurrency og AI-chat med Gemini API"
date = "2026-10-16"
draft = false
+++

## Uge 9 – Concurrency og AI-chat med Gemini API

I denne uge har jeg arbejdet med at integrere **Google Gemini API** i mit **Maler & Håndværk** REST API-projekt.

Jeg har også arbejdet med **concurrency, threads og baggrundsopgaver** i Java.

### Gemini API

Jeg har arbejdet med at integrere Gemini AI, så brugere kan stille spørgsmål om malerarbejde og håndværksydelser.

Jeg har lært, hvordan en Java-backend sender HTTP-requests til en ekstern API og modtager JSON-responses.

### ChatController og ChatService

Jeg har arbejdet med følgende struktur:

**Client → ChatController → ChatService → GeminiApi → Google Gemini API**

- **ChatController** modtager HTTP-requests og returnerer svar.
- **ChatService** håndterer chatlogikken.
- **GeminiApi** står for HTTP-kommunikationen med Google Gemini.
- **DTO'er** bruges til at overføre data.

### API-nøgle

Jeg har arbejdet med at beskytte API-nøglen ved hjælp af environment variables.

```java
String apiKey = System.getenv("GEMINI_API_KEY");
```

På den måde undgår jeg at gemme API-nøglen direkte i kildekoden.

### Concurrency og Threads

Jeg har arbejdet med `ChatTask`, som implementerer `Callable<String>`.

ExecutorService udfører chatopgaver i en thread pool med 10 worker threads. 
Future bruges til at hente svaret.

Systemet venter højst 30 sekunder. 
Hvis tiden overskrides, forsøges opgaven annulleret, og API’et returnerer `504 Gateway Timeout`.

Flere chatopgaver kan behandles samtidigt, men den enkelte request venter på svaret gennem `Future.get()`.

### Test og fejlhåndtering

Jeg har arbejdet med at forstå, hvordan **ChatService** kan testes med Mockito uden at kalde Gemini API direkte.

Jeg har også gennemgået håndtering af ugyldige requests, manglende API-nøgler og fejl fra eksterne tjenester.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan en Java-backend kommunikerer med eksterne API'er, og hvordan AI kan integreres i et REST API.

Jeg har også lært mere om concurrency, threads og baggrundsopgaver.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
