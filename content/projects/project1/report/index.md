+++
title = "Project Report"
date = "2026-08-22"
draft = false
+++
![Project Report](img/report.png)
# Villa Room Booking System

**Webapplikation til online booking af vÃ¦relser**

**3. semesterprojekt â€“ Datamatiker**

- **Studerende:** Saniela Dhimitri
- **Uddannelse:** Datamatiker
- **Semester:** 3. semester
- **Uddannelsessted:** Erhvervsakademi KÃ¸benhavn (EK)
- **Campus:** Lyngby
- **Teknologier:** Java Â· Spring Boot Â· PostgreSQL
- **StudieÃ¥r:** 2026â€“2027

---

### Indhold

1. Indledning
2. Problemformulering
3. Brugerhistorier (User Stories)
4. Funktionelle krav
5. Ikke-funktionelle krav
6. DomÃ¦nemodel
7. Klassediagram
8. ER-diagram
9. Sekvensdiagram
10. Systemarkitektur
11. Teknologier
12. Test
13. Konklusion

---
## 1. Indledning

Villa Room Booking System er en webapplikation, der udvikles til administration og online booking af vÃ¦relser i en mindre villa med otte vÃ¦relser.

FormÃ¥let med systemet er at gÃ¸re bookingprocessen enkel og overskuelig for bÃ¥de gÃ¦ster og administratoren.

En gÃ¦st skal kunne vÃ¦lge check-in- og check-out-dato og derefter se, hvilke vÃ¦relser der er ledige i den Ã¸nskede periode. For hvert vÃ¦relse vises blandt andet billeder, stÃ¸rrelse i mÂ², pris pr. nat, kapacitet og faciliteter sÃ¥som Wi-Fi, TV, aircondition og eget badevÃ¦relse.

NÃ¥r gÃ¦sten har valgt et vÃ¦relse, skal vedkommende kunne indtaste sine personlige oplysninger, gennemfÃ¸re bookingen og betale for opholdet. Efter en gennemfÃ¸rt booking modtager gÃ¦sten en bekrÃ¦ftelse via e-mail eller SMS.

Systemet skal desuden give mulighed for at annullere en booking efter villaens gÃ¦ldende regler. Efter et afsluttet ophold kan gÃ¦sten skrive en anmeldelse og bedÃ¸mme blandt andet renlighed, komfort, beliggenhed, faciliteter og service.

Administratorens del af systemet skal gÃ¸re det muligt at administrere vÃ¦relser, priser, faciliteter, bookinger, betalinger og anmeldelser.

Applikationen udvikles i Java med Spring Boot og anvender PostgreSQL som relationel database.

---

## 2. Problemformulering

Mindre villaer kan hÃ¥ndtere reservationer manuelt via telefon, SMS eller e-mail. Det kan gÃ¸re det vanskeligt at bevare et samlet overblik over ledige vÃ¦relser, bookinger, betalinger og aflysninger. Det kan samtidig Ã¸ge risikoen for fejl og dobbeltbookinger.

Projektet tager derfor udgangspunkt i fÃ¸lgende problemformulering:

> **Hvordan kan der udvikles en brugervenlig webapplikation, som gÃ¸r det muligt for gÃ¦ster at finde, booke, betale og administrere et ophold i en mindre villa, samtidig med at administratoren fÃ¥r et samlet overblik over vÃ¦relser, bookinger, betalinger og tilgÃ¦ngelighed?**

Systemet skal sikre, at det samme vÃ¦relse ikke kan bookes af flere gÃ¦ster i overlappende perioder.

---

## 3. Brugerhistorier (User Stories)

Brugerhistorierne beskriver de vigtigste funktioner i Villa Room Booking System set fra brugerens perspektiv.

### 3.1 Se ledige vÃ¦relser â€“ US1

**Som kunde vil jeg kunne se ledige vÃ¦relser, sÃ¥ jeg kan finde et vÃ¦relse, der passer til mit ophold.**

**Acceptance Criteria:**

