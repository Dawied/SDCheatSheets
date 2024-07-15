<div class="sdcs-header" markdown>
  ![](assets/images/HTML5-logo.png)
</div>

# HTML Cheat sheet

## HyperText Markup Language
Dat is waar de afkorting HTML voor staat. Markup wil zeggen dat we speciale markeringen (tags) gebruiken om het document vorm te geven in de Browser.

HTML code is platte tekst. Met andere woorden gewoon alleen maar tekst. Net als alle andere broncode (source code).

De eerste versie van HTML is in 1993 ontstaan, de laatste versie is HTML5 en bestaat sinds 2014. Voorlopig komt er geen HTML6. HTML5 zal zich blijven aanpassen aan de nieuwe ontwikkelingen op het web. De ontwikkelingen van HMTL5 kan je hier volgen: [WHATWG HTML Living Standard](https://html.spec.whatwg.org/). 


## <!DOCTYPE html>
Een HTML document start altijd met <!DOCTYPE html> Dit is geen onderdeel van de code maar hieraan herkent de browser dat we met html te maken hebben.

## Tags
HTML code wordt geschreven binnen tags. Een tag heeft een begin en een eind. De combinatie van begintag en eindtag wordt een **html element** genoemd.

Bijvoorbeeld de begintag voor een kopje is **<h1\>**, en de eindtag is **</h1\>** tussen de begintag en de eindtag komt de tekst van de kop. Dus zo:

```
<h1>Welkom bij mijn site</h1>
```
En zo werkt het met de meeste andere elementen.

## Attributen
Een tag kan attributen hebben. Een attribuut vertelt iets over de tag. Bijvoorbeeld de tag <html\> kan een attribuut **lang** hebben waarmee wordt aangegeven in welke taal de tekst van de html pagina is geschreven. Dit is nuttige informatie voor de Browser.

Dat ziet er dan zo uit:

```
<html lang="en"><html\>
```
Een attribuut heeft altijd de vorm: **naam="waarde"** Dus hierboven is de attribuutnaam **lang** en de waarde is **en**



## Basis opmaak
Een basis html document bestaat uit de tags <html\> en <body\>:

```
<!DOCTYPE html>
<html>
<body>
  <h1>Welkom bij mijn site</h1>
</body>
</html>
```
In de body komt de rest van de html code. Alleen wat in de body staat wordt zichtbaar in de Browser.

## De head <head\>
Een html document heeft meestal ook een head. In de head staat informatie over het html document. Je ziet de head niet in de Browser, maar de Browser gebruikt de head wel om speciale dingen over het document te weten te komen.

*Verwar de <head\> niet met het element <header\>, dat je in de body kunt zetten om bijvoorbeeld een inleiding voor je pagina te schrijven.*

De volgende elementen kunnen in de head staan:

|Element|Gebruik|
|---|---|
|<title\>|De title van het document, zie je terug in de tab van de Browser|
|<style\>|CSS style die op de pagina gelden|
|<meta\>|Algemene informatie|
|<link\>|Een link naar een ander bestand, bijvoorbeeld JavaScript of CSS|
|<script\>|Een stukje JavaScript code|

## Links
Links, of hyperlinks, zijn klikbare text die naar een andere HTML pagina leiden. Je maakt ze met de **<a\>** tag en de **href** [attribuut](#attributen).

```
<a href="https://www.w3schools.com/tags/tag_a.asp">W3 Schools over links</a>
```
Een link krijgt verschillende kleuren afhankelijk van of erop geklikt is of niet.

|Status|Kleur|
|---|---|
|Niet geklikt|De links is blauw|
|Geklikt|De links is paars|
|Actief|De links is rood|


## vscode html5 basis genereren
Met Visual Studio Code kan je snel de basis voor een html5 document genereren. Type html, kies html5 en Enter

<p align="center">
  <img src="/assets/gifs/vscode-html.gif">
</p>

Op dezelfde manier kan je allerlei html code laten genereren. Type het begin van de html markup die je nodig hebt en kies uit het menu.

