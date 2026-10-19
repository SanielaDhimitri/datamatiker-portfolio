
+++
title = "Uge 5 – REST API, Concurrency, Threads og Dataintegration"
date = "2026-09-18"
draft = false
+++

## Uge 5 – REST API, Concurrency, Threads og Dataintegration

I denne uge har jeg arbejdet med **REST API, Javalin, HTTP, JSON og Concurrency** i mit Maler & Håndværk-projekt.

### REST API og Javalin

Jeg har lært, hvordan et REST API kommunikerer med klienter gennem HTTP-requests og responses.

Jeg har arbejdet med følgende HTTP-metoder:

- **GET** – Henter data.
- **POST** – Opretter data.
- **PUT/PATCH** – Opdaterer data.
- **DELETE** – Sletter data.

Jeg har også arbejdet med **Javalin** til at oprette endpoints.

```java
Javalin app = Javalin.create();

app.get("/", ctx -> ctx.result("Maler & Håndværk API"));

app.start(7070);
```

### JSON og Database

Jeg har arbejdet med JSON til at sende og modtage data mellem klienten og serveren.

Jeg har også lært, hvordan Javalin, JPA/Hibernate og PostgreSQL arbejder sammen.

**Client → Javalin → Java → JPA/Hibernate → PostgreSQL**

### Concurrency og Threads

Jeg har arbejdet med klassen `ChatTask`,
som implementerer `Callable<String>`.

ChatTask sender kundens spørgsmål til ChatService og returnerer svaret. 
ExecutorService udfører opgaven i en thread, og Future bruges til at hente svaret.

På den måde kan systemet behandle flere chatopgaver samtidigt.

### Dataintegration

Jeg har arbejdet med Google Gemini API gennem ChatService. 
Kundens spørgsmål sendes til det eksterne API, 
og svaret returneres til klienten.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan REST API'er fungerer, og hvordan data sendes mellem Java og PostgreSQL.

Jeg har også lært, hvordan **Threads og Concurrency** bruges til at håndtere flere opgaver i en backendapplikation.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
