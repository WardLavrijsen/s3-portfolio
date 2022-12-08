# Software Design World of content Live Score

## Inhoudsopgave

- [Software Design World of content Live Score](#software-design-world-of-content-live-score)
  - [Inhoudsopgave](#inhoudsopgave)
    - [Wie zijn World of Content (WoC)](#wie-zijn-world-of-content-woc)
    - [Wat is de opdracht voor World of Content (WoC)](#wat-is-de-opdracht-voor-world-of-content-woc)
  - [Requirements:](#requirements)
    - [Functionele requirements](#functionele-requirements)
    - [Non-functionele requirements](#non-functionele-requirements)
    - [Randvoorwaarden](#randvoorwaarden)
  - [Conceptioneel model](#conceptioneel-model)
  - [C4 model](#c4-model)
  - [ERD](#erd)
  - [AWS Architectuur](#aws-architectuur)

### Wie zijn World of Content (WoC)

World of Content levert aan zijn klanten een platform voor content delivery. zij zorgen ervoor dat jou content op alle platform klopt. Denk hierbij aan Coca-Cola. Zij hebben erg veel verschillende producten en willen dat deze bij al hun retailers overeenkomt. Hier komt World of content aan te pas. WoC zorgt ervoor dat een brand hun content op hun platform kan beheren en uitsturen naar alle verschillende retailers.

### Wat is de opdracht voor World of Content (WoC)

Voor de klanten van WoC is het moeilijk om een live score te zien. Dit betekent een score van hoeveel content er juist op de site staat. Komt de titel overeen? De beschrijving? De afbeelding? Etc. Daarom gaan we een platform maken die ervoor zorgt dat alle brands bij verschillende retailers kunnen zien of de data overeenkomt. Daarom ga ik in dit document de UX doen om ervoor te zorgen dat deze data in een gebruikersvriendelijke interface komt.

## Requirements:

Dit zijn de requirements vormgegeven volgens Moscow, gesorteerd op functionele en non- functionele requirements.

**FR** staat voor functionele requirement.

**NF** staat voor non-functionele requirement.

### Functionele requirements

- FR-01 Als gebruiker wil ik verschillende brands op de landing page zien, zodat ik mijn brand kan kiezen.

- FR-02 Als gebruiker wil ik verschillende retailers zien die bij de brand horen die ik heb aangeklikt, zodat ik naar die retailer kan gaan.

- FR-03 Als gebruiker wil ik verschillende producten zien die bij de retailer beschikbaar zijn van de brand die eerder is gekozen, zodat ik de totale score kan zien.

- FR-04 Als gebruiker wil ik een specifiek product zien van een brand die bij de retailer beschikbaar is, zodat ik specifiekere data over de live score kan zien.

- FR-05 Als gebruiker wil ik kunnen zien of de gegeven data overeenkomt met de retailer website doormiddel van een livescore, zodat ik een duidelijk overzicht heb.

### Non-functionele requirements

- NF-01 Als gebruiker wil ik dat de website zo snel mogelijk laad wanneer ik deze bezoek, zodat ik gelijk kan kijken of de content aanwezig is.

- NF-02 Als ontwikkelaar wil ik dat de live score wordt bijgehouden in een database, zodat deze makkelijk opgehaald kan worden.

- NF-03 Als ontwikkelaar wil ik dat de live score elke week geupdate word door opnieuw alle huidige data te scrapen, zodat de score up to date blijft.

- NF-04 Als ontwikkelaar wil ik dat alle applicaties maintainable en scalable zijn, zodat er in de toekomst gemakkelijk functionaliteit kan worden toegevoegd.

- NF-05 Als ontwikkelaar wil ik de state cachen, zodat als de applicatie crasht het niet opnieuw hoeft te beginnen.

- NF-06 Als ontwikkelaar wil ik na elke request dat er een seconden gewacht word, voordat er een nieuwe request word gemaakt bij een retailer website, zodat het ip niet geblokkeerd word.

### Randvoorwaarden

- Er word gebruik gemaakt van een web crawler en web scraper om content te controleren bij retailers.
- Er word gebruik gemaakt van Lambda functies binnen AWS voor de API.
- Er word gebruik gemaakt van localhost tijdens development.
- Er word gebruik gemaakt van Python voor de back-end.
- Er word gebruik gemaakt van Next.js voor de front-end.
- Er word gebruik gemaakt van een PostgreSQL database.

## Conceptioneel model

![Conceptioneel model](../images/Afbeeldingen/WoC-%20EER.png)

## C4 model

![C4 model](../images/Afbeeldingen/WoC%20-%20Architectuur%20Software.png)

## ERD

![ERD](../images/Afbeeldingen/S3GP3%20-%20ERD3.png)

## AWS Architectuur

![AWS Architectuur](../images/Afbeeldingen/WoC%20-%20Architectuur%20AWS.png)

Voor alle documentatie zie:

[GitHub](https://github.com/WJJCN/Documentation)