- Systemet viser de 8 vÃ¦relser opdelt efter dato.
- Ledige vÃ¦relser er tydeligt markeret.
- Bookede vÃ¦relser fremgÃ¥r som optaget.
- Kunden kan vÃ¦lge check-in- og check-out-dato.
- Systemet viser kun vÃ¦relser, der er ledige i den valgte periode.
- Systemet viser, hvor mange vÃ¦relser der er ledige.

**Tasks:**

- Implementere visning af ledige og optagede vÃ¦relser med filtrering efter check-in- og check-out-dato.
- Implementere kontrol af eksisterende bookinger i databasen.

---

### 3.2 Se information om vÃ¦relse â€“ US2

**Som kunde vil jeg kunne se information om et vÃ¦relse, sÃ¥ jeg kan vÃ¦lge det vÃ¦relse, der passer bedst til mine behov.**

**Acceptance Criteria:**

- VÃ¦relsets nummer eller navn.
- Billeder af vÃ¦relset.
- StÃ¸rrelse i mÂ².
- Pris pr. nat.
- Maksimalt antal gÃ¦ster.
- Faciliteter sÃ¥som Wi-Fi, TV, aircondition, eget badevÃ¦relse og balkon.
- VÃ¦relsets gennemsnitlige rating.

**Tasks:**

- Implementere en detaljeside for hvert vÃ¦relse med billeder, pris, stÃ¸rrelse, faciliteter og rating.

---

### 3.3 Booke vÃ¦relse â€“ US3

**Som kunde vil jeg kunne booke et ledigt vÃ¦relse, sÃ¥ jeg kan reservere det til mit ophold.**

**Acceptance Criteria:**

- Kunden kan vÃ¦lge et ledigt vÃ¦relse.
- Kunden kan angive check-in og check-out.
- Kunden kan angive antal gÃ¦ster.
- Bookingen kan kun gennemfÃ¸res, hvis vÃ¦relset er ledigt.
- Det samme vÃ¦relse kan ikke dobbeltbookes i samme periode.
- Systemet beregner automatisk antal nÃ¦tter.
- Systemet beregner den samlede pris.

**Tasks:**

- Udvikle bookingfunktionalitet med validering af datoer og ledighed.
- Implementere kontrol mod dobbeltbooking.
- Implementere automatisk beregning af antal nÃ¦tter og samlet pris.

---

### 3.4 Indtaste kundeoplysninger â€“ US4

**Som kunde vil jeg kunne indtaste mine personlige oplysninger, sÃ¥ bookingen kan registreres i mit navn.**

**Acceptance Criteria:**

- Fornavn.
- Efternavn.
- E-mail.
- Telefonnummer.
- Antal gÃ¦ster.
- Systemet validerer de nÃ¸dvendige oplysninger.

**Tasks:**

- Oprette bookingformular.
- Implementere validering af kundeoplysninger.
- Gemme kundeoplysninger sammen med bookingen.

---

### 3.5 Betale booking â€“ US5

**Som kunde vil jeg kunne betale for mit ophold online, sÃ¥ min booking kan bekrÃ¦ftes.**

**Acceptance Criteria:**

- Kunden kan se den samlede pris fÃ¸r betaling.
- Kunden kan gennemfÃ¸re betalingen.
- Betalingens status registreres.
- Status kan vÃ¦re `PENDING`, `PAID`, `FAILED` eller `REFUNDED`.
- Bookingen bekrÃ¦ftes efter en godkendt betaling.

**Tasks:**

- Implementere betalingsfunktionalitet.
- Gemme betalingsoplysninger og betalingsstatus.
- Knytte betalingen til den korrekte booking.

---

### 3.6 Modtage bookingbekrÃ¦ftelse â€“ US6

**Som kunde vil jeg modtage en bookingbekrÃ¦ftelse via e-mail eller SMS, sÃ¥ jeg har dokumentation for min reservation.**

**Acceptance Criteria:**

BekrÃ¦ftelsen indeholder:

- Et unikt bookingnummer.
- Kundens navn.
- VÃ¦relsesnummer.
- Check-in dato og tidspunkt.
- Check-out dato og tidspunkt.
- Antal nÃ¦tter.
- Samlet pris.
- Betalingsstatus.
- Villaens adresse.

