<div class="sdcs-header" markdown>
  ![](assets/images/nextjs-logo.png)
</div>

# NextJs Tutorial

## Een basis web app met NextJS
In deze tutorial maak je een basis NextJs web app. Je komt te weten hoe de app in elkaar steekt, hoe je nieuwe pagina's kan toevoegen en hoe je een data uit een database kunt verwerken in een NextJs applicatie.

## Voorbereiding
Installeer node.js, ga naar https://nodejs.org/en/download, kies je gewenste OS en download de installer. Voer de installer uit.

**Test of de installatie gelukt is**. Open een terminal en type:

`node -v`

Je moet nu het versienummer van de geïnstalleerde nodejs versie te zien krijgen.

## Template app maken

Open een terminal in de map waar je de applicatie wilt maken. In deze map wordt straks een nieuwe map gemaakt met de naam van je applicatie. 

Type:

`npx create-next-app@latest my-games`

Nu volgt een reeks vragen over je app. Geef de onderstaande antwoorden (tenzij je weet wat je doet en iets anders wilt):

*Would you like to use TypeScript?*  ► Yes  
*Which linter would you like to use?* ► None  
*Would you like to use Tailwind CSS?* ► Yes  
*Would you like your code inside a 'src/' directory?* ► Yes  
*Would you like to use App Router? (recommended)* ► Yes  
*Would you like to use Turbopack? (recommended)* ► Yes  
*Would you like to customize the import alias ('@/*' by default)?* ► No  

Nu wordt er een template applicatie gemaakt in de directory 'my-games'

Open de map 'my-games' in je favoriete editor. In deze tutorial wordt Visual Studio Code (VSCode) gebruikt.

Open ook een terminal en type:

```npm run dev```

Je app wordt nu in development mode uitgevoerd. Open een browser en navigeer naar http://localhost:3000

Je moet nu de template applicatie te zien krijgen. Houd de terminal en de browser open. Zolang je npm run dev in de terminal hebt draaien, zal de browser automatisch je wijzigingen laten zien, je hoeft dus niet te refreshen.

### Uitleg van de directories en files van het NextJs project
Neem even de tijd om je nieuwe project te bestuderen. Je ziet een aantal directories en bestanden. Het is handig om te weten waarvoor die directories en bestanden gebruikt worden. Hier is een korte uitleg van de directories en files van je NextJs project.

#### Directories
| Directory                                                                           | Beschrijving                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
|.next|In deze map staan bestanden en directories die NextJs gebruikt voor het bouwen van de app
|node_modules|In deze directory staan alle JavaScript libraries die de app gebruikt
|public|In de pubic map staan de bestanden die nodig zijn om de app uit te voeren
|src|Hier staat de source code van de applicatie zelf
|src/app|In de app directory staan de pagina's van je applicatie
|src/components|Hier bewaren we de componenten die we maken voor de app, zoals de navbar, footer, enz.

#### Files
| File                                                                           | Beschrijving                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
|next-env.d.ts
|next.congig.ts
|package.json|Dit bestand bevat lijsten met al je dependencies/libraries 
|tsconfig.json|Configuratie bestand voor TypeScript

## Pagina's toevoegen
We gaan nu de template app aanpassen zodat het meer onze eigen site gaat worden. Onderweg wordt uitgelegd hoe NextJs werkt.

### Pagina's en de router
Een site bestaat meestal uit meerdere pagina's. De **router** zorgt ervoor dat je gebruikers op de juiste pagina komen.

In dit project wordt de zogenaamde **Page Router** gebruikt. De Page Router zoekt automatisch in je app directory naar pagina's en toont die aan de gebruiker.

De enige pagina die je tot nu toe hebt staat in het bestand **page.tsx**. 

Open dit bestand in de editor. Er staat behoorlijk wat code in, maar dat is de template code. Verwijder alle code en kopieer de onderstaande code ervoor in de plaats.

```
export default function Home() {
  return (
      <main>
        <h1>Home Page</h1>
      </main>
  );
}
```
Bekijk het resultaat in de browser. Nog niet erg indrukwekkend, we gaan dit straks completer en mooier maken.

Nu gaan we een tweede pagina toevoegen en zal je zien hoe de router werkt.

Maak een nieuwe directory in de app directory en noem deze directory 'games'.

Maak in de nieuwe directory games een nieuw bestand en noem dit bestand **page.tsx**, dit wordt onze index pagina met een lijst van alle games.

Open het bestand games/pages.tsx in de editor en voeg de onderstaande code toe:

```
export default function GamesListPage() {
  return (
      <main>
        <h1>GamesList Page</h1>
      </main>
  );
}
```
Bekijk het resultaat in de browser. Je moet nu naar de GamesListPage pagina kunnen navigeren door de url **localhost:3000/games** te bezoeken.

!!! note "Hoe werkt de app router?"

    De App Router van NextJs zoekt in de **app directory** naar bestanden die **page.tsx** heten. Als je de url **/games** invult in de browser, zoekt de router naar een directory met de naam 'games' en daarin naar het bestand **page.tsx**. Vervolgens voert de router de **default function** uit.

    Het maakt verder niet uit hoe de default function genoemd wordt, de router zal altijd de **default function** uitvoeren.

We hebben nu twee pagina's, een Home page en de Games page. Tijd voor een navbar.

We maken onze navbar in een aparte file als een **component**.  

Maak in de **src** directory een nieuwe directory met de naam **components**. Maak in de directory components een nieuwe file met de naam **navbar.tsx**.

Voeg de onderstaande code toe:

```
export default function Navbar() {
  return (
    <nav className="flex gap-4 bg-gray-900 text-white p-4">
      <a href="/">Home</a>
      <a href="/games">Games</a>
    </nav>
  );
}
```

!!! note "Uitgebreidere navbars"

    De bovenstaande navbar is met opzet eenvoudig gehouden. Je kan op het Internet talloze voorbeelden van mooiere en complexere navbars vinden.


Nu hebben we het Navbar component beschikbaar om toe te voegen aan onze pagina's. Je zou natuurlijk het component in elke pagina apart kunnen toevoegen, maar het is makkelijker om het op een centrale plek te doen. 

Die centrale plek bestaat al. In de file **layout.tsx** zit de algemene code voor onze pagina's. Alle pagina's worden gemaakt met layout.tsx als basis. 

Open het bestand app/layout.tsx en 

Voeg in het **<body\>** element het Navbar component toe.

```
(...)
<body>
  <Navbar/>
  {children}
</body>
(...)
```
Nu heb je op elke pagina een navbar.

Kijk nog even terug naar layout.tsx. Je ziet in de body **{children}** staan. Dit is de **placeholder** voor de pagina's die je maakt in de applicatie. De inhoud van je pagina's wordt door NextJs op de plek van {children} gezet.

!!! note "Tailwind autocomplete in VSCode"
    Om in VSCode autocomplete voor Tailwind css classes te krijgen installeer je de officiële Tailwind CSS InteliSense extension in VSCode

