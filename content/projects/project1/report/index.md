+++
title = "Project Report"
date = "2026-08-22"
draft = false
+++
![Project Report](img/report.png)
# Villa Room Booking System

**Webapplikation til online booking af værelser**

**3. semesterprojekt : Datamatiker**

- **Studerende:** Saniela Dhimitri
- **Uddannelse:** Datamatiker
- **Semester:** 3. semester
- **Uddannelsessted:** Erhvervsakademi København (EK)
- **Campus:** Lyngby
- **Teknologier:** Java · Spring Boot · PostgreSQL
- **Studieår:** 2026–2027

---

### Indhold

1. Indledning
2. Problemformulering
3. Brugerhistorier (User Stories)
4. Funktionelle krav
5. Ikke-funktionelle krav
6. Domænemodel
7. Klassediagram
8. ER-diagram
9. Sekvensdiagram
10. Systemarkitektur
11. Teknologier
12. Test
13. Konklusion

---
## 1. IndledningAC

Villa Room Booking System er en webapplikation, der udvikles til administration og online booking af værelser i en mindre villa med otte værelser.

Formålet med systemet er at gøre bookingprocessen enkel og overskuelig for både gæster og administratoren.

En gæst skal kunne vælge check-in- og check-out-dato og derefter se, hvilke værelser der er ledige i den ønskede periode. For hvert værelse vises blandt andet billeder, størrelse i m², pris pr. nat, kapacitet og faciliteter såsom Wi-Fi, TV, aircondition og eget badeværelse.

Når gæsten har valgt et værelse, skal vedkommende kunne indtaste sine personlige oplysninger, gennemføre bookingen og betale for opholdet. Efter en gennemført booking modtager gæsten en bekræftelse via e-mail eller SMS.

Systemet skal desuden give mulighed for at annullere en booking efter villaens gældende regler. Efter et afsluttet ophold kan gæsten skrive en anmeldelse og bedømme blandt andet renlighed, komfort, beliggenhed, faciliteter og service.

Administratorens del af systemet skal gøre det muligt at administrere værelser, priser, faciliteter, bookinger, betalinger og anmeldelser.

Applikationen udvikles i Java med Spring Boot og anvender PostgreSQL som relationel database.

---

## 2. Problemformulering

Mindre villaer kan håndtere reservationer manuelt via telefon, SMS eller e-mail. Det kan gøre det vanskeligt at bevare et samlet overblik over ledige værelser, bookinger, betalinger og aflysninger. Det kan samtidig øge risikoen for fejl og dobbeltbookinger.

Projektet tager derfor udgangspunkt i følgende problemformulering:

> **Hvordan kan der udvikles en brugervenlig webapplikation, som gør det muligt for gæster at finde, booke, betale og administrere et ophold i en mindre villa, samtidig med at administratoren får et samlet overblik over værelser, bookinger, betalinger og tilgængelighed?**

Systemet skal sikre, at det samme værelse ikke kan bookes af flere gæster i overlappende perioder.

---

## 3. Brugerhistorier (User Stories)

Brugerhistorierne beskriver de vigtigste funktioner i Villa Room Booking System set fra brugerens perspektiv.

### 3.1 Se ledige værelser : US1

**Som kunde vil jeg kunne se ledige værelser, så jeg kan finde et værelse, der passer til mit ophold.**

**Acceptance Criteria:**

- Systemet viser de 8 værelser opdelt efter dato.
- Ledige værelser er tydeligt markeret.
- Bookede værelser fremgår som optaget.
- Kunden kan vælge check-in- og check-out-dato.
- Systemet viser kun værelser, der er ledige i den valgte periode.
- Systemet viser, hvor mange værelser der er ledige.

**Tasks:**

- Implementere visning af ledige og optagede værelser med filtrering efter check-in- og check-out-dato.
- Implementere kontrol af eksisterende bookinger i databasen.

---

### 3.2 Se information om værelse : US2

**Som kunde vil jeg kunne se information om et værelse, så jeg kan vælge det værelse, der passer bedst til mine behov.**

**Acceptance Criteria:**

- Værelsets nummer eller navn.
- Billeder af værelset.
- Størrelse i m².
- Pris pr. nat.
- Maksimalt antal gæster.
- Faciliteter såsom Wi-Fi, TV, aircondition, eget badeværelse og balkon.
- Værelsets gennemsnitlige rating.

**Tasks:**

- Implementere en detaljeside for hvert værelse med billeder, pris, størrelse, faciliteter og rating.

