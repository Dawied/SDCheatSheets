<div class="sdcs-header" markdown>
  ![](assets/images/Laravel-tutorial-logo.png)
</div>

# Laravel Tutorial

## Een Password Manager met Laravel
In deze tutorial programmeer je een password manager. Je kan er je wachtwoorden voor sites waar je moet inloggen mee bewaren. 

Als je de tutorial stap voor stap volgt maak je kennis met veel basis technieken die je ook in andere projecten kunt toepassen. 

Aan het eind van de tutorial heb je een werkende password manager, maar valt er ook nog genoeg te verbeteren en toe te voegen.

Aan de slag!

## Functionaliteiten
Het is een goede gewoonte om van te voren een lijst te maken met functionaliteiten voor je project. Elke functionaliteit krijgt een omschrijving en een prioriteit. De prioriteit bepalen we met de **M**o**SC**o**W** methode:

**M**ust-have<br>
Functionaliteit die absoluut gerealiseerd moet worden

**S**hould-have<br>
Functionaliteit die belangrijk is, maar eventueel een volgende versie gerealiseerd kan worden

**C**ould-have<br>
Ook wel nice-to-haves genoemd, leuk als het lukt, maar het kan ook later

**W**ill-not-have<br>
Functionaliteit die we niet in deze versie gaan maken, misschien in een latere versie wel 

Hier is de lijst met functionaliteiten en de prioriteiten. In de tutorial realiseren we alleen de Must-haves:

|Functionaliteit|Prioriteit|
|---|---|
|Wachtwoorden toevoegen|M|
|Wachtwoorden wijzigen|M|
|Wachtwoorden verwijderen|M|
|categoriën toevoegen|M|
|categoriën wijzigen|M|
|categoriën verwijderen|M|
|Een master password gebruiken om toegang te krijgen (per user)|M|
|Opgeslagen wachtwoorden versleutelen met het master password|M|
|Wachtwoorden kunnen zoeken|S|
|Wachtwoorden kunnen groeperen op categorie|S|
|Automatisch vragen om wachtwoorden op te slaan (Browser extensie)|W|
|Automatisch wachtwoorden invullen op sites (Browser extensie)|W|

## Database ontwerp
Voordat we kunnen starten met bouwen gaan we een database ontwerp maken. We hebben in elk geval drie tabellen nodig. Een users tabel voor de gebruiker(s) van de applicatie, een tabel om de wachtwoorden in op te slaan, een een tabel om de categoriën op te slaan.

Het database diagram ziet er als volgt uit:

TODO: ERD maken

We beschrijven de kolommen van de tabellen in een datadictionary:

TODO: Datadictionary maken

## Laravel project opzetten

## Migrations

## Seeders

## Models en Controllers

## Views