**Tasks:**

- Generere et unikt bookingnummer.
- Implementere bookingbekrÃ¦ftelse.
- Implementere afsendelse via e-mail og/eller SMS.

---

### 3.7 Annullere booking â€“ US7

**Som kunde vil jeg kunne annullere min booking, sÃ¥ jeg kan afbestille mit ophold, hvis mine planer Ã¦ndrer sig.**

**Acceptance Criteria:**

- Kunden kan vÃ¦lge at annullere via sin bookingbekrÃ¦ftelse.
- Bookingen kan annulleres indtil 2 timer fÃ¸r check-in.
- Systemet afviser annulleringen, hvis der er mindre end 2 timer til check-in.
- Bookingens status Ã¦ndres til `CANCELLED`.
- VÃ¦relset bliver igen tilgÃ¦ngeligt for andre kunder.

**Tasks:**

- Implementere annulleringsfunktion.
- Implementere 2-timers-reglen.
- Opdatere bookingstatus og vÃ¦relsets tilgÃ¦ngelighed.

---

### 3.8 Se min booking â€“ US8

**Som kunde vil jeg kunne se min booking, sÃ¥ jeg kan kontrollere oplysningerne om mit ophold.**

**Acceptance Criteria:**

Kunden kan se:

- Bookingnummer.
- VÃ¦relse.
- Check-in og check-out.
- Antal nÃ¦tter.
- Samlet pris.
- Bookingstatus.
- Betalingsstatus.

**Tasks:**

- Udvikle en side til visning af kundens booking og bookingdetaljer.

---

### 3.9 Skrive anmeldelse â€“ US9

**Som kunde vil jeg kunne skrive en anmeldelse efter mit ophold, sÃ¥ jeg kan dele min oplevelse med andre gÃ¦ster.**

**Acceptance Criteria:**

- Kun kunder med et afsluttet ophold kan skrive en anmeldelse.
- Kunden kan give 1â€“5 stjerner.
- Kunden kan bedÃ¸mme renlighed.
- Kunden kan bedÃ¸mme komfort.
- Kunden kan bedÃ¸mme beliggenhed.
- Kunden kan bedÃ¸mme faciliteter.
- Kunden kan bedÃ¸mme value for money.
- Kunden kan skrive en kommentar.
- Systemet beregner den gennemsnitlige rating.

**Tasks:**

- Implementere reviewformular.
- Kontrollere, at kunden har gennemfÃ¸rt opholdet.
- Gemme ratings og kommentar.
- Beregne og vise gennemsnitlig rating.

---

### 3.10 Administrere vÃ¦relser â€“ US10

**Som admin vil jeg kunne administrere villaens vÃ¦relser, sÃ¥ informationen pÃ¥ hjemmesiden altid er opdateret.**

**Acceptance Criteria:**

Admin kan:

- Se alle 8 vÃ¦relser.
- Oprette og redigere et vÃ¦relse.
- Ã†ndre pris pr. nat.
- Ã†ndre stÃ¸rrelse og kapacitet.
- TilfÃ¸je eller Ã¦ndre billeder.
- Ã†ndre faciliteter sÃ¥som Wi-Fi, TV og aircondition.

**Tasks:**

- Udvikle CRUD-funktionalitet til administration af vÃ¦relser.

---

### 3.11 Administrere bookinger â€“ US11

**Som admin vil jeg kunne se og administrere bookinger, sÃ¥ jeg har overblik over villaens reservationer.**

**Acceptance Criteria:**

Admin kan:

- Se alle bookinger.
- Se ledige og optagede vÃ¦relser.
- SÃ¸ge efter en booking.
- Se bookinger efter dato.
- Se kommende check-ins og check-outs.
- Se bookingstatus.
- Annullere en booking.

**Tasks:**

- Udvikle administrationsside til bookinger med sÃ¸gning, filtrering og Ã¦ndring af status.

---

### 3.12 Se Admin Dashboard â€“ US12

