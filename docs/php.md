<div class="sdcs-header" markdown>
  ![](assets/images/PHP-logo.png)
</div>

# PHP Cheat Sheet


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


## De ternary operator (?)


<table>
  <tr>
   <td>
<h3>Gewone if-else:</h3>

<code>$naam = "Wim";</code>
<p>
<code>if ($naam == "Wim") {</code>
<p>
<code>    $isWim = true;</code>
<p>
<code>} else {</code>
<p>
<code>    $isWim = false;</code>
<p>
<code>}</code>
   </td>
   <td>
<h3>Herschreven met ternary operator:</h3>

<code>$isWim = ($naam == "Wim") ? true : false;</code>
<h3>Nog korter:</h3>


<p>
<code>$isWim = ($naam == "Wim");</code>
   </td>
  </tr>
</table>



## Forms en inputs &lt;form>&lt;/form>


<table>
  <tr>
   <td><strong>index.html</strong>
<p>
<code>&lt;form action="process.php" method="post"></code>
<p>
<code>    &lt;input type="text" name="voornaam"></code>
<p>
<code>    &lt;input type="text" name="achternaam"></code>
<p>
<code>    &lt;input type="submit" value="Versturen"></code>
<p>
<code>&lt;/form></code>
   </td>
  </tr>
  <tr>
   <td><strong>process.php</strong>
<p>
<code>&lt;?php</code>
<p>
<code>$voornaam = empty($_POST["voornaam"]) ? "onbekend" : $_POST["voornaam"];</code>
<p>
<code>$achternaam = empty($_POST["achternaam"]) ? "onbekend" : $_POST["achternaam"];</code>
<p>
<code>echo "Voornaam: " . $voornaam . "&lt;br>"</code>
<p>
<code>echo "Achternaam: " . $achternaam;</code>
   </td>
  </tr>
</table>


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


## functies

Functies zijn blokjes code. Je kan functies gebruiken om dezelfde code maar 1x te schrijven en daarna vanuit andere code te gebruiken, 'aan te roepen'.

Je kan gegevens aan functies meegeven. Dat noemen we parameters. De parameters staan tussen de haakjes achter de functienaam. Als je meer parameters nodig hebt zet je een komma tussen elke parameter.

Een functie kan ook een waarde teruggeven. Dit doe je met 'return'.
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



## Samenvoegen van tekst (.)
Aan elkaar plakken van stukjes tekst doe je met de punt ".".
```
$error = "fout bij verwerken van het form";
$melding = "fout: " . $error;
echo $melding;
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
