# Software Design FAST

## Inhoudsopgave

- [Software Design FAST](#software-design-fast)
  - [Inhoudsopgave](#inhoudsopgave)
  - [Inleiding](#inleiding)
  - [Projectomschrijving:](#projectomschrijving)
  - [Waarom dit project:](#waarom-dit-project)
  - [Waaruit gaat de applicatie bestaan:](#waaruit-gaat-de-applicatie-bestaan)
  - [Planning:](#planning)
    - [Sprint 1:](#sprint-1)
    - [Sprint 2:](#sprint-2)
    - [Sprint 3:](#sprint-3)
    - [Sprint 4:](#sprint-4)
    - [Sprint 5:](#sprint-5)
  - [Requirements:](#requirements)
    - [Functionele:](#functionele)
    - [Niet-Functionele:](#niet-functionele)
  - [Gesprekken Stakeholders:](#gesprekken-stakeholders)
    - [Gesprek 1:](#gesprek-1)
    - [Gesprek 2:](#gesprek-2)
  - [ORM](#orm)
    - [Implementeren ORM](#implementeren-orm)
    - [Entity](#entity)
  - [C4 Model](#c4-model)
  - [Distributated Software](#distributated-software)
    - [Wat is distributated software?](#wat-is-distributated-software)
    - [Hoe is dit toegepast in mijn project?](#hoe-is-dit-toegepast-in-mijn-project)
  - [REST API](#rest-api)
    - [Wat is een REST API?](#wat-is-een-rest-api)
      - [Client-server](#client-server)
      - [Stateless](#stateless)
      - [Cacheable](#cacheable)
      - [Uniform interface](#uniform-interface)
      - [Layered system](#layered-system)
      - [Code on demand](#code-on-demand)
    - [Verbs](#verbs)
    - [Status codes](#status-codes)
    - [REST API in mijn project](#rest-api-in-mijn-project)
  - [Asynchronous](#asynchronous)
    - [Wat is asynchronous?](#wat-is-asynchronous)

## Inleiding

In dit document zijn de requirements, de algemene planning

Projectdocumentatie software semester 3
Forza Automation System for Tickets (FAST)

## Projectomschrijving:

Het Forza Automation System for Tickets kort gezegd FAST wordt gevoed door een website waarop aangegeven kan worden welke wedstijden, clubs en competities in het systeem moeten komen. Daarna wordt er dagelijks van de externe ticketpartners alle data opgehaald die bij tickets komen kijken. Dit allemaal in een database opgeslagen zodat het makkelijk is om alle recente ticketprijzen te kunnen zien. Deze info is dan allemaal terug te zien op deze website maar is ook te koppelen door middel van een API aan de al bestaande website.

## Waarom dit project:

Dit project is opgezet voor Forza Voetbalreizen. Het probleem binnen dit bedrijf is dat alle prijzen, wedstrijden en tickets handmatig ingevoerd moeten worden, dit wordt daarna opgeslagen in een super complex Excel bestand. Dit is super foutgevoelig en kost erg veel tijd. Eerst moet op het begin van elk seizoen alle wedstrijden die ze aanbieden handmatig in het systeem gezet worden. Daarna moeten bij alle ticketpartners om prijzen gevraagd worden en dit moet allemaal in een Excel bestand komen. Doordat dit op het begin van het seizoen gebeurt kan dit betekenen dat de website is gevoed met te lage prijzen, verkeerde beschikbaarheid of andere problemen die komen kijken bij niet geüpdatete prijzen. Dit betekent dus dat er bij iedere wijziging een update moet plaatsvinden. Dit kost super veel tijd. En dat is wat FAST kan oplossen door dit allemaal automatisch te doen.

## Waaruit gaat de applicatie bestaan:

- Inlogsysteem voor de beveiliging.
- Database om alle info in op te slaan.
- Externe API’s van ticketpartners.
- API om deze geautomatiseerde info te gebruiken in andere producten.
- Website om alle voorkeuren en wedstrijden op aan te geven.
- Iedere dag updates van prijzen.
- Pagina’s om prijzen toe te voegen van ticketpartners zonder API.

## Planning:

Ik ga mijn planning opdelen in sprints van 3 weken. Dit betekent dat er in totaal 5 sprints zijn.

### Sprint 1:

In sprint 1 wil ik me focussen op de inhoud van het project, de requirements, use cases en de communicatie richting Forza Voetbalreizen over wat voor hen belangrijk is en wat ze er graag in willen zien. Na dat ik weet wat er gebouwd moet gaan worden ga ik kijken welke talen, frameworks en database het beste passen bij dit project.

### Sprint 2:

Eerst begin ik met het verwerken van feedback, zowel vanuit de docenten als vanuit de stakeholder gezien. Aangezien dit project erg gefocust is op communicatie met externe partijen ga ik deze sprint de focus leggen op het uitzoeken en begrijpen van deze externe partijen. Kijken hoe deze API’s eruitzien en ervoor zorgen dat ik de juiste data hieruit kan halen.

### Sprint 3:

Na het verwerken van de feedback ga ik beginnen met het opzetten van een database en de backend vorm geven. Hierbij de kennis die ik in sprint 2 heb opgedaan voor de externe API’s toepassen en zorgen dat dit een mooi geheel wordt in de backend.

### Sprint 4:

Eerst feedback verwerken en daarna aan de slag met het front-end. Eerst maak ik een design en overleg ik met de stakeholder de kwaliteit en eventuele wijzigingen. Als deze dan zo is zoals de stakeholder hem graag wil zien ga ik dit implementeren en verbinden met de backend zodat het makkelijk te gebruiken is.

### Sprint 5:

Ik begin met het verwerken van feedback maar ga geen grootte functies meer toevoegen. Ik zorg ervoor dat het wordt afgewerkt en de belangrijkste functionaliteiten erin zitten. Daarnaast ga ik de leeruitkomsten bekijken en aanpassingen maken zodat ik deze allemaal goed aan toon. Daarna lever ik het op bij de stakeholder voor de feedback vanuit hen.

## Requirements:

### Functionele:

- Als gebruiker wil ik een competitie kunnen selecteren zodat ik kan aangeven welke competities wel en niet aangeboden worden.
- Als gebruiker wil ik een club kunnen selecteren zodat ik kan aangeven welke competities wel en niet aangeboden worden.
- Als gebruiker wil ik een wedstrijd kunnen selecteren zodat ik kan aangeven welke competities wel en niet aangeboden worden.
- Als gebruiker wil ik een ticketcategorie kunnen aanmaken zodat je prijzen eerlijk vergelijkt.
- Als gebruiker wil ik een ticketcategorie kunnen aanpassen en verwijderen zodat ik altijd de nieuwste categorieën heb.
- Als gebruiker wil ik van iedere wedstrijd de verschillende prijzen kunnen zien zodat ik altijd weet welke wedstrijd het goedkoopste is.
- Als gebruiker wil ik kunnen inloggen zodat de data beschermd is.
- Als gebruiker wil ik ticketpartners kunnen selecteren van een competitie zodat ik kan selecteren welke ticketpartners ik voor iedere competitie wil zien.
- Als gebruiker wil ik een ticketpartner kunnen toevoegen.
- Als gebruiker wil ik handmatig prijzen kunnen invoegen zodat ik bij ticketpartners die geen API hebben alsnog prijzen in het systeem heb.
- Als gebruiker wil ik dat de data geëxporteerd kan worden zodat ik deze op de boekingswebsite kan toepassen.

### Niet-Functionele:

- Als gebruiker wil ik dat mijn website voor mobiel werkt zodat ik prijzen makkelijk op mijn telefoon kan zien.
- Als gebruiker wil ik dat de prijzen iedere avond geüpdatet worden zodat ik altijd de meest recente prijzen kan zien.
- Als gebruiker wil ik dat de data binnen 1 seconde inlaadt zodat ik niet lang hoef te wachten als er een klant naar prijzen vraagt.

## Gesprekken Stakeholders:

Doordat mijn vader mijn stakeholder is heb ik af en toe gesprekken gezien de requirements, ui en andere componenten die met de stakeholder besproken moeten worden.

### Gesprek 1:

Tijdens het eerste gesprek is de basis van het project besproken. Hieruit is de omschrijving, de requirements en de planning opgekomen.

### Gesprek 2:

In het 2de gesprek zijn de requirements doorgelopen en het eerste design laten zien. Hieruit is naar voren gekomen dat het belangrijk is om ook een verschil in ticketcategorie te hebben. Zo heeft iedere club dus ook nog verschillende soorten kaartjes. Deze moeten dus ook geselecteerd kunnen worden en daarop toegepast kunnen worden.

- Frame van de opdracht laten zien.
- Planning besproken.
- Front-end design doorlopen en veranderingen doorgevoerd.
- Inhoud van het project besproken.
- Aanpassing in de ticket categorie.
- Bekeken hoe de verschillende ticket categorieën in elkaar zitten bij de ticketpartners.
- Hoe de verschillende ticketpartners de prijzen aanleveren en dus daarbij gekeken hoe dit het makkelijkste doorgevoerd kan worden.

Nieuwe Requirements na dit gesprek:

- Prijzen moeten handmatig ingevoerd kunnen worden.
- Ticket categorieën aanmaken.
- Ticket categorieën wijzigen en verwijderen.
- Het filteren van wedstrijden op bijvoorbeeld datum. (Could Have)

## ORM

Ik heb gekozen voor een ORM omdat ik hiermee makkelijk kan werken en ik niet zelf de queries hoef te schrijven. Hierdoor kan ik me meer focussen op de functionaliteiten en de kwaliteit van de code.

Ik heb gebruik gemaakt van de panache Libarary in Quarkus. Deze library is een ORM die gebruik maakt van Hibernate. Hierdoor kan ik makkelijk queries maken en de data opslaan in een database.

#### Implementeren ORM

```java
@ApplicationScoped
public class ClubRepository implements PanacheRepository<Club>{}
```

#### Entity

```java
@Entity
public class Club {
    @Id
    private Integer id;
    private String name;
    private String logo;
    private Integer leagueId;

    public Club() {
    }

    public Club(Integer id, String name, String logo, Integer leagueId) {
        this.id = id;
        this.name = name;
        this.logo = logo;
    }
```

## C4 Model

[Image: C4 Model fase 1]
![C4 Model 1](/images/C4%20FAST%201.png)

[Image: C4 Model fase 2]
![C4 Model 1](/images/C4%20FAST%202.png)

## Distributated Software

### Wat is distributated software?

Distributated software is software die op meerdere servers draait. Deze servers kunnen op verschillende locaties staan. De servers kunnen ook verschillende taken hebben. Zo kan er een server zijn die alleen de data opslaat en een server die alleen de data verwerkt. Dit is een voorbeeld van distributated software.

### Hoe is dit toegepast in mijn project?

Het project is opgedeeld in 4 verschillende services. Deze services zijn:

- Front-end
- Back-end
- Database
- Externe API

De front en back-end service communiceren met elkaar via een REST API. De frontend kan dus de data ophalen van de backend. De backend kan de data ophalen van de database en de externe API. De database slaat de data op en de externe API haalt is de data van de ticketpartners en voetbal API.

De database en de Backend communiceren via jbdc.

## REST API

### Wat is een REST API?

Een REST API is een API die gebruik maakt van de REST principes. REST staat voor Representational State Transfer. REST is een architectuur die gebruikt wordt om data uit te wisselen tussen verschillende systemen. REST is een architectuur die gebruik maakt van HTTP. REST is een architectuur die gebruik maakt van de 6 principes:

- Client-server
- Stateless
- Cacheable
- Uniform interface
- Layered system
- Code on demand

#### Client-server

De client-server architectuur is een architectuur waarbij de client en de server gescheiden zijn. De client is de gebruiker van de applicatie en de server is de applicatie zelf. De client kan dus niet direct met de server communiceren. De client moet dus eerst een request sturen naar de server. De server kan dan een response terugsturen naar de client.

#### Stateless

De stateless architectuur is een architectuur waarbij de server geen informatie over de client bijhoudt. De server weet dus niet wie de client is. De server weet dus ook niet wat de client eerder heeft gedaan, heeft opgevraagd, heeft veranderd of heeft verwijderd.

#### Cacheable

De cacheable architectuur is een architectuur waarbij de server de data kan opslaan in een cache. De cache is een tijdelijke opslagplaats.

#### Uniform interface

De uniform interface architectuur is een architectuur waarbij de server en de client dezelfde interface gebruiken. De server en de client gebruiken dezelfde taal. De server en de client gebruiken dezelfde data structuur. De server en de client gebruiken dezelfde communicatie protocollen.

#### Layered system

De layered system architectuur is een architectuur waarbij de server en de client in verschillende lagen zijn opgedeeld.

#### Code on demand

De code on demand architectuur is een architectuur waarbij de server code kan uitvoeren op de client.

Dit is super fijn omdat de server en de client dan makkelijk met elkaar kunnen communiceren. De server en de client hoeven dus niet te weten hoe de andere applicatie werkt. De server en de client hoeven dus niet te weten hoe de andere applicatie is opgebouwd.

### Verbs

Verbs zijn de HTTP methodes. De HTTP methodes zijn GET, POST, PUT, PATCH en DELETE. De GET methode wordt gebruikt om data op te halen. POST om data op te slaan. PUT om data te veranderen. PATCH om data te veranderen. DELETE om data te verwijderen.

### Status codes

Status codes zorgen ervoor dat de client weet wat de server heeft gedaan. De reden waarom dit zo handig is en de reden is waarom het veel wordt gebruikt is omdat de client dan bijvoorbeeld een foutmelding laten zien als de server een foutmelding heeft gestuurd.

Zo heb je bijvoorbeeld 200 voor dat het goed is.
Zo heb je bijvoorbeeld 400 voor dat er een fout is.
en 500 voor dat er een server fout is.

![Status Code memes](https://preview.redd.it/z6mbo9dyc1x51.jpg?auto=webp&s=a0b3e0d975fd1467598689bfb7162d7fef44e8b7)
_Hoe het niet moet_

### REST API in mijn project

In mijn project heb ik een REST API gemaakt. Deze REST API is gemaakt met Quarkus. Quarkus is een Java framework die gebruik maakt van de REST principes.

## Asynchronous

### Wat is asynchronous?

Asynchrone communicatie is vaak een complex onderwerk maar met deze voorbeelden is het heel logisch

- Als je de vaatwasser aanzet wacht je dan tot deze klaar is?
- Als je een mail stuurt wacht je dan tot de ontvanger deze heeft gelezen?
- Als je een bestelling plaatst wacht je dan tot je pakket binnen is?

Nee, je wacht niet tot de vaatwasser klaar is, je wacht niet tot de ontvanger de mail heeft gelezen en je wacht niet tot je pakket binnen is. Je doet andere dingen terwijl je wacht. Dit is asynchrone communicatie.

Hoe heeft dit dan met software te maken?

Simpel, je software gaat iets anders doen in de tijd dat het bijvoorbeeld op de API wacht.

Dit zorgt er bijvoorbeeld voor dat je applicatie niet vastloopt als de API niet reageert. Dit zorgt er ook voor dat je applicatie sneller is.

Zo zou je applicatie zonder asynchrone communicatie bijvoorbeeld niet werken als er op een button wordt geklikt.

![async](https://velog.velcdn.com/images%2Fazurestefan%2Fpost%2F37a894d3-d473-4a9a-8445-2164d2f58439%2Fimage.png)
_Hier zie je hoe asynchrone communicatie werkt in javascript_

```js
(async () => {
  try {
    const res = await axios.get(
      "http://localhost:8080/api/game/" +
        searchParams.get("leagueid") +
        "/" +
        searchParams.get("clubid")
    );
    setData(res.data);
  } catch (error) {
    console.error("error");
    console.error(error);
  }
})();
```

_Dit is een voorbeeld van asynchrone communicatie in mijn frontend_
