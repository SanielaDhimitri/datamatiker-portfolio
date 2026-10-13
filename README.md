# Datamatiker-portfolio

Dette repository indeholder min portfolio som datamatikerstuderende. Her præsenterer jeg mine studieprojekter og dokumenterer min læring og udvikling gennem semesteret.

## Hovedprojekt

### Maler & Håndværk

Maler & Håndværk er et projekt om håndtering af maler- og håndværksydelser. I portfolioen præsenterer jeg projektets funktionalitet, dokumentation og udvikling.

## DevLog

I min DevLog dokumenterer jeg udviklingen af Maler & Håndværk uge for uge. Her beskriver jeg, hvad jeg har arbejdet med, hvilke teknologier jeg har brugt, hvilke udfordringer jeg har mødt, og hvad jeg har lært.

## Portfolioens indhold

- Projektet Maler & Håndværk
- Ugentlige DevLog-indlæg
- Projektdokumentation
- Diagrammer
- Teknologier og værktøjer

## Teknologier

Portfolioen er bygget med:

- Hugo
- Blowfish
- Markdown
- HTML
- CSS
- Git og GitHub


## UML Sekvensdiagram

Sekvensdiagrammet viser, hvordan klasserne kommunikerer med hinanden i en bestemt rækkefølge.

Eksempel: Oprettelse af WorkRequest

Kunden sender en POST-request til /api/workrequests.

Routes sender requesten videre til WorkRequestController.

Controller kalder WorkRequestService.

Service kalder WorkRequestDAO.

DAO gemmer WorkRequest i PostgreSQL via JPA/Hibernate.

Resultatet sendes tilbage gennem lagene.

Kunden modtager HTTP-status 201 Created og et JSON-svar.

Kort sagt: Sekvensdiagrammet viser, hvordan en HTTP-request bevæger sig gennem applikationens lag og tilbage til klienten.



## Forfatter

**Saniela Dhimitri**  
Datamatikerstuderende