**Som admin vil jeg kunne se et dashboard, sÃ¥ jeg hurtigt kan fÃ¥ overblik over villaens aktuelle situation.**

**Acceptance Criteria:**

Dashboardet viser:

- Antal vÃ¦relser: 8.
- Antal ledige vÃ¦relser.
- Antal optagede vÃ¦relser.
- Dagens ankomster.
- Dagens afgange.
- Kommende bookinger.
- Betalinger og omsÃ¦tning.

**Tasks:**

- Udvikle admin dashboard og hente de nÃ¸dvendige data fra databasen.


---

## 4. Funktionelle krav

De funktionelle krav beskriver, hvilke funktioner Villa Room Booking System skal kunne udfÃ¸re.

**Systemet skal kunne:**

- Vise information om villaen og dens kontaktoplysninger.
- Vise villaens vÃ¦relser.
- Give gÃ¦sten mulighed for at sÃ¸ge efter ledige vÃ¦relser ud fra check-in- og check-out-dato.
- Vise vÃ¦relsets nummer, billeder, stÃ¸rrelse, kapacitet, pris og faciliteter.
- Vise hvor mange vÃ¦relser der er ledige i den valgte periode.
- Forhindre dobbeltbookinger.
- Beregne antal overnatninger og den samlede pris automatisk.
- Registrere gÃ¦stens oplysninger.
- Oprette og gemme bookinger.
- Registrere betaling og betalingsstatus.
- Generere et unikt bookingnummer.
- Sende bookingbekrÃ¦ftelse via e-mail eller SMS.
- Give gÃ¦sten mulighed for at annullere bookingen indtil 2 timer fÃ¸r check-in.
- Give gÃ¦sten mulighed for at skrive en anmeldelse og give 1â€“5 stjerner efter afsluttet ophold.
- Give administratoren mulighed for at administrere vÃ¦relser, priser, faciliteter, bookinger, betalinger og anmeldelser.
- Gemme relevante oplysninger i databasen.

---

## 5. Ikke-funktionelle krav

Ud over de funktionelle krav stilles der ogsÃ¥ krav til systemets kvalitet, sikkerhed og brugervenlighed.

### Brugervenlighed

BrugergrÃ¦nsefladen skal vÃ¦re enkel, overskuelig og nem at forstÃ¥ for bÃ¥de gÃ¦ster og administrator.

### Responsivt design

Webapplikationen skal kunne anvendes pÃ¥ computer, tablet og mobiltelefon.

### Sikkerhed

Adgangskoder og kundeoplysninger skal hÃ¥ndteres sikkert.

Administratorfunktioner mÃ¥ kun vÃ¦re tilgÃ¦ngelige for administratoren.

### PÃ¥lidelighed

Systemet skal forhindre dobbeltbookinger og sikre, at oplysninger om vÃ¦relser, bookinger og betalinger er korrekte.

### Vedligeholdelse

Applikationen skal anvende en tydelig lagdelt arkitektur med Controller, Service og Repository, sÃ¥ koden er struktureret og nemmere at vedligeholde.

### Ydeevne

SÃ¸gning efter ledige vÃ¦relser og gennemfÃ¸relse af bookinger skal ske inden for rimelig tid.

### Validering

Brugerens input, sÃ¥som navn, e-mail, telefonnummer, datoer og antal gÃ¦ster, skal valideres, fÃ¸r oplysningerne gemmes.

---



## 6. DomÃ¦nemodel

DomÃ¦nemodellen beskriver de vigtigste begreber i Villa Room Booking System og relationerne mellem dem.

De centrale domÃ¦neklasser er:

- User
- Role
- Room
- Booking
- Payment
- Review
- Amenity
- RoomImage
- RoomAmenity

En kunde kan have flere bookinger, mens hver booking tilhÃ¸rer Ã©n kunde. Et vÃ¦relse kan have flere bookinger pÃ¥ forskellige tidspunkter, men systemet skal sikre, at bookingerne ikke overlapper hinanden.

