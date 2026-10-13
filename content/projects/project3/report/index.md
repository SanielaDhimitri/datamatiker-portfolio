+++
title = "Project Report"
date = 2026-10-13
draft = false
+++
Maler & Håndværk
REST API til håndværksydelser og arbejdsforespørgsler
3. semesterprojekt – Datamatiker
- Uddannelse: Datamatiker
- Uddannelsessted: Erhvervsakademi København (EK), Lyngby
- Teknologier: Java · Javalin · JPA/Hibernate · PostgreSQL · JWT · Gemini AI
- Studieår: 2026–2027

  Indhold
1. Indledning
2. Problemformulering
6. Domænemodel
7. Klassediagram
8. ER-diagram
9. Sekvensdiagram
10. Systemarkitektur
11. Teknologier
12. Test
13. Konklusion

1. Indledning
   Maler & Håndværk er et backendprojekt til en håndværksvirksomhed med malerarbejde som primær ydelse. Systemet skal gøre det lettere at modtage og behandle arbejdsforespørgsler, administrere tilbud og håndtere forskellige services.
   Besøgende skal kunne sende arbejdsforespørgsler uden login. Registrerede brugere kan logge ind med JWT, og rollerne ADMIN og MEDLEM bestemmer adgangen til beskyttede funktioner. Systemet indeholder desuden integration med AI-chat via Gemini.
   Projektet udvikles som et REST API i Java og Javalin. JPA/Hibernate bruges til databaseadgang, og data gemmes i PostgreSQL. Frontend, bookingkalender, kundeportal og betaling er ikke dokumenteret som færdige dele af denne backendversion.
2. Problemformulering
   Håndværksvirksomheder kan modtage henvendelser via telefon, e-mail og sociale medier. Det kan gøre det svært at samle kundeoplysninger, følge arbejdsforespørgsler og udarbejde tilbud.
   Hvordan kan et REST API udvikles, så kunder nemt kan sende arbejdsforespørgsler, mens virksomheden sikkert kan administrere forespørgsler, tilbud og services ved hjælp af rollebaseret adgang og AI-integration?
   Projektet fokuserer på en overskuelig backendarkitektur, sikker adgang, datalagring og automatiserede tests.
3. User Stories
   User Stories beskriver funktioner i den aktuelle backend og planlagte udvidelser.
   US1 – Opret arbejdsforespørgsel
   User Story: Som besøgende vil jeg kunne oprette en arbejdsforespørgsel uden login.
   Acceptance Criteria:
- Kunden kan sende en forespørgsel uden login.
- Forespørgslen gemmes i databasen.
  Tasks:
- [x] WorkRequest CRUD
- [x] POST endpoint
- [x] API-test
  US2 – Se services
  User Story: Som besøgende vil jeg kunne se virksomhedens services.
  Acceptance Criteria:
- Services kan ses uden login.
- Services hentes fra databasen.
  Tasks:
- [x] Service entity
- [ ] GET endpoint
- [ ] API-test
  US3 – Login med JWT
  User Story: Som bruger vil jeg kunne logge ind og få adgang til systemet.
  Acceptance Criteria:
- Korrekt login giver et JWT-token.
- Forkert login afvises.
  Tasks:
- [x] Login
- [x] JWT
- [x] BCrypt
- [ ] Login-test
  US4 – Roller og sikkerhed
  User Story: Som administrator vil jeg beskytte API-endpoints med roller.
  Acceptance Criteria:
- ADMIN og MEDLEM har forskellige rettigheder.
- Uautoriserede requests afvises.
  Tasks:
- [x] Roller
- [x] JWT-verifikation
- [x] Beskyttede endpoints
- [ ] Sikkerhedstest
  US5 – Se arbejdsforespørgsler
  User Story: Som ADMIN eller MEDLEM vil jeg kunne se arbejdsforespørgsler.
  Acceptance Criteria:
- Brugeren kan hente alle forespørgsler.
- Brugeren kan hente en forespørgsel via ID.
  Tasks:
- [x] GET endpoints
- [x] DAO og Service
- [x] API-tests
  US6 – Opret tilbud
  User Story: Som ADMIN vil jeg kunne oprette tilbud til kunder.
  Acceptance Criteria:
- Tilbuddet knyttes til en WorkRequest.
- Tilbuddet gemmes i databasen.
  Tasks:
- [x] Offer CRUD
- [x] ADMIN-adgang
- [x] API-tests
  US7 – Accepter eller afvis tilbud
  User Story: Som kunde vil jeg kunne acceptere eller afvise et tilbud.
  Acceptance Criteria:
- Kunden kan acceptere eller afvise tilbuddet.
- Tilbuddets status opdateres.
  Tasks:
- [ ] Accept endpoint
- [ ] Afvis endpoint
- [ ] API-test
  US8 – Administrer services
  User Story: Som ADMIN vil jeg kunne administrere virksomhedens services.
  Acceptance Criteria:
- ADMIN kan oprette, ændre og slette services.
- Ændringer gemmes i databasen.
  Tasks:
- [ ] Service CRUD
- [ ] ADMIN-adgang
- [ ] API-test
  US9 – AI-chat
  User Story: Som kunde vil jeg kunne stille spørgsmål til en AI-chat.
  Acceptance Criteria:
- Kunden kan sende en besked.
- AI returnerer et svar.
  Tasks:
- [x] Gemini API
- [x] ChatService
- [ ] API-test
  US10 – AI-analyse
  User Story: Som ADMIN vil jeg kunne analysere arbejdsforespørgsler med AI.
  Acceptance Criteria:
- ADMIN kan anmode om en analyse.
- AI returnerer et forslag eller en analyse.
  Tasks:
- [ ] AI-analyse
- [ ] ADMIN-adgang
- [ ] API-test
  US11 – Annuller arbejdsforespørgsler og tilbud
  User Story: Som ADMIN vil jeg kunne annullere arbejdsforespørgsler og tilbud.
  Acceptance Criteria:
- Status ændres til ANNULLERET.
- Kun ADMIN kan annullere.
  Tasks:
- [x] PATCH endpoints
- [x] Statusopdatering
- [x] API-tests
  Status: [x] = tidligere implementeret eller gennemgået; [ ] = mangler eller skal verificeres. Status bør kontrolleres mod den aktuelle kode og testresultater.
4. Funktionelle krav
   REST API'et skal kunne:
- Modtage en arbejdsforespørgsel uden login.
- Gemme og hente arbejdsforespørgsler fra databasen.
- Understøtte opdatering og annullering af arbejdsforespørgsler.
- Understøtte tilbud, som er knyttet til arbejdsforespørgsler.
- Give brugere mulighed for login med JWT.
- Beskytte endpoints ud fra rollerne ADMIN og MEDLEM.
- Håndtere services og deres relation til arbejdsforespørgsler.
- Modtage beskeder til AI-chat via Gemini.
- Returnere JSON og passende HTTP-statuskoder.
  Planlagte eller ikke fuldt verificerede funktioner: kundens accept/afvisning af tilbud, komplet Service CRUD, offentlig servicevisning og administrativ AI-analyse.
5. Ikke-funktionelle krav
   Sikkerhed
- Beskyttede endpoints kræver gyldigt JWT.
- Adgangskoder lagres som hashes med BCrypt.
- Roller kontrolleres på administrative funktioner.
- Hemmelige API-nøgler må ikke indgå direkte i kildekoden.
  Pålidelighed og validering
- Ugyldige input skal give forståelige fejl.
- Data skal gemmes korrekt i PostgreSQL.
- Ukendte ressourcer skal give en passende fejl, fx HTTP 404.
  Vedligeholdelse
- Koden opdeles i Routes, Controllers, Services, DAO, DTO, Mappers og Entities.
- Tests skal kunne køres automatisk.
  API-design
- API'et anvender HTTP-metoder som GET, POST, PUT, PATCH og DELETE efter behov.
- Request og response sendes primært som JSON.
6. Domænemodel
   Domænemodellen beskriver de centrale begreber i backendprojektet:
- User: En registreret bruger med login og roller.
- Role: Bestemmer rettigheder, fx ADMIN og MEDLEM.
- WorkRequest: En kundes forespørgsel om en arbejdsopgave.
- Service: En type håndværksydelse.
- Offer: Et tilbud knyttet til en arbejdsforespørgsel.
  En WorkRequest kan oprettes uden en registreret bruger. En WorkRequest kan være knyttet til flere services og flere tilbud. Den præcise domænemodel skal svare til de aktuelle Java-entities.
  Domænemodel

Bemærk: Billedet skal kontrolleres og eventuelt opdateres, hvis det viser den tidligere booking- og projektmodel.
7. Klassediagram
   Klassediagrammet skal vise projektets faktiske Java-klasser og deres relationer. De vigtigste områder er:
- Entities som User, Role, WorkRequest, Service og Offer.
- DTO'er til input og output.
- Controllers til HTTP-requests.
- Services til forretningslogik.
- DAO-klasser til databaseoperationer.
- Mappers til konvertering mellem DTO og entity.
  Klassediagram

Diagrammet skal opdateres, hvis det stadig viser planlagte klasser som Review, Customer eller PaymentStatus.
8. ER-diagram
   ER-diagrammet beskriver relationerne mellem databasens tabeller. Centrale tabeller i den gennemgåede backend omfatter:
- app_user
- app_role / rolle-relaterede tabeller (navne kontrolleres mod entity-mapping)
- user_role
- work_request
- service
- work_request_service
- offer
  Tabellerne forbindes med primærnøgler (PK) og fremmednøgler (FK). work_request_service understøtter en many-to-many-relation. Et tilbud hører til en arbejdsforespørgsel.
  ER-diagram

