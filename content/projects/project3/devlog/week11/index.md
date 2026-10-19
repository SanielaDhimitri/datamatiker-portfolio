
+++
title = "Uge 11 – Afsluttende test og projektdokumentation"
date = "2026-10-30"
draft = false
+++

## Uge 11 – Afsluttende test og projektdokumentation

I denne uge har jeg fokuseret på at gennemgå mit **Maler & Håndværk** REST API-projekt og forberede dokumentationen til eksamen.

### Backendarkitektur

Jeg har gennemgået projektets opbygning:

**Routes → Controller → Service → DAO → JPA/Hibernate → PostgreSQL**

Jeg har fået en bedre forståelse af, hvordan de forskellige lag arbejder sammen.

### Test

Jeg har gennemgået følgende testværktøjer:

- **JUnit og Mockito** – Unit tests.
- **REST Assured og Hamcrest** – Test af REST API.
- **Testcontainers** – Integrationstest med PostgreSQL.

### Database og sikkerhed

Jeg har arbejdet med JPA-relationer mellem `User`, `WorkRequest`, `Service` og `Offer`.

Jeg har også gennemgået JWT, BCrypt, authentication og authorization.

### AI og concurrency

Jeg har gennemgået integrationen med Google Gemini API samt brugen af ChatTask, Callable,
ExecutorService og Future til at håndtere samtidige chatopgaver og timeout.

### DevOps

Jeg har arbejdet med Docker, Maven og GitHub Actions.

GitHub Actions bygger projektet med:

`mvn clean package -DskipTests`

Det betyder, at projektet bygges uden at køre tests.

### Dokumentation og eksamensforberedelse

Jeg har opdateret min portfolio med Hugo og gennemgået projektets User Stories, diagrammer, arkitektur og teknologier.

Jeg har også forberedt mig på at forklare projektets funktioner og tekniske løsninger til eksamen.

### Konklusion

Uge 11 har hjulpet mig med at samle min viden fra semesteret og få et bedre overblik over backendudvikling, test, sikkerhed og DevOps.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
