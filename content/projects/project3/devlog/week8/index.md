
+++
title = "Uge 8 – Sikkerhed, JWT, BCrypt og adgangskontrol"
date = "2026-10-09"
draft = false
+++

## Uge 8 – Sikkerhed, JWT, BCrypt og adgangskontrol

I denne uge har jeg arbejdet med **sikkerhed** i mit Maler & Håndværk REST API-projekt.

Fokus var på **authentication, authorization, BCrypt, JWT og brugerroller**.

### Authentication og Authorization

Jeg har lært forskellen mellem:

- **Authentication** – Kontrollerer, hvem brugeren er.
- **Authorization** – Kontrollerer, hvad brugeren har adgang til.

### Brugerregistrering og BCrypt

Jeg har arbejdet med registrering og login, hvor brugerens adgangskode hashes med **BCrypt**, før den gemmes i databasen.

```java
String hash = BCrypt.hashpw(password, BCrypt.gensalt(12));
boolean valid = BCrypt.checkpw(password, hash);
```

BCrypt gør det muligt at kontrollere adgangskoden uden at gemme den som almindelig tekst.

### JWT – JSON Web Token

Jeg har arbejdet med JWT til sikker adgang til beskyttede endpoints.

Når brugeren logger ind, kan serveren udstede et JWT-token, som sendes med efterfølgende requests.

```http
Authorization: Bearer YOUR_JWT_TOKEN
```

Jeg har også lært om tokenudløb og validering.

### Roller og adgangskontrol

Jeg har arbejdet med to brugerroller:

- **ADMIN** – Kan administrere arbejdsforespørgsler og tilbud.
- **MEDLEM** – Har adgang til funktioner for almindelige registrerede brugere.

Jeg har også lært forskellen mellem offentlige og beskyttede endpoints.

### HTTP-statuskoder

- `200 OK` – Request gennemført.
- `201 Created` – Ressource oprettet.
- `400 Bad Request` – Ugyldige data.
- `401 Unauthorized` – Manglende eller ugyldig authentication.
- `403 Forbidden` – Brugeren har ikke tilladelse.

### Test og udfordringer

Jeg har gennemgået test af login, registrering, ugyldige adgangskoder, JWT-tokens og brugerroller.

En vigtig del var at forstå, hvordan authentication og authorization fungerer sammen.

### Hvad har jeg lært?

Jeg har fået en bedre forståelse af, hvordan man beskytter et REST API med **BCrypt, JWT og rollebaseret adgangskontrol**.

---

[← Tilbage til udviklingsloggen](/datamatiker-portfolio/projects/project3/devlog/)