---

### 3.3 Booke værelse : US3

**Som kunde vil jeg kunne booke et ledigt værelse, så jeg kan reservere det til mit ophold.**

**Acceptance Criteria:**

- Kunden kan vælge et ledigt værelse.
- Kunden kan angive check-in og check-out.
- Kunden kan angive antal gæster.
- Bookingen kan kun gennemføres, hvis værelset er ledigt.
- Det samme værelse kan ikke dobbeltbookes i samme periode.
- Systemet beregner automatisk antal nætter.
- Systemet beregner den samlede pris.

**Tasks:**

- Udvikle bookingfunktionalitet med validering af datoer og ledighed.
- Implementere kontrol mod dobbeltbooking.
- Implementere automatisk beregning af antal nætter og samlet pris.

---

### 3.4 Indtaste kundeoplysninger : US4

**Som kunde vil jeg kunne indtaste mine personlige oplysninger, så bookingen kan registreres i mit navn.**

**Acceptance Criteria:**

- Fornavn.
- Efternavn.
- E-mail.
- Telefonnummer.
- Antal gæster.
- Systemet validerer de nødvendige oplysninger.

**Tasks:**

- Oprette bookingformular.
- Implementere validering af kundeoplysninger.
- Gemme kundeoplysninger sammen med bookingen.

---

### 3.5 Betale booking : US5

**Som kunde vil jeg kunne betale for mit ophold online, så min booking kan bekræftes.**

**Acceptance Criteria:**

- Kunden kan se den samlede pris før betaling.
- Kunden kan gennemføre betalingen.
- Betalingens status registreres.
- Status kan være `PENDING`, `PAID`, `FAILED` eller `REFUNDED`.
- Bookingen bekræftes efter en godkendt betaling.

**Tasks:**

- Implementere betalingsfunktionalitet.
- Gemme betalingsoplysninger og betalingsstatus.
- Knytte betalingen til den korrekte booking.

---

### 3.6 Modtage bookingbekræftelse : US6

**Som kunde vil jeg modtage en bookingbekræftelse via e-mail eller SMS, så jeg har dokumentation for min reservation.**

**Acceptance Criteria:**

Bekræftelsen indeholder:

- Et unikt bookingnummer.
- Kundens navn.
- Værelsesnummer.
- Check-in dato og tidspunkt.
- Check-out dato og tidspunkt.
- Antal nætter.
- Samlet pris.
- Betalingsstatus.
- Villaens adresse.

**Tasks:**

- Generere et unikt bookingnummer.
- Implementere bookingbekræftelse.
- Implementere afsendelse via e-mail og/eller SMS.

---

### 3.7 Annullere booking – US7

**Som kunde vil jeg kunne annullere min booking, så jeg kan afbestille mit ophold, hvis mine planer ændrer sig.**

**Acceptance Criteria:**

- Kunden kan vælge at annullere via sin bookingbekræftelse.
- Bookingen kan annulleres indtil 2 timer før check-in.
- Systemet afviser annulleringen, hvis der er mindre end 2 timer til check-in.
- Bookingens status ændres til `CANCELLED`.
- Værelset bliver igen tilgængeligt for andre kunder.

**Tasks:**

- Implementere annulleringsfunktion.
- Implementere 2-timers-reglen.
- Opdatere bookingstatus og værelsets tilgængelighed.

---

### 3.8 Se min booking – US8

**Som kunde vil jeg kunne se min booking, så jeg kan kontrollere oplysningerne om mit ophold.**

**Acceptance Criteria:**

Kunden kan se:

- Bookingnummer.
- Værelse.
- Check-in og check-out.
- Antal nætter.
- Samlet pris.
- Bookingstatus.
- Betalingsstatus.

**Tasks:**

- Udvikle en side til visning af kundens booking og bookingdetaljer.

---

### 3.9 Skrive anmeldelse – US9

**Som kunde vil jeg kunne skrive en anmeldelse efter mit ophold, så jeg kan dele min oplevelse med andre gæster.**

**Acceptance Criteria:**

- Kun kunder med et afsluttet ophold kan skrive en anmeldelse.
- Kunden kan give 1–5 stjerner.
- Kunden kan bedømme renlighed.
- Kunden kan bedømme komfort.
- Kunden kan bedømme beliggenhed.
- Kunden kan bedømme faciliteter.
- Kunden kan bedømme value for money.
- Kunden kan skrive en kommentar.
- Systemet beregner den gennemsnitlige rating.

