# Software Quality Assurance

## Inhoudsopgave

- [Software Quality Assurance](#software-quality-assurance)
  - [Inhoudsopgave](#inhoudsopgave)
  - [1. Wat is Software Quality Assurance?](#1-wat-is-software-quality-assurance)
    - [2 Automatiseren](#2-automatiseren)
  - [2.1 CI/CD](#21-cicd)
  - [3. Unit Testing](#3-unit-testing)
  - [4. Integration Testing](#4-integration-testing)
  - [4. Static code analysis](#4-static-code-analysis)

## 1. Wat is Software Quality Assurance?

Sofware Quality Assurance is een van de belangrijkste dingen in de ontwikkeling van je software. De reden hiervoor is dat je wil dat je software goed werkt en dat je software niet kapot gaat. Stel je voor dat je een nieuwe versie released en alles breekt. Om dit te voorkomen zijn er allerlei manieren om goede software quality Assurance te hebben.

We maken software voor anderen. Hoogst waarschijnlijk degene die ervoor betalen. Zij verwachten natuurlijk dat je software van hoge kwaliteit is en zij er op kunnen bouwen. Door middel van quality Assurance kun je ervoor zorgen dat je software van hoge kwaliteit is en dat je software niet kapot gaat.

![Software Quality Assurance](https://mailtrap.io/wp-content/uploads/2020/06/testing_meme12.jpg)

### 2 Automatiseren

Als je constant al deze verschillende testen zou moeten doen ben je voor eeuwig bezig. Daarom is het super handig om dit te automatiseren. Je kunt dit doen door middel van een CI/CD pipeline.

## 2.1 CI/CD

CI/CD staat voor Continuous Integration en Continuous Deployment. Doormiddel van de CI/CD kunnen alle vormen van QA worden toegepast in mijn code en ervoor zorgen dat dit makkelijk verbeterd wordt.

Meer lezen over mijn CI/CD

[Naar Bestand](../README.md#46-cicd)

## 3. Unit Testing

Unit Testing is het testen van een klein stukje code. Dit kan een functie zijn of een stukje code. Dit is de meest bekende vorm van QA.

Doordat ik in dit project gebruik maak van veelal bestaande libraries is het niet mijn voorkeur om unit testing toe te passen. Dit omdat ik niet veel eigen logic code heb. Het zou dus een stuk verstandiger zijn om integration testing toe te passen.

## 4. Integration Testing

Integration Testing is het testen van een stukje code in combinatie met andere stukken code. Dit is een stuk minder bekend dan unit testing. Dit is ook de reden dat ik dit heb gekozen voor mijn project.

Voor de integration testen heb ik een h2 (in memory) database opgezet en heb ik een aantal testen geschreven. Deze testen testen de verschillende endpoints van mijn API. Dit doe ik door middel van een libary in quarkus. Deze test client stuurt een request naar de API en kijkt of de response goed is.

Voorbeeld van een integration test in java:

```java
@QuarkusTest
public class GameRecourceTest {
    @Test
    public void getGamesAjax() {
        given()
                .when().get("/api/game/88/194")
                .then()
                .statusCode(200)
                .body("size()", is(2));
    }
}

```

[Frontend repo](https://github.com/WardLavrijsen/FAST-Frontend.git) | [Backend repo](https://github.com/WardLavrijsen/FAST-Backend)

## 4. Static code analysis

Een andere manier om de kwaliteit van je code te testen is door middel van static code analysis. Dit is het analyseren van je code zonder dat je code wordt uitgevoerd. Ik heb dit gedaan door middel van sonarcloud te intergreren in mijn CI/CD pipeline. Hierdoor kan ik mijn code analyseren en verbeteren.

![Sonarcloud op het begin](../images/SonarCloudZonder.jpg)
_De eerste keer dat sonarcloud de static code analysis uitvoerde_

![Sonarcloud op het begin](../images/SonarCloudMet.jpg)
_Nadat ik de problemen had opgelost die in sonarcloud naar voren waren gekomen_

Zo zorgt deze static code analysis ervoor dat ik mijn code kan verbeteren.

Het grootste voordeel hieraan is dat op het moment dat ik de code push naar github, de CI/CD pipeline automatisch wordt uitgevoerd. Hieruit volgt een overzicht van de kwaliteit van mijn code. Hieruit krijg ik dus een duidelijk overzicht van wat ik moet verbeteren.

![Github CI](../images/StaticCodeGithub.jpg)
_Hier is te zien wat er bij deze CI fout ging._
