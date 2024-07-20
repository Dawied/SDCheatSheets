<div class="sdcs-header" markdown>
  ![](assets/images/PHP-logo.png)
</div>

# PHP Cheat Sheet

## PHP
PHP is een scripttaal die gebruikt wordt om dynamische website te bouwen. Vroeger stond de afkorting voor "Personal Home Page", tegenwoordig voor "PHP Hypertext Preprocessor". PHP bestaat sinds 1994 en wordt sindsdien actief doorontwikkeld.

## Bronnen
Buiten deze Cheat Sheet om zijn hier nog een paar interessante sites met informatie over PHP

|Site|Beschrijving|
|---|---|
|<a href="https://www.w3schools.com/php/default.asp">w3schools PHP Tutorial</a>|Veel voorbeelden en een mooie tryit editor om code uit te proberen.|
|<a href="https://www.codecademy.com/resources/docs/php">Codecademy</a>|Alles over PHP ingedeeld in categoriën. Begrijpelijke taal|
|<a href="https://www.php.net/manual/en/index.php">Officiële PHP documentie</a>|Technisch maar compleet. Vaak met voorbeelden van gebruikers|
|<a href="https://phptherightway.com/">PHP The Right Way</a>|Compleet, maar nogal technisch. Uitgebreide voorbeeldcode|

Als je voorbeeld code uit deze cheat sheet snel wilt uitproberen gebruik dan de <a href="https://www.w3schools.com/php/phptryit.asp?filename=tryphp_intro">TryIt editor van W3Schools</a>.


## Variabelen
Een variabele is een stukje geheugen in je programma met een naam. 

In dat stukje geheugen kan je een waarde opslaan. Je kan tekst opslaan maar ook getallen en datums. 

In php herken je een variabele omdat er altijd het dollarteken “$” voor staat. Bijvoorbeeld: $variabele1, $variabele2, $auto_merk, etc.

Je geeft een variabele een waarde door er het “=” teken achter te zetten gevolgd door een waarde:

```
$var1 = "Mercedes";
<p>
$var2 = 100000;
   </td>
  </tr>
</table>
```

## Arrays
Arrays zijn variabelen waar meerdere waarden in kunnen worden opgeslagen. Je kan een array vergelijken met een ladekast. In elk laatje kan je iets stoppen, een waarde. De laatjes hebben nummers die beginnen bij 0:

In PHP maak je een array op de volgende manier:

```
$cars = array("Volvo", "BMW", "Toyota");
```

Nu heb je een array met de naam $cars. Er zitten drie elementen in. Op plek 0 zit “Volvo”, op plek 1 zit “BMW” en op plek 2 zit “Toyota”.

Als je iets uit de array wilt halen gebruik je de blokhaken met de index van het element dat je nodig hebt:

```
$myCar = $cars[2];
echo $myCar;
```

### Associative arrays
Elk element in een standaard array heeft een index. Die index begint bij 0. 

Je hebt behalve de standaard arrays in PHP ook de beschikking over een **associative array**. Bij een associative array kan je een eigen **key** als index opgeven.

```
$studenten = array(1010001 => "Jelle van Eijk", 1010002 => "Els ten Brugge", 1010003 => "Mark Hoogland");
echo $studenten[1010002];
```

De key in een associative array kan een nummer of een string zijn.


## Loops
PHP heeft drie verschillende soorten loops. Hieronder staan voorbeelden van alledrie. 

### while loop
```
$cars = array("Volvo", "BMW", "Toyota");
$i = 0;

while ($i < count($cars)) {
    echo $cars[$i] . "<br>";
    $i++;
}
```

### for loop
```
$cars = array("Volvo", "BMW", "Toyota");

for ($i = 0; $i < count($cars); $i++) {
    echo $cars[$i] . "<br>";
}
```

### foreach loop (meest gebruikt voor arrays)
De foreach loop heeft twee vormen, de eerste gebruikt alleen de waarden in de array, de tweede vorm haalt ook de keys op

