
+++
title = "Uge 7 – Routes, HTTP-tests, REST Assured og Fejlhåndtering"
date = "2026-10-02"
draft = false
+++

## Uge 7 – Routes, HTTP-tests, REST Assured og Fejlhåndtering

I denne uge har jeg arbejdet med **Javalin Routes, HTTP-requests, REST Assured, fejlhåndtering og validering** i mit Maler & Håndværk-projekt.

### Javalin Routes

Jeg har lært, hvordan Routes forbinder HTTP-endpoints med Controller-metoder.

**Client → Routes → Controller → Service → DAO → PostgreSQL**

Jeg har arbejdet med HTTP-metoderne:

- **GET** – Henter data.
- **POST** – Opretter data.
- **PUT/PATCH** – Opdaterer data.
- **DELETE** – Sletter data.

### HTTP-tests

Jeg har brugt `.http`-filer i IntelliJ IDEA til at sende requests og kontrollere JSON-responses og statuskoder.

### REST Assured

Jeg har arbejdet med REST Assured til automatiseret test af REST API’et. Testene kontrollerer statuskoder og JSON-svar. Ved beskyttede endpoints sendes et JWT med den nødvendige brugerrolle.

Jeg har lært at bruge:

- `given()` – Forbereder requesten.
- `when()` – Sender requesten.
- `then()` – Kontrollerer svaret.

### JUnit, Hamcrest og CRUD

Jeg har brugt **JUnit** og **Hamcrest** til at kontrollere API'ets funktioner.

Jeg har arbejdet med tests af CRUD-operationer: Create, Read, Update og Delete.

### Fejlhåndtering og validering

Jeg har lært at håndtere ugyldige requests og bruge korrekte HTTP-statuskoder:

- `200 OK` – Request gennemført.
- `201 Created` – Ressource oprettet.
- `400 Bad Request` – Ugyldige data.
- `404 Not Found` – Ressource findes ikke.
- `500 Internal Server Error` – Serverfejl.

Jeg har også arbejdet med validering af input og exception handling i Javalin.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan REST API-endpoints fungerer, og hvordan de testes automatisk med **REST Assured, JUnit og Hamcrest**.

Jeg har også lært, hvorfor validering og fejlhåndtering er vigtige i backendudvikling.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
