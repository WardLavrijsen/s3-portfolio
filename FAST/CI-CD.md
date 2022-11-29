# Continuous Integration and Continius Deployment

## Inhoudsopgave

- [Continuous Integration and Continius Deployment](#continuous-integration-and-continius-deployment)
  - [Inhoudsopgave](#inhoudsopgave)
  - [1. Wat is CI/CD?](#1-wat-is-cicd)

## 1. Wat is CI/CD?

CI/CD zorgt ervoor dat je het testen en deployen van je software automatisch kan doen. Dit is super handig. Je kunt dit doen door middel van een CI/CD pipeline.

Voor mijn project heb ik gebruik gemaakt van Github Actions. Via hier heb ik alle verschillende stappen van mijn CI/CD pipeline gemaakt. Hieronder zie je een voorbeeld van mijn CI/CD pipeline.

Dit is ook erg belangrijk voor de klant omdat zij hierdoor makkelijk updates kunnen doen en de software altijd up to date is.

![Software Quality Assurance](https://flexagon.com/wp-content/uploads/2020/04/a-world-without-ci.cd-meme.jpg)

om dit te doen heb ik gebruik gemaakt van Github Actions. Dit is een gratis tool die je kan gebruiken om CI/CD te doen. Ik heb hier een workflow voor gemaakt die elke keer als er een push wordt gedaan naar de master branch de software gaat builden en testen. Als dit succesvol is wordt de software gedeployed naar de server. Ook heb ik een workflow gemaakt die elke keer als er een pull request wordt gedaan de software gaat builden en testen. Als dit succesvol is kan de pull request gemerged worden. Dit is erg handig omdat je dan weet dat de software altijd werkt en dat er geen fouten in de software zitten.

![Github CI](./images/StaticCodeGithub.jpg)
_CI/CD zorgt ervoor dat je alle problemen meteen tegenkomt._

[Frontend CI](/FAST/FrontendIntegrade.yml) | [Frontend CD](/FAST/FrontendDeploy.yml)

[Backend CI](/FAST/BackendIntegrade.yml) | [Backend CD](/FAST/BackendDeploy.yml)

[Frontend repo](https://github.com/WardLavrijsen/FAST-Frontend.git) | [Backend repo](https://github.com/WardLavrijsen/FAST-Backend)