=== "Alleen waarden"
    ```
    $cars = array("Volvo", "BMW", "Toyota");

    foreach ($cars as $car) {
        echo $car . "<br>";
    }
    ```
=== "Waarden en Keys"
    ```
    $cars = array("Volvo", "BMW", "Toyota");

    foreach ($cars as $key => $car) {
        echo "$key: $car" . "<br>";
    }
    ```

## if-elseif-else
```
$uur = 14;
if ($uur <= 12) {
   $dagdeel = "ochtend";
} elseif ($uur > 12 && $uur < 18) {
   $dagdeel = "middag";
} else {
   $dagdeel = "avond";
}
echo $dagdeel;
```

## De ternary operator (?)
Met de ternary operator "?" kan je op één regel een volledig if-else statement schrijven.

**Een gewone if-else:**
```php
$naam = "Wim";
if ($naam == "Wim") {
  $isWim = true;
} else {
  $isWim = false;
}
```

**Dezelfde if-else maar nu met de ternary operator:**

```
$isWim = ($naam == "Wim") ? true : false;
```

## Samenvoegen van tekst (.)
Aan elkaar plakken van stukjes tekst doe je met de punt ".".
```
$error = "fout bij verwerken van het form";
$melding = "fout: " . $error;
echo $melding;
```

Je kan dit ook nog op een andere (betere) manier doen:
```
$error = "fout bij verwerken van het form";
$melding = "fout: $error";
echo $melding;
```
*De laatste manier kan je alleen gebruiken met string tussen dubbele aanhalingstekens!*

Welke manier je gebruikt hangt af van de situatie en je kiest elke keer de meest geschikte methode, met de voorkeur voor de laatste manier.

## functies
Functies zijn blokjes code. Je kan functies gebruiken om je code overzichtelijk te maken en ook om dezelfde code maar 1x te schrijven.

Je kan gegevens aan functies meegeven. Dat noemen we **parameters**. De parameters staan tussen de haakjes achter de functienaam. Als je meer parameters nodig hebt zet je een komma tussen elke parameter.

Een functie kan ook een waarde **teruggeven**. Dit doe je met 'return'. De waarde die wordt teruggegeven noemen we de **return value**.
```
echo dagdeel(14);

function dagdeel($uur) {
    if ($uur <= 12) {
        $dagdeel = "ochtend";
    } elseif ($uur > 12 && $uur < 18) {
        $dagdeel = "middag";
    } else {
        $dagdeel = "avond";
    }
    return $dagdeel;
}
```
In dit voorbeeld is $uur een parameter en de functie geeft de waarde van de variabele $dagdeel terug.

## Forms en inputs <form\></form\>
Een voorbeeld van een eenvoudig form met bijbehorende php bestand om de input te verwerken.

``` py title="index.html"
<form action="process.php" method="POST">
  <input type="text" name="voornaam">
  <input type="text" name="achternaam">

  <input type="submit" value="Versturen">
</form>
```

```py title="process.php"
<?php

$voornaam = empty($_POST["voornaam"]) ? "onbekend" : $_POST["voornaam"];
$achternaam = empty($_POST["achternaam"]) ? "onbekend" : $_POST["achternaam"];

echo "Voornaam: " . $voornaam . "<br>"
echo "Achternaam: " . $achternaam;
```


## Naar een andere pagina gaan (redirect)
Je kan vanuit een PHP programma de gebruiker naar een andere pagina sturen met een redirect:
```
header("Location: index.php");
```

## Fouten in code afvangen
Je kan in PHP stukjes code tegen fouten beschermen met try - catch

```
try {
   // code om uit te voeren
} catch (Exception $e) {
   // hier wordt een eventuele fout afgevangen
}
```

## Code invoegen (include)
Je kan een ander PHP bestand invoegen met include

```
<?php 
   include("dbcode.php"); // de code in dbcode.php wordt ingevoegd

   // overige code
```
