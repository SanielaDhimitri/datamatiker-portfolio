+++
title = "Uge 40 – Concurrency og Threads"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg med **concurrency og threads** i projektet **Maler & Håndværk**.

Jeg implementerede en tråd i Booking-funktionaliteten for at arbejde med, hvordan en opgave kan udføres i en separat tråd.

## BookingTask

Jeg lavede en ny klasse `BookingTask`, som implementerer `Runnable`.

`Runnable` betyder, at `BookingTask` er en opgave, som en tråd kan udføre.

## BookingMenu

I `BookingMenu` opretter jeg en `BookingTask` og giver den til en ny `Thread`.

```java
BookingTask task = new BookingTask(booking);
Thread thread = new Thread(task);
thread.start();
```

Processen kan beskrives sådan:

`Booking → BookingTask → Thread → thread.start()`

Når `thread.start()` kaldes, starter Java tråden og udfører `run()`-metoden i `BookingTask`.

## Hvad jeg arbejdede med

- `BookingTask`
- `Runnable`
- `Thread`
- `thread.start()`
- Concurrency i Booking-funktionaliteten

## Resultat

Jeg har fået praktisk erfaring med at oprette og starte en tråd i Java og bruge `Runnable` til at definere den opgave, som tråden skal udføre.


## E-mailfunktionalitet

Jeg arbejdede også med e-mailfunktionaliteten i projektet. Når en arbejdsforespørgsel oprettes, forsøger programmet at sende en e-mail.

Under testen fik jeg fejlen `AuthenticationFailedException (535)`. Det betyder, at SMTP-serveren afviste loginoplysningerne. Jeg undersøgte derfor e-mailkonfigurationen og lærte, at afsenderkontoens oplysninger og SMTP-indstillinger skal være korrekte, før programmet kan sende e-mails.

E-mailfunktionen er en separat del af projektet fra `BookingTask` og tråden.

## Andre emner i uge 40

I undervisningen arbejdede vi også med logging og API-dokumentation. Vi så blandt andet på Logback, exception mapping og validation i Javalin.

Vi arbejdede også med dokumentationsformatet for 3. semester og lavede øvelser i timerne.

---

[← Tilbage](/projects/project1/devlog/)