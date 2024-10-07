<div class="sdcs-header" markdown>
  ![](assets/images/Laravel-logo.png)
</div>



# Laravel Cheat Sheet

## Het Laravel Framework
Laravel is een populair PHP framework waarmee je snel een complete en veilige applicatie voor het web kunt maken. Iedere twee jaar verschijnt er een nieuwe versie van het framework. Laravel kan gecombineerd worden met diverse JavaScript frameworks zoals VUE en React. Met Laravel **Breeze** (Tailwind CSS) of **Laravel UI** (Bootstrap CSS) kan je snel een compleet gebruikerssysteem met authorisatie toevoegen.

## Bronnen
Buiten deze Cheat Sheet om zijn hier nog een paar interessante sites met informatie over Laravel

| Site                                                                           | Beschrijving                                                        |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| <a href="https://laravel-news.com/category/tutorials">Laravel Tutorials</a> | Links naar betrouwbare Laravel tutorials |
| <a href="https://laracasts.com/">Laracasts</a>|Tutorials en een uitgebreid forum om vragen in te stellen of antwoorden te vinden|
| <a href="https://laravel.com/docs/11.x">Laravel Docs</a>|Officiële documentatie. Let op dat je in de juiste versie van de documentatie kijkt, rechtsbovenin kan je de benodigde versie kiezen.|

## Benodigdheden

### Composer
Composer is de package manager voor PHP. Hiermee kan je PHP packages/libraries eenvoudig installeren.

Download Composer voor je eigen OS en installeer:

https://getcomposer.org/download/

### Node.js
Node.js is een JavaScript runtime environment. Met Node.js kan je JavaScript gebruiken buiten de Browser om. Dit is nodig om JavaScript onderdelen binnen de Laravel applicatie te gebruiken.

Download Node.js voor je eigen OS en installeer:

https://nodejs.org/en/download

### PHP 8.2+
Voor Laravel 11 heb je minimaal PHP 8.2 nodig. Download en installeer PHP voor jouw OS.

### Extra tools
Composer, Node.js en PHP heb je minimaal nodig. Maar voor veel applicaties heb je ook een **Database** nodig. Laravel werkt met diverse databases zoals SQLite, MySQL/MariaDB, PostgresSQL. Een populaire keuze is MySQL/MariaDB.

Als **IDE** werkt Visual Studio Code prima. Een andere veelgebruikte IDE voor Laravel is PHPStorm of IntelliJ.

Een **Database Manager** is handig om je databases mee te beheren. PHPMyAdmin een optie, maar voor een upgrade in gebruikersgemak gebruik je en van onderstaande opties.

Een veelgebruikte tool is DataGrid van Jetbrains. DataGrid is ook geintegreerd aanwezig in PHPStorm en IntelliJ. Voor VS Code zijn er plugins beschikbaar waarmee je de database kan beheren. 

## Een nieuw Laravel project maken

Als je PHP, Composer en Node.js heb geïnstalleerd, open je een nieuwe terminal. Navigeer naar de directory waar je het project wilt bewaren. Bedenk een naam voor je project. In de voorbeelden gebruiken we als naam **my-app**.

Type in de terminal het volgende commando:

```
composer create-project laravel/laravel my-app
```

Er wordt nu een basis Laravel applicatie gemaakt in de map 'my-app'. Navigeer naar deze nieuwe map:

```
cd my-app
```
!!! note "De root directory"

    Vanaf nu voer je alle commando's voor je applicatie uit in de **root** directory van de applicatie. Dit is in het voorbeeld dus de 'my-app' directory. Zorg ervoor dat alle terminals die je gebruikt altijd in deze directory staan, anders werken de commando's niet.


## Database instellingen in .env
Start je IDE (VSCode of een andere IDE) en open de map met de applicatie. Ga op zoek naar het bestand '**.env**' en open dit bestand in de IDE. In het bestand .env staan de basisinstellingen voor je applicatie. Een van die instellingen is welke database je wilt gebruiken. Standaard is dit SQLite. Als je bijvoorbeeld MySQL/MariaDB gebruikt dan moet je nu de inloggegevens voor in .env toevoegen.