Et vÃ¦relse kan have flere faciliteter, sÃ¥som Wi-Fi, TV og aircondition, og den samme facilitet kan vÃ¦re tilknyttet flere vÃ¦relser. Derfor anvendes `RoomAmenity` som en join-klasse mellem `Room` og `Amenity`.

En booking er knyttet til et vÃ¦relse og en kunde og kan desuden vÃ¦re forbundet med en betaling og en anmeldelse.

### DomÃ¦nemodel

Herunder vises projektets domÃ¦nemodel:

![DomÃ¦nemodel](/images/domain-model.png)

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

`RoomAmenity` fungerer som en join-klasse mellem `Room` og `Amenity` og hÃ¥ndterer many-to-many-relationen mellem vÃ¦relser og faciliteter.

Java-klasserne mappes til tabeller i PostgreSQL-databasen ved hjÃ¦lp af JPA/Hibernate.

### Klassediagram 7a

![Klassediagram 7a](/images/class-diagram-1.png)

### Klassediagram 7b

![Klassediagram 7b](/images/class-diagram-2.png)


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

Hver tabel har en **Primary Key (PK)**, som identificerer hver rÃ¦kke entydigt.

**Foreign Keys (FK)** bruges til at skabe relationer mellem tabellerne. For eksempel er en booking knyttet til bÃ¥de en kunde og et vÃ¦relse.

Tabellen `room_amenities` fungerer som en join-tabel mellem `rooms` og `amenities`. Dette gÃ¸r det muligt at implementere en many-to-many-relation, hvor et vÃ¦relse kan have flere faciliteter, og den samme facilitet kan vÃ¦re tilknyttet flere vÃ¦relser.

### ER-diagram

Herunder vises projektets ER-diagram:

![ER-diagram](/images/er-diagram.png)

---

## 9. Sekvensdiagram

Sekvensdiagrammet viser, hvordan de forskellige dele af systemet kommunikerer med hinanden under en booking.

Diagrammet beskriver processen fra det tidspunkt, hvor kunden sÃ¸ger efter et ledigt vÃ¦relse, til bookingen bliver oprettet og bekrÃ¦ftet.

Bookingprocessen foregÃ¥r overordnet sÃ¥ledes:

1. Kunden vÃ¦lger check-in- og check-out-dato.
2. Systemet sÃ¸ger efter ledige vÃ¦relser.
3. Kunden vÃ¦lger et vÃ¦relse.
4. Kunden indtaster sine personlige oplysninger.
5. Systemet kontrollerer, at vÃ¦relset stadig er ledigt.
6. Bookingen oprettes.
7. Betalingen registreres.
8. Kunden modtager en bookingbekrÃ¦ftelse.

Sekvensdiagrammet viser kommunikationen mellem blandt andet brugergrÃ¦nsefladen, Controller, Service, Repository og databasen.

### Sekvensdiagram

Herunder vises projektets sekvensdiagram:

![Sekvensdiagram](/images/sequence-diagram.png)

---

## 10. Systemarkitektur

Villa Room Booking System opbygges med en lagdelt arkitektur. FormÃ¥let er at adskille de forskellige ansvarsomrÃ¥der i applikationen, sÃ¥ systemet bliver mere overskueligt og lettere at vedligeholde.

Systemet bestÃ¥r af fÃ¸lgende lag:

### Controller

Controller-laget modtager HTTP-requests fra brugeren og sender dem videre til Service-laget.

### Service

Service-laget indeholder systemets forretningslogik. Her hÃ¥ndteres blandt andet bookingregler, kontrol af ledige vÃ¦relser, prisberegning og validering.

### Repository

Repository-laget stÃ¥r for kommunikationen med databasen og bruges til at hente, gemme, opdatere og slette data.

### Database

PostgreSQL anvendes som relationel database til at gemme blandt andet brugere, vÃ¦relser, bookinger, betalinger og anmeldelser.

Systemets overordnede struktur er:

**Browser â†’ Controller â†’ Service â†’ Repository â†’ PostgreSQL**

### Systemarkitektur

Herunder vises systemets arkitekturdiagram:

![Systemarkitektur](/images/system-architecture.png)

