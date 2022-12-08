# Dot Framework Security

## Inhoudsopgave

- [Dot Framework Security](#dot-framework-security)
  - [Inhoudsopgave](#inhoudsopgave)
  - [1. Inleiding](#1-inleiding)
  - [2. Wat is OWASP?](#2-wat-is-owasp)
    - [A01:2021 - Broken Access Control](#a012021---broken-access-control)
    - [A02:2021 - Cryptographic Failures](#a022021---cryptographic-failures)
    - [A03:2021 - Injection](#a032021---injection)
    - [A04:2021 - Insecure Design](#a042021---insecure-design)
    - [A05:2021 - Security Misconfiguration](#a052021---security-misconfiguration)
    - [A06:2021 - Vulnerable and Outdated Components](#a062021---vulnerable-and-outdated-components)
    - [A07:2021 - Indentification and Authenticated Vulnerabilities](#a072021---indentification-and-authenticated-vulnerabilities)
    - [A08:2021 - Software and Data Integrity failures](#a082021---software-and-data-integrity-failures)
    - [A09:2021 - Security Logging and Monitoring failures](#a092021---security-logging-and-monitoring-failures)
    - [A10:2021 - Surver Side Request Forgery (SSRF)](#a102021---surver-side-request-forgery-ssrf)
  - [3. Hoofdvraag](#3-hoofdvraag)
  - [4. Deelvragen](#4-deelvragen)
  - [5. Wat is Injection?](#5-wat-is-injection)
  - [6. Vormen van Injection](#6-vormen-van-injection)
    - [6.1 SQL-injectie:](#61-sql-injectie)
    - [6.2 Cross-site scripting (XSS):](#62-cross-site-scripting-xss)
    - [6.3 OS command injection](#63-os-command-injection)
  - [7. Hoe kan je Injection tegen gaan?](#7-hoe-kan-je-injection-tegen-gaan)
  - [8. Kan mijn applicatie kwetsbaar zijn voor Injection?](#8-kan-mijn-applicatie-kwetsbaar-zijn-voor-injection)
    - [8.1 Static code analysis](#81-static-code-analysis)
    - [8.2 ORM](#82-orm)
  - [9. Conclusie](#9-conclusie)
  - [10. Bronnen](#10-bronnen)

## 1. Inleiding

Wanneer je een applicatie ontwikkeld en publiceerd is veiligheid een van de belangrijkste dingen om rekening mee te houden. Je wil niet dat je applicatie gehackt wordt en dat er gegevens gestolen worden. Om dit te voorkomen is het belangrijk om te weten wat de risico's zijn en hoe je deze risico's kan voorkomen.

In dit onderzoek ga ik onderzoeken wat OWASP is en wat de verschillende beveiligingsrisico's zijn. Daarna kies ik er een uit en hierbij ga ik vragen opstellen. Dit doe ik allemaal door middel van het DOT framework.

## 2. Wat is OWASP?

OWASP staat voor Open Web Application Security Project. Het is een non-profit organisatie die zich richt op het verbeteren van de veiligheid van web applicaties. OWASP is een wereldwijde gemeenschap van beveiligingsexperts en ontwikkelaars die de veiligheid van webapplicaties willen verbeteren. OWASP richt zich op het ontwikkelen van open source tools en documentatie om de veiligheid van webapplicaties te verbeteren.

[OWASP heeft 10 belangrijke beveiligingsrisico's opgesteld.](https://owasp.org/www-project-top-ten/) Deze zijn:

- A01:2021 - Broken Access Control
- A02:2021 - Cryptographic Failures
- A03:2021 - Injection
- A04:2021 - Insecure Design
- A05:2021 - Security Misconfiguration
- A06:2021 - Vulnerable and Outdated Components
- A07:2021 - Indentification and Authenticated Vulnerabilities
- A08:2021 - Software and Data Integrity failures
- A09:2021 - Security Logging and Monitoring failures
- A10:2021 - Surver Side Request Forgery (SSRF)

#### A01:2021 - Broken Access Control

Met Broken Access Control wordt bedoeld dat er geen controle is op wie toegang heeft tot bepaalde informatie of functionaliteiten. Dit kan leiden tot een datalek, waarbij de gegevens van gebruikers in handen komen van kwaadwillenden.

Denk hierbij aan een website waar je als een user bij een bepaalde pagina kan komen, maar als je als admin bent, kan je ook bij die pagina komen. Dit is een voorbeeld van Broken Access Control. De user zou niet bij die pagina moeten kunnen komen alleen de admin.

#### A02:2021 - Cryptographic Failures

Cryptographic Failures zijn fouten die ontstaan door slechte encryptie. Het is natuurlijk belangrijk dat je wachtwoord, creditcard gegevens, etc. goed beveiligdzi jn. Op het moment dat deze niet goed geencrypt zijn, kunnen kwaadwillenden deze gegevens stelen. Op het moment dat het wel goed beveiligd is, kunnen ze deze gegevens niet stelen.

#### A03:2021 - Injection

Injection is een manier om een webapplicatie te hacken. Dit kan op verschillende manieren. Denk hierbij aan SQL injection, waarbij je een SQL query kan uitvoeren op de database van de webapplicatie.

Op het moment dat je data kan toevoegen of in de database kan kloten zonder dat dit gecontroleerd wordt, kan je een SQL injection uitvoeren. dit kan betekenen dat je bijvoorbeeld de hele database leeghaald.

#### A04:2021 - Insecure Design

Insecure Design is het ontwerp van een webapplicatie. Het is belangrijk dat je een webapplicatie goed ontwerpt. Niet de fouten die gemaakt worden tijdens het bouwen van de applicatie zijn belangrijk, maar de fouten die gemaakt worden tijdens het ontwerpen van de applicatie.

Op het moment dat je een webapplicatie ontwerpt, moet je goed nadenken over de beveiliging. Denk hierbij aan het gebruik van een database. Het is belangrijk dat je de database goed beveiligd. En dat bijvoorbeeld alleen je backend hier toegang tot heeft.

#### A05:2021 - Security Misconfiguration

Hierbij gaat het over het misconfigureren van een webapplicatie. Dit kan op verschillende manieren. Denk hierbij aan het niet updaten van een webapplicatie, het gebruiken van te oude software, het niet goed zetten van libary security settings, etc.

#### A06:2021 - Vulnerable and Outdated Components

Hierbij gaat het over het gebruik van verouderde software. Denk hierbij aan het gebruik van een verouderde versie van een library of een ouder bestuuringssysteem. Het is belangrijk dat je altijd up to date bent met de software die je gebruikt. Op het moment dat je verouderde software gebruikt, kan je een vulnerability hebben. Ook het is belangrijk om te weten welke componenten je gebruikt. En wat de componenten doen. Op het moment dat je een component gebruikt die je niet kent, kan je een vulnerability hebben.

#### A07:2021 - Indentification and Authenticated Vulnerabilities

Hierbij gaat het over het identificeren van een gebruiker. Denk hierbij aan het niet toestaan van een zwak of makkelijk wachtwoord. Het is belangrijk dat je nadenkt over wat je wel en niet toestaat.

#### A08:2021 - Software and Data Integrity failures

Dit heeft te maken met wat voor infrastructuren je gebruikt. Denk hierbij aan het gebruiken van een libary waarvan je niet weet waar die vandaan komt of hoe die werkt. Of een niet juiste CI/CD pipeline. Het is belangrijk dat je weet wat je gebruikt en hoe het werkt.

#### A09:2021 - Security Logging and Monitoring failures

Dit gaat over het loggen van een webapplicatie. Het is belangrijk dat je weet wat er gebeurt op je webapplicatie. Op het moment dat je niet weet wat er gebeurt, kan je niet weten of er een vulnerability is.

#### A10:2021 - Surver Side Request Forgery (SSRF)

Dit betekend dat je de gebruiker een link kan ingeven zonder dat deze gecontroleerd wordt. dit betekend dat er op de server een fout kan ontstaan. Denk hierbij aan het ophalen van een bestand van de server. Op het moment dat je een bestand van de server ophaalt, maar het is een kwaataardig bestand, kan je een vulnerability hebben.

## 3. Hoofdvraag

Ik heb gekozen om mijn onderzoek te gaan doen over A03:2021 - Injection. De reden waarom ik hiervoor heb gekozen is omdat dit voor mij een onderwerp wat zeker van toepassing is op mijn applicatie. Daarnaast heb ik veel gehoord over SQL injection en wil graag weten hoe dit werkt. Ook wil ik uitzoeken hoe dit werkt en het toepassen op mijn applicatie.

> **Wat is Injection en hoe kan je dit tegengaan?**

## 4. Deelvragen

- [Wat is Injection?](#5-wat-is-injection)
- [Wat zijn vormen van Injection?](#6-vormen-van-injection)
- [Hoe kan je Injection tegen gaan?](#7-hoe-kan-je-injection-tegen-gaan)
- [Kan mijn applicatie kwetsbaar zijn voor Injection?](#8-kan-mijn-applicatie-kwetsbaar-zijn-voor-injection)

## 5. Wat is Injection?

Injection is een beveiligingskwetsbaarheid die optreedt wanneer een aanvaller in staat is om kwaadaardige code in een programma of systeem te injecteren. Deze code kan dan worden uitgevoerd, waardoor de aanvaller volledige controle over het systeem kan krijgen en mogelijk ook toegang tot gevoelige gegevens.

Er bestaan verschillende soorten injectie-aanvallen, zoals SQL-injectie, cross-site scripting (XSS), command-injectie, OS-command-injectie en LDAP-injectie. Deze aanvallen exploiteren kwetsbaarheden in programma's of systemen, waardoor de aanvaller toegang kan krijgen tot gevoelige informatie of data kan manipuleren.

Om te beschermen tegen injectie-aanvallen is het belangrijk om goede beveiligingspraktijken te volgen bij het ontwikkelen van software. Dit betekent onder andere dat ingevoerde gebruikersgegevens goed moeten worden gesanitiseerd om te voorkomen dat er kwaadaardige code in zit, en dat er strikte toegangsbeveiliging moet worden toegepast om te voorkomen dat onbevoegde gebruikers toegang krijgen tot gevoelige gegevens. Het is ook belangrijk om regelmatig updates en patches voor software en systemen te installeren om te voorkomen dat ze kwetsbaar zijn voor bekende exploits.

Het komt er op neer dat je door middel van injection een kwaataardig stukje code op je server kan laten runnen waardoor de aanvaller hier bij komt.

## 6. Vormen van Injection

Injection kan op verschillende manieren worden uitgevoerd. Dit kan het ook zo gevaarlijk maken want de ene vorm kan je wel tegen gaan maar dan heb je helemaal niet aan de andere gedacht.

### 6.1 SQL-injectie:

SQL-injectie is een soort beveiligingslek dat optreedt in programma's of systemen die gebruik maken van een SQL-database. Het houdt in dat een aanvaller een speciaal geformatteerde SQL-query maakt die zijn kwaadaardige code bevat, en deze vervolgens via het kwetsbare programma of systeem naar de database stuurt. Wanneer de database de query verwerkt, wordt de code uitgevoerd, waardoor de aanvaller toegang krijgt tot de gegevens in de database of de gegevens kan manipuleren.

Er zijn verschillende manieren waarop een aanvaller een SQL-injectieaanval kan uitvoeren. Een veel voorkomende techniek is het invoeren van kwaadaardige code in een formulierveld dat is ontworpen om gebruikersinvoer te accepteren. Een aanmeldingsformulier kan bijvoorbeeld velden hebben voor de gebruikersnaam en het wachtwoord van de gebruiker. Een aanvaller kan zijn eigen SQL-code invoeren in het gebruikersnaamveld, en wanneer het programma of systeem de query verwerkt, wordt de code uitgevoerd, waardoor de aanvaller mogelijk toegang krijgt tot het systeem.

Een andere veelgebruikte techniek is het uitbuiten van kwetsbaarheden in de database zelf. Een aanvaller kan bijvoorbeeld een SQL-injectieaanval gebruiken om authenticatiecontroles te omzeilen en toegang te krijgen tot de database zonder geldige gebruikersnaam en geldig wachtwoord. Hierdoor kan de aanvaller gegevens in de database bekijken, wijzigen of verwijderen.

Ter bescherming tegen SQL-injectie aanvallen is het belangrijk om de best practices voor veilige codering te volgen. Dit omvat het goed zuiveren van gebruikersinvoer om ervoor te zorgen dat deze geen kwaadaardige code bevat, en het implementeren van strenge toegangscontroles om te voorkomen dat onbevoegde gebruikers toegang krijgen tot de database. Het is ook belangrijk de databasesoftware regelmatig bij te werken en te patchen om ervoor te zorgen dat deze niet kwetsbaar is voor bekende exploits.

Daarnaast is het belangrijk om de database regelmatig te controleren op tekenen van een aanval, zoals ongebruikelijke activiteit of gegevenswijzigingen. Dit kan helpen om een aanval snel te identificeren en erop te reageren, waardoor de potentiële schade tot een minimum wordt beperkt.

Voorbeeld van een sql injection

```sql
// Attacker-supplied input:
username: ' OR 1=1; --

// Original SQL query:
SELECT * FROM users WHERE username = '$username' AND password = '$password';

// Modified SQL query:
SELECT * FROM users WHERE username = '' OR 1=1; --' AND password = '$password';

```

Hier zie je door de aanvaller een sql injection uit te voeren dat hij de query heeft aangepast waardoor hij nu het beveiligingssysteem omzeild.

### 6.2 Cross-site scripting (XSS):

Cross-site scripting (XSS) is een type beveiligingslek waarmee aanvallers kwaadaardige code in websites of webapplicaties kunnen injecteren. Hierdoor kan de aanvaller willekeurige JavaScript uitvoeren in de context van de browser van het slachtoffer, waardoor gevoelige informatie zoals inloggegevens of persoonlijke gegevens kunnen worden gestolen.

XSS-aanvallen doen zich meestal voor wanneer een aanvaller een kwaadaardig script in een website of webtoepassing injecteert via gebruikersinvoer. Dit kan op verschillende manieren gebeuren, onder meer door het gebruik van plug-ins van derden of door misbruik te maken van zwakke plekken in de code van de website.

Er zijn twee hoofdtypen XSS-aanvallen: niet-persistente en persistente. Bij niet-persistente XSS-aanvallen wordt een kwaadaardig script in een website of webtoepassing geïnjecteerd via een enkel verzoek, bijvoorbeeld wanneer een gebruiker een commentaar op een blogbericht indient. Bij persistente XSS-aanvallen daarentegen wordt een kwaadaardig script in de database van de website of webtoepassing geïnjecteerd, waar het wordt uitgevoerd telkens wanneer de website wordt geladen.

XSS-aanvallen kunnen bijzonder gevaarlijk zijn omdat ze aanvallers in staat stellen willekeurige JavaScript uit te voeren in de context van de browser van het slachtoffer. Dit betekent dat de aanvaller gevoelige informatie kan stelen, zoals inloggegevens of persoonlijke gegevens, door JavaScript te gebruiken om toegang te krijgen tot de cookies of andere gevoelige gegevens die in de browser van het slachtoffer zijn opgeslagen. Daarnaast kunnen XSS-aanvallen worden gebruikt om phishing-aanvallen uit te voeren, waarbij de aanvaller het slachtoffer verleidt tot het verstrekken van gevoelige informatie door het kwaadaardige script te vermommen als een legitiem formulier of aanmeldingspagina.

Ter bescherming tegen XSS-aanvallen is het belangrijk dat ontwikkelaars van websites en webtoepassingen de input van gebruikers goed valideren en zuiveren. Dit kan worden gedaan door een combinatie van validatietechnieken aan server- en clientzijde, zoals het uitfilteren van potentieel gevaarlijke tekens of het gebruik van een firewall voor webtoepassingen om schadelijke verzoeken te blokkeren. Daarnaast moeten ontwikkelaars ervoor zorgen dat hun code vrij is van kwetsbaarheden die door aanvallers kunnen worden uitgebuit.

Voorbeeld van een XSS aanval:

```html
Input van de aanvaller:
<script>
  alert("XSS");
</script>

// Orginele HTML page:
<div id="comments">
  <h2>Comments</h2>
  <ul>
    <li>Comment 1</li>
    <li>Comment 2</li>
  </ul>
</div>

// Aangepaste HTML page:
<div id="comments">
  <h2>Comments</h2>
  <ul>
    <li>Comment 1</li>
    <li>Comment 2</li>
    <li>
      <script>
        alert("XSS");
      </script>
    </li>
  </ul>
</div>
```

In dit voorbeeld heeft de aanvaller een kwaadaardige JavaScript-code geleverd als commentaar op een website. Wanneer de website wordt geladen, wordt de JavaScript-code uitgevoerd in de context van de browser van het slachtoffer, waardoor een waarschuwingsvenster verschijnt met de melding "XSS". Dit type aanval wordt een cross-site scripting (XSS)-aanval genoemd omdat hierbij kwaadaardige JavaScript-code in een website of webtoepassing wordt geïnjecteerd.

### 6.3 OS command injection

OS command injection is een type beveiligingslek waarmee aanvallers willekeurige commando's kunnen uitvoeren op een computersysteem. Hierdoor kan de aanvaller ongeautoriseerde toegang tot het systeem krijgen, gevoelige informatie stelen of andere kwaadaardige acties uitvoeren.

Opdrachtinjectie van het besturingssysteem vindt meestal plaats wanneer een aanvaller kwaadaardige code kan invoegen in een programma of systeem dat is ontworpen voor interactie met het besturingssysteem. Dit kan op verschillende manieren gebeuren, onder meer door het gebruik van plug-ins van derden of door misbruik te maken van zwakke plekken in de programmacode.

Ter bescherming tegen OS commando-injectie aanvallen is het belangrijk dat ontwikkelaars gebruikersinvoer goed valideren en zuiveren. Dit kan worden gedaan door een combinatie van validatietechnieken aan server- en clientzijde, zoals het uitfilteren van potentieel gevaarlijke tekens of het gebruik van een firewall voor webtoepassingen om kwaadaardige verzoeken te blokkeren. Daarnaast moeten ontwikkelaars ervoor zorgen dat hun code vrij is van kwetsbaarheden die door aanvallers kunnen worden uitgebuit.

Hier is een voorbeeld van een OS command injection aanval:

```java
// Attacker-supplied input:
filename: "; rm -rf /; #

// Origineel:
String filename = request.getParameter("filename");
Process process = Runtime.getRuntime().exec("cat " + filename);

// Aangepast program:
String filename = request.getParameter("filename");
Process process = Runtime.getRuntime().exec("cat " + filename + "; rm -rf /; #");

```

In dit voorbeeld heeft de aanvaller een bestandsnaam opgegeven die een kwaadaardig OS-commando bevat. Dit commando is ontworpen om alle bestanden op het systeem te verwijderen, wat ernstige schade kan veroorzaken. De # aan het einde van het commando wordt gebruikt om de rest van de regel te commentariëren, waardoor het oorspronkelijke cat commando niet kan worden uitgevoerd.

## 7. Hoe kan je Injection tegen gaan?

Een manier om injectiekwetsbaarheden te voorkomen is het gebruik van een combinatie van server- en client-side validatietechnieken. Bij server-side validatie wordt gebruikersinvoer op de server gecontroleerd voordat deze wordt verwerkt, terwijl bij client-side validatie de gebruikersinvoer in de webbrowser van de client wordt gecontroleerd voordat deze naar de server wordt gestuurd. Dit kan helpen voorkomen dat aanvallers via gebruikersinvoer kwaadaardige code in het systeem invoeren.

Een andere manier om injectiekwetsbaarheden te voorkomen is het gebruik van query's met parameters of prepared statements. Bij deze technieken wordt de gebruikersinvoer gescheiden van de SQL-code, waardoor wordt voorkomen dat aanvallers kwaadaardige code in de SQL-query invoegen. Dit kan bescherming bieden tegen SQL-injectieaanvallen, een veelvoorkomend type injectieaanval.

Daarnaast kunnen ontwikkelaars web application firewalls (WAF's) gebruiken om zich tegen injectieaanvallen te beschermen. WAF's controleren inkomend verkeer en blokkeren verzoeken die mogelijk kwaadaardige code bevatten. Dit kan helpen voorkomen dat aanvallers via gebruikersinvoer kwaadaardige code in het systeem invoeren.

## 8. Kan mijn applicatie kwetsbaar zijn voor Injection?

### 8.1 Static code analysis

Doordat ik gebruik maak van sonarcloud heb ik de mogelijkheid om mijn code te laten analyseren op kwetsbaarheden. Hieronder zie je een screenshot van de resultaten van de analyse.

![sonarcloud](../images/SonarCloudZonder.jpg)

### 8.2 ORM

Daarnaast maak ik gebruik van een ORM. Een ORM kan beschermen tegen injectiekwetsbaarheden door automatisch veilige SQL-queries te genereren en uit te voeren op basis van de objecten die in de code worden gebruikt.

Neem bijvoorbeeld de volgende code die een ORM gebruikt om een gebruiker in een database in te voegen:

```java
User user = new User("John Doe", "johndoe@example.com");
entityManager.persist(user);
```

In dit voorbeeld genereert het ORM automatisch een SQL INSERT statement dat de gegevens van de gebruiker in de database invoegt. De ORM zal automatisch speciale tekens in de naam en het e-mailadres van de gebruiker escapen, wat voorkomt dat een aanvaller kwaadaardige SQL-code in de query invoegt. Dit kan helpen beschermen tegen SQL-injectie-aanvallen, een veel voorkomende soort injectie-aanval.

Kortom, een ORM kan bescherming bieden tegen injectiekwetsbaarheden door automatisch veilige SQL-query's te genereren en uit te voeren op basis van de objecten die in de code worden gebruikt. Dit kan helpen voorkomen dat aanvallers kwaadaardige SQL-code in de query invoegen, wat bescherming kan bieden tegen SQL-injectieaanvallen.

## 9. Conclusie

In dit onderzoek ben ik doormiddel van de deelvragen en het DOT framework gaan kijken naar de verschillende vormen van injection, Hoe deze werken en wat je kunt doen om deze te verkomen. Ik heb tijdens dit onderzoek een hoop meer informatie kunnen opdoen over injection. Nu kan ik dus de hoofdvraag beantwoorden.

> **Wat is Injection en hoe kan je dit tegengaan?**

Injectie is een soort beveiligingslek waarmee aanvallers kwaadaardige code in een computerprogramma of -systeem kunnen invoegen. Om zich tegen injectiekwetsbaarheden te beschermen, is het belangrijk dat ontwikkelaars de input van gebruikers goed valideren en zuiveren en ervoor zorgen dat hun code vrij is van kwetsbaarheden. Dit kan helpen voorkomen dat aanvallers ongeoorloofde toegang tot het systeem krijgen of gevoelige informatie stelen.

Het bestrijden van injectie omvat een aantal verschillende strategieën en technieken die zijn ontworpen om te voorkomen dat aanvallers misbruik maken van kwetsbaarheden in software. Dit kan een combinatie omvatten van validatie aan server- en clientzijde, het gebruik van query's met parameters of prepared statements, en het gebruik van firewalls voor webtoepassingen (WAF's).

## 10. Bronnen

- [Dot framework](https://ictresearchmethods.nl/The_DOT_Framework)
- [FHICT research reports](https://fhict.instructure.com/courses/12517/pages/research-reports-bachelor-students-only?module_item_id=835960)
- [Code injection](https://en.wikipedia.org/wiki/Code_injection)
- [Cross-site scripting](https://en.wikipedia.org/wiki/Cross-site_scripting)
- [Web application security](https://en.wikipedia.org/wiki/Web_application_security)
- [OWASP Foundation Top 10 security](https://owasp.org/www-project-top-ten/)
- [OWASP Foundation code injection](https://owasp.org/www-community/attacks/Code_Injection)
- [OWASP Foundation injection](https://owasp.org/Top10/A03_2021-Injection/)
- [OWASP Foundation Cross-Site Scripting (XSS)](https://owasp.org/www-community/attacks/xss/)