**Tasks:**

- Implementere reviewformular.
- Kontrollere, at kunden har gennemført opholdet.
- Gemme ratings og kommentar.
- Beregne og vise gennemsnitlig rating.

---

### 3.10 Administrere værelser – US10

**Som admin vil jeg kunne administrere villaens værelser, så informationen på hjemmesiden altid er opdateret.**

**Acceptance Criteria:**

Admin kan:

- Se alle 8 værelser.
- Oprette og redigere et værelse.
- Ændre pris pr. nat.
- Ændre størrelse og kapacitet.
- Tilføje eller ændre billeder.
- Ændre faciliteter såsom Wi-Fi, TV og aircondition.

**Tasks:**

- Udvikle CRUD-funktionalitet til administration af værelser.

---

### 3.11 Administrere bookinger – US11

**Som admin vil jeg kunne se og administrere bookinger, så jeg har overblik over villaens reservationer.**

**Acceptance Criteria:**

Admin kan:

- Se alle bookinger.
- Se ledige og optagede værelser.
- Søge efter en booking.
- Se bookinger efter dato.
- Se kommende check-ins og check-outs.
- Se bookingstatus.
- Annullere en booking.

**Tasks:**

- Udvikle administrationsside til bookinger med søgning, filtrering og ændring af status.

---

### 3.12 Se Admin Dashboard – US12

**Som admin vil jeg kunne se et dashboard, så jeg hurtigt kan få overblik over villaens aktuelle situation.**

**Acceptance Criteria:**

Dashboardet viser:

- Antal værelser: 8.
- Antal ledige værelser.
- Antal optagede værelser.
- Dagens ankomster.
- Dagens afgange.
- Kommende bookinger.
- Betalinger og omsætning.

**Tasks:**

- Udvikle admin dashboard og hente de nødvendige data fra databasen.


---

## 4. Funktionelle krav

De funktionelle krav beskriver, hvilke funktioner Villa Room Booking System skal kunne udføre.

**Systemet skal kunne:**

- Vise information om villaen og dens kontaktoplysninger.
- Vise villaens værelser.
- Give gæsten mulighed for at søge efter ledige værelser ud fra check-in- og check-out-dato.
- Vise værelsets nummer, billeder, størrelse, kapacitet, pris og faciliteter.
- Vise hvor mange værelser der er ledige i den valgte periode.
- Forhindre dobbeltbookinger.
- Beregne antal overnatninger og den samlede pris automatisk.
- Registrere gæstens oplysninger.
- Oprette og gemme bookinger.
- Registrere betaling og betalingsstatus.
- Generere et unikt bookingnummer.
- Sende bookingbekræftelse via e-mail eller SMS.
- Give gæsten mulighed for at annullere bookingen indtil 2 timer før check-in.
- Give gæsten mulighed for at skrive en anmeldelse og give 1–5 stjerner efter afsluttet ophold.
- Give administratoren mulighed for at administrere værelser, priser, faciliteter, bookinger, betalinger og anmeldelser.
- Gemme relevante oplysninger i databasen.

---

## 5. Ikke-funktionelle krav

Ud over de funktionelle krav stilles der også krav til systemets kvalitet, sikkerhed og brugervenlighed.

### Brugervenlighed

Brugergrænsefladen skal være enkel, overskuelig og nem at forstå for både gæster og administrator.

### Responsivt design

Webapplikationen skal kunne anvendes på computer, tablet og mobiltelefon.

### Sikkerhed

Adgangskoder og kundeoplysninger skal håndteres sikkert.

Administratorfunktioner må kun være tilgængelige for administratoren.

### Pålidelighed

Systemet skal forhindre dobbeltbookinger og sikre, at oplysninger om værelser, bookinger og betalinger er korrekte.

### Vedligeholdelse

Applikationen skal anvende en tydelig lagdelt arkitektur med Controller, Service og Repository, så koden er struktureret og nemmere at vedligeholde.

### Ydeevne

Søgning efter ledige værelser og gennemførelse af bookinger skal ske inden for rimelig tid.

### Validering

Brugerens input, såsom navn, e-mail, telefonnummer, datoer og antal gæster, skal valideres, før oplysningerne gemmes.

---



## 6. Domænemodel

Domænemodellen beskriver de vigtigste begreber i Villa Room Booking System og relationerne mellem dem.

De centrale domæneklasser er:

- User
- Role
- Room
- Booking
- Payment
- Review
- Amenity
- RoomImage
- RoomAmenity