---

## 11. Teknologier

Villa Room Booking System udvikles med en rÃ¦kke teknologier til backend, database og versionsstyring.

### Java

Java anvendes som det primÃ¦re programmeringssprog til udvikling af applikationens backend og forretningslogik.

### Spring Boot

Spring Boot anvendes til at opbygge webapplikationen og strukturere systemet i Controller-, Service- og Repository-lag.

### JPA / Hibernate

JPA og Hibernate anvendes til Object-Relational Mapping (ORM), sÃ¥ Java-objekter kan gemmes og hentes fra databasen.

### PostgreSQL

PostgreSQL anvendes som relationel database til blandt andet brugere, vÃ¦relser, bookinger, betalinger og anmeldelser.

### Maven

Maven anvendes til dependency management og til at administrere projektets biblioteker og dependencies.

### Git og GitHub

Git anvendes til versionsstyring af projektet, mens GitHub bruges til at gemme projektets repository online og fÃ¸lge Ã¦ndringer i kildekoden.

### Docker

Docker kan anvendes til at kÃ¸re PostgreSQL-databasen i et isoleret og ensartet udviklingsmiljÃ¸.

### IntelliJ IDEA

IntelliJ IDEA anvendes som udviklingsmiljÃ¸ til programmering, test og arbejde med projektets kode.

### Technology Stack

Herunder vises en samlet oversigt over de teknologier og vÃ¦rktÃ¸jer, der anvendes i projektet:

![Villa Room Booking Technology Stack](/images/technology-stack.png)

---

## 12. Test

Test er en vigtig del af udviklingen af Villa Room Booking System. FormÃ¥let er at kontrollere, at systemets funktioner virker korrekt, og at fejl opdages sÃ¥ tidligt som muligt.

I projektet anvendes bÃ¥de **Unit Tests** og **Integration Tests**.

### Unit Tests

Unit tests anvendes til at teste enkelte dele af applikationen isoleret.

JUnit 5 anvendes til at skrive og kÃ¸re testene, mens Mockito kan anvendes til at mocke dependencies, sÃ¥ forretningslogikken kan testes uden at vÃ¦re afhÃ¦ngig af den rigtige database.

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
- Kontrol af ledige vÃ¦relser.
- Relationer mellem systemets entities.

Integration tests er vigtige, fordi de kontrollerer samspillet mellem applikationen og databasen og sikrer, at de forskellige dele af systemet fungerer korrekt sammen.

### Test af booking

Et af de vigtigste testomrÃ¥der er bookingprocessen.

Systemet skal kontrollere, om der allerede eksisterer en booking for det valgte vÃ¦relse i den Ã¸nskede periode.

Hvis perioderne overlapper hinanden, skal den nye booking afvises. Dette sikrer, at det samme vÃ¦relse ikke kan bookes af flere gÃ¦ster pÃ¥ samme tidspunkt.


---

## 13. Konklusion

Villa Room Booking System har til formÃ¥l at udvikle en brugervenlig og struktureret webapplikation til online booking af vÃ¦relser i en mindre villa.

Systemet giver gÃ¦ster mulighed for at sÃ¸ge efter ledige vÃ¦relser, se information om vÃ¦relserne, oprette en booking, betale for opholdet og modtage en bookingbekrÃ¦ftelse. Derudover kan gÃ¦ster administrere deres booking og skrive en anmeldelse efter afsluttet ophold.

For administratoren giver systemet mulighed for at administrere vÃ¦relser, bookinger, priser, faciliteter, betalinger og anmeldelser.

Projektet anvender en lagdelt arkitektur med Controller, Service og Repository samt PostgreSQL som relationel database. JPA/Hibernate anvendes til kommunikationen mellem Java-applikationen og databasen.

Unit tests og integration tests anvendes til at kontrollere systemets funktionalitet og samspillet mellem de forskellige dele af applikationen.

Projektet giver dermed praktisk erfaring med udvikling af en komplet webapplikation, herunder systemdesign, databasedesign, backend-udvikling, test og versionsstyring.




[← Back](/projects/project1/)
