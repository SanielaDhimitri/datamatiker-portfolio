+++
title = "Uge 40 – Concurrency og Threads"
draft = false

[build]
list = "never"
+++

I denne uge arbejdede jeg med **concurrency og threads** i projektet **Maler & Håndværk**.

Jeg arbejdede med threads på to forskellige måder. I Booking-funktionaliteten brugte jeg `Thread` og `Runnable`, og i `AdminMenu` brugte jeg `ExecutorService` og `Future` til at udføre flere databaseopgaver samtidigt.

## BookingTask

Jeg lavede en klasse `BookingTask`, som implementerer `Runnable`.

`Runnable` bruges til at definere en opgave, som en tråd kan udføre.

I `BookingMenu` opretter jeg en `BookingTask` og giver den til en ny `Thread`.

```java
BookingTask task = new BookingTask(booking);
Thread thread = new Thread(task);
thread.start();
```

Processen kan beskrives sådan:

`Booking → BookingTask → Thread → thread.start()`

Når `thread.start()` kaldes, starter Java tråden og udfører `run()`-metoden i `BookingTask`.

## Concurrency i AdminMenu

Jeg implementerede også concurrency i `AdminMenu`.

Når administratoren åbner menuen, skal programmet hente antal bookinger, arbejdsforespørgsler, tilbud, personer, services og projekter fra databasen.

Til dette bruger jeg en `ExecutorService` med en fixed thread pool på 5 threads.

```java
ExecutorService executor =
        Executors.newFixedThreadPool(5);
```

Jeg sender derefter 6 forskellige tasks til `ExecutorService`.

```java
Future<Long> bookingFuture =
        executor.submit(() -> bookingDAO.count());

Future<Long> workRequestFuture =
        executor.submit(() -> workRequestDAO.count());

Future<Long> offerFuture =
        executor.submit(() -> offerDAO.count());

Future<Long> personFuture =
        executor.submit(() -> personDAO.count());

Future<Long> serviceFuture =
        executor.submit(() -> serviceDAO.count());

Future<Long> projectFuture =
        executor.submit(() -> projectDAO.count());
```

Der er **5 worker threads og 6 tasks**. Det betyder, at op til 5 tasks kan arbejde samtidigt, mens den sidste task venter på, at en thread bliver ledig.

## Future

Resultaterne fra de forskellige tasks gemmes i `Future<Long>`.

Jeg bruger derefter `.get()` til at hente resultaterne:

```java
long antalBookinger = bookingFuture.get();
long antalWorkRequests = workRequestFuture.get();
long antalTilbud = offerFuture.get();
long antalPersoner = personFuture.get();
long antalServices = serviceFuture.get();
long antalProjekter = projectFuture.get();
```

Resultaterne bliver derefter vist i admin-oversigten.

## Hvad jeg arbejdede med

- `BookingTask`
- `Runnable`
- `Thread`
- `thread.start()`
- `ExecutorService`
- `Executors.newFixedThreadPool(5)`
- `Future`
- `submit()`
- `get()`
- Concurrency i `BookingMenu`
- Concurrency i `AdminMenu`

## Resultat

Jeg har arbejdet med to forskellige måder at bruge threads i Java.

I `BookingMenu` opretter og starter jeg selv en `Thread`.

I `AdminMenu` bruger jeg `ExecutorService`, som administrerer en pool af threads og udfører flere databaseopgaver concurrent.

Det har givet mig praktisk erfaring med **threads, tasks, thread pools, Future og concurrency** i Java.

---

[Back to DevLog](/datamatiker-portfolio/projects/project3/devlog/)