En kunde kan have flere bookinger, mens hver booking tilhører én kunde. Et værelse kan have flere bookinger på forskellige tidspunkter, men systemet skal sikre, at bookingerne ikke overlapper hinanden.

Et værelse kan have flere faciliteter, såsom Wi-Fi, TV og aircondition, og den samme facilitet kan være tilknyttet flere værelser. Derfor anvendes `RoomAmenity` som en join-klasse mellem `Room` og `Amenity`.

En booking er knyttet til et værelse og en kunde og kan desuden være forbundet med en betaling og en anmeldelse.

### Domænemodel

Herunder vises projektets domænemodel:

![Domænemodel](/datamatiker-portfolio/images/domain-model.png)

---

## 7. Klassediagram

Klassediagrammet beskriver de Java-klasser, der anvendes til at implementere Villa Room Booking System.

De vigtigste klasser er:

- User
- Role
- Room
- Booking
- Payment
- Review
- Amenity
- RoomImage
- RoomAmenity

Diagrammet viser klassernes vigtigste attributter samt relationerne mellem klasserne og deres kardinalitet, for eksempel one-to-many og many-to-many.

`RoomAmenity` fungerer som en join-klasse mellem `Room` og `Amenity` og håndterer many-to-many-relationen mellem værelser og faciliteter.

Java-klasserne mappes til tabeller i PostgreSQL-databasen ved hjælp af JPA/Hibernate.

### Klassediagram 7a

![Klassediagram 7a](/datamatiker-portfolio/images/class-diagram-1.png)

### Klassediagram 7b

![Klassediagram 7b](/datamatiker-portfolio/images/class-diagram-2.png)


---

## 8. ER-diagram

ER-diagrammet (Entity Relationship Diagram) viser strukturen i Villa Room Booking System-databasen og relationerne mellem de forskellige tabeller.

De vigtigste tabeller er:

- users
- roles
- rooms
- bookings
- payments
- reviews
- amenities
- room_images
- room_amenities

Hver tabel har en **Primary Key (PK)**, som identificerer hver række entydigt.

**Foreign Keys (FK)** bruges til at skabe relationer mellem tabellerne. For eksempel er en booking knyttet til både en kunde og et værelse.

Tabellen `room_amenities` fungerer som en join-tabel mellem `rooms` og `amenities`. Dette gør det muligt at implementere en many-to-many-relation, hvor et værelse kan have flere faciliteter, og den samme facilitet kan være tilknyttet flere værelser.

### ER-diagram

Herunder vises projektets ER-diagram:

![ER-diagram](/datamatiker-portfolio/images/er-diagram.png)

---

## 9. Sekvensdiagram

Sekvensdiagrammet viser, hvordan de forskellige dele af systemet kommunikerer med hinanden under en booking.

Diagrammet beskriver processen fra det tidspunkt, hvor kunden søger efter et ledigt værelse, til bookingen bliver oprettet og bekræftet.

Bookingprocessen foregår overordnet således:

1. Kunden vælger check-in- og check-out-dato.
2. Systemet søger efter ledige værelser.
3. Kunden vælger et værelse.
4. Kunden indtaster sine personlige oplysninger.
5. Systemet kontrollerer, at værelset stadig er ledigt.
6. Bookingen oprettes.
7. Betalingen registreres.
8. Kunden modtager en bookingbekræftelse.

Sekvensdiagrammet viser kommunikationen mellem blandt andet brugergrænsefladen, Controller, Service, Repository og databasen.

### Sekvensdiagram

Herunder vises projektets sekvensdiagram:

![Sekvensdiagram](/datamatiker-portfolio/images/sequence-diagram.png)

---

## 10. Systemarkitektur

Villa Room Booking System opbygges med en lagdelt arkitektur. Formålet er at adskille de forskellige ansvarsområder i applikationen, så systemet bliver mere overskueligt og lettere at vedligeholde.

Systemet består af følgende lag:

### Controller

Controller-laget modtager HTTP-requests fra brugeren og sender dem videre til Service-laget.

### Service

Service-laget indeholder systemets forretningslogik. Her håndteres blandt andet bookingregler, kontrol af ledige værelser, prisberegning og validering.

### Repository

Repository-laget står for kommunikationen med databasen og bruges til at hente, gemme, opdatere og slette data.

### Database

PostgreSQL anvendes som relationel database til at gemme blandt andet brugere, værelser, bookinger, betalinger og anmeldelser.

Systemets overordnede struktur er:

**Browser → Controller → Service → Repository → PostgreSQL**

### Systemarkitektur

Herunder vises systemets arkitekturdiagram:

![Systemarkitektur](/datamatiker-portfolio/images/system-architecture.png)

---

## 11. Teknologier

Villa Room Booking System udvikles med en række teknologier til backend, database og versionsstyring.

### Java

Java anvendes som det primære programmeringssprog til udvikling af applikationens backend og forretningslogik.

### Spring Boot

Spring Boot anvendes til at opbygge webapplikationen og strukturere systemet i Controller-, Service- og Repository-lag.

### JPA / Hibernate

JPA og Hibernate anvendes til Object-Relational Mapping (ORM), så Java-objekter kan gemmes og hentes fra databasen.

### PostgreSQL

PostgreSQL anvendes som relationel database til blandt andet brugere, værelser, bookinger, betalinger og anmeldelser.

### Maven

Maven anvendes til dependency management og til at administrere projektets biblioteker og dependencies.

### Git og GitHub

Git anvendes til versionsstyring af projektet, mens GitHub bruges til at gemme projektets repository online og følge ændringer i kildekoden.

### Docker

Docker kan anvendes til at køre PostgreSQL-databasen i et isoleret og ensartet udviklingsmiljø.

### IntelliJ IDEA

IntelliJ IDEA anvendes som udviklingsmiljø til programmering, test og arbejde med projektets kode.

### Technology Stack

Herunder vises en samlet oversigt over de teknologier og værktøjer, der anvendes i projektet:

![Villa Room Booking Technology Stack](/datamatiker-portfolio/images/technology-stack.png)

---

## 12. Test

Test er en vigtig del af udviklingen af Villa Room Booking System. Formålet er at kontrollere, at systemets funktioner virker korrekt, og at fejl opdages så tidligt som muligt.

I projektet anvendes både **Unit Tests** og **Integration Tests**.

### Unit Tests

Unit tests anvendes til at teste enkelte dele af applikationen isoleret.

JUnit 5 anvendes til at skrive og køre testene, mens Mockito kan anvendes til at mocke dependencies, så forretningslogikken kan testes uden at være afhængig af den rigtige database.

Der kan blandt andet testes:

- Beregning af antal overnatninger.
- Beregning af samlet pris.
- Validering af check-in- og check-out-datoer.
- Kontrol af bookingstatus.
- Regler for annullering af en booking.
- Kontrol af dobbeltbooking.

### Integration Tests

Integration tests anvendes til at kontrollere, at flere dele af systemet fungerer korrekt sammen.

Der kan blandt andet testes:

- Oprettelse og lagring af data i databasen.
- Hentning af data fra databasen.
- Opdatering og sletning af data.
- Repository- og databasefunktionalitet.
- Oprettelse og hentning af bookinger.
- Kontrol af ledige værelser.
- Relationer mellem systemets entities.

Integration tests er vigtige, fordi de kontrollerer samspillet mellem applikationen og databasen og sikrer, at de forskellige dele af systemet fungerer korrekt sammen.

### Test af booking

Et af de vigtigste testområder er bookingprocessen.

Systemet skal kontrollere, om der allerede eksisterer en booking for det valgte værelse i den ønskede periode.

Hvis perioderne overlapper hinanden, skal den nye booking afvises. Dette sikrer, at det samme værelse ikke kan bookes af flere gæster på samme tidspunkt.


---

## 13. Konklusion

Villa Room Booking System har til formål at udvikle en brugervenlig og struktureret webapplikation til online booking af værelser i en mindre villa.

Systemet giver gæster mulighed for at søge efter ledige værelser, se information om værelserne, oprette en booking, betale for opholdet og modtage en bookingbekræftelse. Derudover kan gæster administrere deres booking og skrive en anmeldelse efter afsluttet ophold.

For administratoren giver systemet mulighed for at administrere værelser, bookinger, priser, faciliteter, betalinger og anmeldelser.

Projektet anvender en lagdelt arkitektur med Controller, Service og Repository samt PostgreSQL som relationel database. JPA/Hibernate anvendes til kommunikationen mellem Java-applikationen og databasen.

Unit tests og integration tests anvendes til at kontrollere systemets funktionalitet og samspillet mellem de forskellige dele af applikationen.

Projektet giver dermed praktisk erfaring med udvikling af en komplet webapplikation, herunder systemdesign, databasedesign, backend-udvikling, test og versionsstyring.




[← Back](/datamatiker-portfolio/projects/project1/)