Kontrollér diagrammets tabelnavne, kolonner og kardinaliteter mod PostgreSQL, før det anvendes som dokumentation for den aktuelle database.
9. Sekvensdiagram
   Et centralt flow er oprettelse af en arbejdsforespørgsel uden login:
1. Kunden sender en POST-request med oplysninger om opgaven.
2. Routes sender requesten til WorkRequestController.
3. Controlleren læser og validerer input via DTO.
4. WorkRequestService behandler forespørgslen.
5. WorkRequestDAO gemmer data gennem Hibernate.
6. PostgreSQL gemmer arbejdsforespørgslen.
7. API'et returnerer et JSON-svar og en passende HTTP-status.
   Sekvensdiagram

Hvis billedet viser bookingkalender i stedet for WorkRequest-flowet, skal det udskiftes.
10. Systemarkitektur
    Systemet anvender en lagdelt backendarkitektur:
    HTTP-klient → Routes → Controller → Service → DAO → JPA/Hibernate → PostgreSQL
- Main: Starter applikationen og samler nødvendige komponenter.
- API / Routes: Definerer REST-endpoints og deres adgangsregler.
- Controller: Modtager HTTP-requests og returnerer responses.
- Service: Indeholder forretningslogik.
- DAO: Håndterer databaseoperationer.
- DTO og Mappers: Overfører og konverterer data.
- Entities: Repræsenterer data, som gemmes via Hibernate.
- Config: Konfigurerer Javalin og Hibernate.
- Security: Håndterer JWT og roller.
- Exception: Håndterer fejl.
- Test: Tester applikationens funktioner.
  Gemini AI er en ekstern service, som backend kan kommunikere med.
  Systemarkitektur

11. Teknologier
    Teknologi	Formål
    Java	Programmeringssprog til backend
    Javalin	REST API og HTTP-routing
    Maven	Dependencies og build
    JPA / Hibernate	ORM og databaseadgang
    PostgreSQL	Relationel database
    Docker	Lokalt udviklings- og testmiljø
    Jackson	JSON-konvertering
    JWT	Tokenbaseret autentifikation
    BCrypt	Hashing af adgangskoder
    Gemini API	AI-chat og mulig AI-analyse
    JUnit	Automatiserede tests
    Mockito	Mocking i unit tests
    REST Assured	Test af REST-endpoints
    Hamcrest	Assertions i API-tests
    Git og GitHub	Versionsstyring
    GitHub Actions	Automatisk build/CI
    IntelliJ IDEA	Udviklingsmiljø


Technology Stack

12. Test
    Tests bruges til at kontrollere API'ets funktionalitet, sikkerhed og samspil med databasen.
    Unit Tests
    JUnit og Mockito kan anvendes til at teste forretningslogik isoleret fra databasen. Relevante testområder er:
- Oprettelse og validering af WorkRequest.
- Statusændringer og annullering.
- Oprettelse og behandling af Offer.
- Fejlhåndtering i Service-laget.
  Integration Tests og API-tests
  REST Assured og Hamcrest anvendes til at teste HTTP-responses og API-endpoints. Relevante scenarier er:
- POST WorkRequest uden login.
- GET WorkRequest-liste og WorkRequest via ID.
- HTTP 404 ved ukendt ID.
- Oprettelse af Offer med ADMIN-adgang.
- JWT-login og beskyttede endpoints.
- PATCH-annullering af WorkRequest og Offer.
- Korrekte HTTP-statuskoder og JSON-svar.
  Manglende eller ikke verificerede tests
- Kundens accept og afvisning af tilbud.
- Fuld Service CRUD.
- AI-chat ved fejl fra Gemini.
- Administrativ AI-analyse.
  Teststatus: Det samlede antal beståede tests bør hentes fra den seneste Maven-kørsel og ikke angives uden aktuel kontrol.
13. Konklusion
    Maler & Håndværk er et REST API, der samler virksomhedens arbejdsforespørgsler, tilbud og services i en backend. Besøgende kan sende arbejdsforespørgsler uden login, mens JWT og roller bruges til at beskytte administrative funktioner.
    Systemet er bygget med Java, Javalin, Hibernate og PostgreSQL og anvender en lagdelt arkitektur med Controllers, Services og DAO. AI-chat via Gemini udvider mulighederne for at hjælpe kunder med spørgsmål.
    Projektet giver praktisk erfaring med REST API-design, databaseforbindelser, sikkerhed, rollebaseret adgang, integrationer og automatiserede tests. Funktioner som kundens accept/afvisning af tilbud, komplet serviceadministration og administrativ AI-analyse er fortsat planlagte eller kræver verifikation.
    [← Back](/projects/project3/)