Pas voor MySQL de volgende regels aan en vervang de waarden met de inloggegevens voor jouw database:

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=myapp
DB_USERNAME=myapp_admin
DB_PASSWORD=secretpassword
```
Hierna voer je het onderstaande commando uit in een terminal in de map 'my-app':

```
php artisan migrate
```
Als de database myapp nog niet bestaat dan zal Laravel vragen of de database aangemaakt moet worden. Kies 'yes'.
Nu worden de standaard tabellen 'users', 'cache' en 'jobs' aangemaakt in je database.

## De applicatie gebruiksklaar maken en starten
Open een nieuwe terminal in de map 'my-app' en voor het volgende commando uit:

```
npm install
```
Hiermee installeer je de benodigde JavaScript packages.

en daarna:

```
npm run dev
```

Hiermee start je de Vite development server. Door dit commando in de achtergrond actief te houden worden wijzigingen in JavaScript en CSS automatisch verwerkt en krijg je  **hot reload** functionaliteit. Daardoor hoef je de Browser niet te verversen om je wijzigingen te zien.

Open opnieuw een terminal en run het volgende commando:

```
php artisan serve
```

Hiermee start je de Laravel development server. Je kunt je nieuwe Laravel app nu bekijken door met de Browser het adres http://localhost:8000 te bezoeken.

De applicatie blijft actief zolang je het commando php artisan serve in de terminal actief laat. Sluit deze terminal dus niet. Je kan de terminal van je OS gebruiken of een terminal in je IDE.

Er zijn nog andere opties om een Laravel ontwikkelomgeving op te zetten en de applicatie te runnen. Check hiervoor: 
https://laravel.com/docs/11.x/installation

## Een user systeem toevoegen
Er bestaan twee Laravel packages waarmee je een usersysteem kan toevoegen aan je applicatie. De nieuwste tool is **Breeze**, hiermee wordt een usersysteem met Tailwind CSS gemaakt.

De **Laravel-ui** package bevat boilerplate code voor een basis registratie- en login systeem. Je kunt Laravel-ui Bootstrap als CSS laten gebruiken. Die optie bestaat niet voor Breeze 

Kies een van de twee packages, afhankelijk van je eigen voorkeur.

Ga terug naar de terminal vanwaaruit je de applicatie hebt gestart en run de volgende commando's en beantwoord vragen om bestanden te overschrijven met 'yes':

### Laravel UI (met Bootstrap)
```
composer require laravel/ui
php artisan ui bootstrap --auth
npm install
```

### Laravel Breeze (met Tailwind)
```
composer require laravel/breeze
php artisan breeze:install
npm install
```

Hiermee wordt een kant en klaar gebruikerssysteem geïnstalleerd.

Omdat er nieuwe tabellen in de database nodig zijn voor het gebruikerssysteem, moet je nogmaals het **artisan migrate** commando uitvoeren:

```
php artisan migrate
```

De Laravel applicatie moet nu een functionerend registratie- en loginsysteem hebben. Je kan het zelf uitbreiden met bijvoorbeeld een rollensysteem. De gebruikers worden opgeslagen in de tabel 'users'.

## De ontwikkelomgeving
Om snel en goed met Laravel te werken is een **IDE** een must! Gebruik bijvoorbeeld **Visual Studio Code** of **PHPStorm**. Je IDE heeft ook terminals ingebouwd die je kan gebruiken om je Laravel app te besturen.

Je gebruikt **drie terminals**. Alledrie moeten geopend staan in de root van je applicatie folder. 

De **eerste** terminal gebruik jijzelf om bijvoorbeeld artisan commando's uit te voeren.

De **tweede** terminal draait een ontwikkelomgeving voor de JavaScript onderdelen via het commando 'npm run dev'. Bovendien geeft dit commando je een hot reload, waardoor je wijzigingen direct terugziet in de Browser.

De **derde** terminal draait de Laravel ontwikkelomgeving inclusief een ingebouwde webserver om de applicatie te serveren. Het commando voor deze terminal is 'php artisan serve', en de applicatie is te vinden op url: http://localhost:8000

## Artisan
Artisan is de command line tool van Laravel. Met Artisan beheer je je Laravel applicatie. Je kunt er boiler plate code mee genereren, de cache mee beheren, de database beheren en meer. 

Artisan is een PHP applicatie, dus je start artisan met 'php' ervooor, bijvoorbeeld: 'php artisan migrate'.

## Migrations
In Laravel worden tabellen in je database gedefinieerd door migration files. Dit zijn bestanden in de app/database/migrations map.

Migrations worden uitgevoerd met het **artisan migrate** commando.

Het aanmaken van een nieuwe tabel bestaat uit de volgende stappen:

- Maak met artisan een migration bestand voor je tabel
- Definieer de kolommen in de up() function
- Voer de migration uit met artisan

Je kunt eenmaal uitgevoerde migrations ongedaan maken met arstisan **migrate:rollback**. Hieronder staan een paar van de meest gebruikte artisan migrate commando's:

|Commando|Beschrijving|
|---|---|
|php artisan make:migration create_students_table|Maak een nieuwe migratie, in dit voorbeeld voor de tabel met de naam 'students'. Je vindt het aangemaakte bestand terug in de map database/migrations
|php artisan migrate|Voer alle openstaande migraties uit. Migraties die eerder al een keer zijn uitgevoerd worden niet opnieuw uitgevoerd.|
|php artisan migrate:fresh|Voer alle migraties uit. Ook de migraties die eerder al een keer zijn uitgevoerd worden opnieuw uitgevoerd.
|php artisan migrate:rollback|Maak de laatste migratie ongedaan. Je kunt rollback steeds opnieuw uitvoeren totdat alle migraties zijn teruggedraaid|
|php artisan migrate:reset|Maak alle uitgevoerde migraties ongedaan. De database wordt leeggemaakt.
|php artisan migrate:status|Je krijgt een overzicht van de status van de migraties.

Raadpleeg de <a href="https://laravel.com/docs/11.x/migrations">Laravel database documentatie</a> voor meer database en migrate commando's.


## Models, Views, Controllers
In Laravel werk je met het **MVC design pattern**, Model, View, Controller. Eerst even in het kort waar deze termen voor staan:

### Model
Een model is de 'brug' naar een tabel in de database. Via het model in Laravel kan je veel database acties, zoals het toevoegen, wijzigen of verwijderen van records, eenvoudiger uitvoeren.

### View
Een view is een pagina in je applicatie waar de informatie uit een of meerdere tabellen getoond wordt. Views bestaand uit een mix van HTML code en Blade template code.

### Controller
De controller is de schakel tussen het Model en de View. Een controller bestaat vaak uit standaard functies waarmee je CRUD functionaliteit bouwt.

!!! note "CRUD"
    CRUD staat voor **Create**, **Read**, **Update** en **Delete**. Dit zijn de standaard acties die je nodig hebt om een tabel te bewerken.

Je kan met artisan een Resource Controller laten aanmaken die alle functies bevat die nodig zijn voor je CRUD:

```
php artisan make:controller StudentController --resource
```
Je krijgt nu een bestand met de functies index, create, store, show, edit, update, destroy. Je moet zelf nog de benodigde code in deze functies maken.  

### Artisan commando's voor MVC
Je kan met Artisan boiler plate code voor Models, Views en Controllers laten aanmaken. Hieronder staan een paar veelgebruikte artisan commando's die je hiervoor kan gebruiken.

|Commando|Beschrijving|Aangemaakte bestand(en)
|---|---|---|
|php artisan make:model Student|Maak een Model voor de tabel students|app/Models/Student.php
|php artisan make:model Student --seed|Maak een model voor de tabel students en een seeder|app/Models/Student.php<br>database/seeders/StudentSeeder.php
|php artisan make:controller StudentController|Maak een controller voor de tabel students|app/Http/Controllers/StudentController.php
|php artisan make:controller StudentController --resource|Maak een resource Controller voor de tabel students|app/Http/Controllers/StudentController.php
|php artisan make:model Student -mcr|Maak een Model, een Resource Controller en een Migration voor de tabel students|app/Models/Student.php<br>database/migrations/(..)_create_students_table.php<br>app/Http/Controllers/StudentController.php
|php artisan make:view student|Maak een View voor de tabel students|resources/views/student.blade.php
|php artisan make:model Student -mcrsf|Het meest complete commando. Creëert een Model, een Resource Controller, een Migration, een Seeder, en een Factory.<br><br>Voeg zelf nog de benodigde Views toe en je bent compleet.|app/Models/Student.php<br>database/factories/StudentFactory.php<br>database/migrations/(...)_create_students_table.php<br>database/seeders/StudentSeeder.php<br>app/Http/Controllers/StudentController.php 

## Laravel Naming Conventions
Laravel volgt de <a href="https://www.php-fig.org/psr/psr-12/">PSR-2/PSR-12 standaard</a>. Een set met coding style standaarden voor PHP.

Hieronder staan alvast enkele belangrijke regels die je kunt volgen.  

Models en Controllers worden met **PascalCase** geschreven, elk woord begint met een hoofdletter. Dus bijvoorbeeld **S**tudent**C**ontroller. 

Models en Controllers worden altijd in **enkelvoud** geschreven. Dus Student.php en **niet** Student**s**.php

Tabellen worden in **snake_case** geschreven en in het **meervoud**. Dus bijvoorbeeld **s**tudent_**g**rade**s**. 

Variabelen worden in **camelCase** geschreven. Dus bijvoorbeeld **s**tudent**G**rade = 10;

## Convention over Configuration
Hoe beter je de Laravel standaarden volgt, hoe beter Laravel je kan helpen met automatische configuratie en acties, dit wordt **convention over configuration** genoemd.

Twee voorbeelden van convention over configuration: 

Als je een Model maak met de naam **Student**, dan hoef je Laravel niet meer te vertellen dat de bijbehorende tabel **students** is. Laravel gaat ervan uit dat de tabel die bij een Model hoort geschreven is in de Engelse **meervoudsvorm** van het Model.<br>(*Deze convention werkt trouwens niet lekker als je Nederlandse namen voor tabellen gebruikt*.) 

Als je in een migration een kolom met de naam "**id**" toevoegt, dan gaat Laravel ervan uit dat dit de **primary key** van die tabel is.

## Primary Keys en Foreign Keys in Migrations

### Primary key
Als je de primary key "id" noemt dan zal Laravel in de tabel deze kolom als primary key met een auto-increment aanmaken:

```  title="(...)_create_students_table.php"
Schema::create('students', function (Blueprint $table) {
    $table->id(); // Er wordt automatisch een unsigned bigint met auto-increment aangemaakt
});
```

### Foreign Keys
Als je een foreign key aanmaakt met 'id' en de naam van de gerelateerde tabel ervoor, dan weet Laravel hoe deze relatie werkt.

```  title="(...)_create_lessons_table.php"
        Schema::create('lessons', function (Blueprint $table) {
            $table->id();
            $table->foreignId('student_id')->constrained();    // foreign key naar de tabel students
            $table->timestamps();
        });
