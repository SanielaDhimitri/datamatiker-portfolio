
+++
title = "Uge 10 – DevOps, Docker og GitHub Actions"
date = "2026-10-23"
draft = false
+++

## Uge 10 – DevOps, Docker og GitHub Actions

I denne uge har jeg arbejdet med **DevOps, Docker, Maven og GitHub Actions** i mit Maler & Håndværk-projekt.

Fokus var på at forstå containere, automatisering og build-processen i Java.

### DevOps og Docker

Jeg har lært, hvordan DevOps bruges til at automatisere udviklingsprocessen.

Jeg har arbejdet med **Docker Desktop** og undersøgt forskellen mellem Docker Image, Container og Docker Engine.

Jeg har også brugt Docker i forbindelse med PostgreSQL og Testcontainers til databasetests.

### Maven

Jeg har brugt Maven til at håndtere dependencies og bygge projektet.

```bash
mvn compile
mvn test
mvn clean package
```

Maven bruger `pom.xml` til projektets dependencies og konfiguration.

### Git og GitHub

Jeg har brugt Git til versionsstyring og GitHub til at gemme projektet.

```bash
git add .
git commit -m "Update project"
git push
```

### GitHub Actions – CI

Jeg har arbejdet med GitHub Actions til at automatisere build-processen.

Workflowet bruger **Java 25, Eclipse Temurin og Maven** og starter ved push eller pull request til `main`.

```bash
mvn clean package -DskipTests
```

Kommandoen bygger projektet uden at køre tests.

### Udfordringer

Jeg har arbejdet med at:

- Kontrollere Docker Desktop og Docker Engine.
- Løse Maven- og buildproblemer.
- Kontrollere Java-versioner og dependencies.
- Pushe ændringer til GitHub.
- Kontrollere GitHub Actions-workflowet.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan Docker, Maven og GitHub Actions arbejder sammen.

Jeg har også lært, hvordan **Continuous Integration (CI)** kan automatisere builds og opdage fejl i projektet.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
