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
  - [C4 Model](#c4-model)

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

## C4 Model

[Image: C4 Model fase 1]
![C4 Model 1](/images/C4%20FAST%201.png)

[Image: C4 Model fase 2]
![C4 Model 1](/images/C4%20FAST%202.png)