```

De **->constrained()** zorgt ervoor dat in de tabel een constrained wordt aangemaakt. Dit zorgt ervoor dat je niet per ongeluk een student kan verwijderen als er nog een lesson met die student bestaat.

## Seeders en Factories
Om je applicatie goed te kunnen testen heb je testgegevens nodig. Laravel geeft de mogelijkheid om die testgegevens voor je te genereren. Hierbij gebruik je Seeders en Factories.

### Seeders
Met Seeders kan je snel een hoeveelheid testgegevens voor je applicatie genereren. Gebruik artisan om de boiler plate code voor een Seeder te genereren:

```
php artisan make:seeder StudentSeeder
```

### Factories
Met Factories kan je Nep gegevens laten genereren, zoals namen, datums, nummers etc. Hiervoor gebruik je de standaard meegeleverde package **Faker**.

Een Factory gebruik je vaak in combinatie met een Seeder.

Gebruik artisan om de boiler plate code voor een Factory te genereren:

```
php artisan make:factory StudentFactory
```

Voorbeeld van een eenvoudige Factory voor de tabel student:

``` title="StudentFactory.php"
class StudentFactory extends Factory
{
    public function definition(): array
    {
        return [
            'first_name' => fake()->firstName(),
            'last_name' => fake()->lastName(),
            'email' => fake()->unique()->safeEmail(),
            'studentnumber' => fake()->unique()->numberBetween(10000, 999999),
        ];
    }
}
```

### Seeder uitvoeren
Om een specifieke Seeder uit te voeren gebruik je onderstaand artisan commando. In het voorbeeld wordt de Seeder voor de tabel student uitgevoerd:

```
php artisan db:seed --class=StudentSeeder
```

Je kunt ook een reeks Seeders in een keer uitvoeren. Je voegt dan de benodigde Seeders toe in het bestand '**DatabaseSeeder.php**' en voert het onderstaande artisan commando uit:

```
php artisan db:seed
```

Voorbeeld van een DatabaseSeeder.php die 10 studenten aanmaakt:

``` title="DatabaseSeeder.php"
class DatabaseSeeder extends Seeder
{
    public function run(): void
    {
        Student::factory(10)->create();
    }
}
```

## Routes
Routes zijn url's in je applicatie waarmee de gebruiker naar de diverse beschikbare pagina's kan navigeren. Zonder een route naar een pagina is die pagina niet beschikbaar.

Routes worden gedefinieerd in het bestand **web.php**. Meestal wil je dat een route verwijst naar een functie in een Controller. Die functie gaat dan de benodigde acties uitvoeren om de pagina met de juiste gegevens te laten zien.

Hieronder staat een voorbeeld van een route naar de index functie van de StudentController:

``` title="web.php"
Route::get('/students', [App\Http\Controllers\StudentController::class, 'index']);
```

In plaats van voor iedere functie in een controller een aparte route te definieren, kan je ook een resource route gebruiken. Een resource route maakt achter de schermen in één keer routes voor alle functies van een resource controller:

``` title="web.php"
Route::resource('students', App\Http\Controllers\StudentController::class);
```

Deze route maakt achter de schermen routes voor de functies in je resource controller: index, create, store, show, edit, update en destroy


## Views
Views zijn de pagina's waarmee je de gebruiker de gegevens van je applicatie kan laten zien en laten bewerken.
Views bestaan uit een **combinatie** van **HTML** code en **Blade** template code.

Een View wordt aangeroepen vanuit een Controller en krijgt van de controller functie de gegevens mee om te laten zien of te laten bewerken.

Views worden opgeslagen in de **resource/views** folder. Het is gebruikelijk om voor elke tabel waarvoor je Views wilt maken een subdirectory te maken. De Views voor de tabel students staat dan in de folder resources/views/student

Hieronder staat een voorbeeld van de index function uit StudentController:

``` linenums="1" title="StudentController.php"
public function index()
{
  $students = Student::all();
  return view('student.index', ['students' => $students]);
}
```
Op regel 3 worden alle studenten uit de database opgehaald. Hiervoor wordt het Model Student gebruikt.

Op regel 4 wordt de index View teruggegeven zodat die aan de gebruiker getoond kan worden. De view krijgt de opgehaalde studenten meegestuurd.

De volledige bestandsnaam van de index View is **index.blade.php**, maar je hoeft alleen maar 'index' te schrijven. En omdat de View in de subdirectory 'resources/views/student' staat schrijf je dus '**student.index**'

Je kan in plaats van **['students' => $students]** ook de handige functie compact() gebruiken. Het resultaat is hetzelfde:

``` linenums="1" title="StudentController.php"
public function index()
{
  $students = Student::all();
  return view('student.index', compact('students'));
}
```

En hier is dan de voorbeeld code voor de View 'index':

``` linenums="1" title="index.blade.php"
<table>
    <thead>
    <tr>
        <td>First Name</td>
        <td>Last Name</td>
    </tr>
    </thead>
    <tbody>
        @foreach($students as $student)
            <tr>
                <td>{{$student->first_name}}</td>
                <td>{{$student->last_name}}</td>
            </tr>
        @endforeach
    </tbody>
</table>
```

Het is een eenvoudige HTML Table. In de **body** van de table wordt **Blade template code** gebruikt om met een loop alle studenten te laten zien.

De studenten staan in de variabele **$students**. Dit is een array met studenten die door de controller functie is opgehaald en aan de view is doorgegeven.

Je kan de Blade template code herkennen aan het '**@**' teken dat altijd voor de instructie staat. In bovenstaand voorbeeld wordt de Blade functie **@foreach()** gebruikt om door de gegevens te lopen. De loop wordt afgesloten met een **@endforeach**. 

Op regel 11 en 12 zie je dat de **first_name** en **last_name** van de student in een **<td\>** wordt gezet. De dubbele krulhaken zijn Blade code om aan te geven dat we de inhoud van de variabelen willen laten zien.

