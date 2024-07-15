<div class="sdcs-header">
  <img src="/assets/images/PHPMySQL-logo.png">
</div>

# PHP en MySQL Cheat Sheet

## Database aanmaken

Een database met de naam "mijndatabase" aanmaken:

```
CREATE DATABASE mijndatabase;
```

## Database selecteren om te gebruiken

Een database met de naam "mijndatabase" selecteren om daarna te kunnen gebruiken:

```
USE mijndatabase;
```

## Tabel aanmaken

Om de tabel "voorbeeld" te maken met de kolommen kolom1, kolom2 en kolom3, voer je het onderstaande SQL statement uit:
```
CREATE TABLE voorbeeld
(
  kolom1 VARCHAR(10),
  kolom2 TEXT,
  kolom3 DATETIME
);

```
* Het datatype van kolom1 is VARCHAR(10), tekst van maximaal 10 karakters
* Het datatype van kolom2 is TEXT, tekst van onbeperkte lengte
* Het datatype van kolom3 is DATETIME, een datum en tijd

## Gegevens uit een tabel selecteren

Om gegevens uit de tabel "voorbeeld" te selecteren, voer je het onderstaande SQL statement uit:
```
SELECT * FROM voorbeeld;
```

## Gegevens invoeren in een tabel

Om gegevens in de tabel "voorbeeld" in te voeren, voer je het onderstaande SQL statement uit:
```
INSERT INTO voorbeeld (kolom1, kolom2, kolom3) 
VALUES("tekst1", "tekst2", "01-01-2019");
```

## Een script uitvoeren op mysql

Stel je hebt een script met de naam create_db.sql. In dit script staat een SQL statement om een tabel aan te maken. Je kan nu het script op mysql uitvoeren door op de command prompt het volgende commando te geven:
```
mysql -u [username] -p [password] < create_db.sql
```

## Met PHP een verbinding maken met de database

Stel je hebt een database met de naam "school", de gebruiker van de database is "root" en het wachtwoord is ook "geheim123". Dan maak je een verbinding met deze database met de onderstaande code:

```
$host = 'localhost';
$dbname = 'school';
$username = 'root';
$password = 'geheim123';

$connectStr = 'mysql:host=' . $host . ';dbname=' . $dbname . ';charset=utf8';
$db = new PDO($connectStr, $username, $password);
// Om fouten af te vangen met try-catch, het onderstaande toevoegen
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);        
```

## Met PHP code een record toevoegen aan een tabel

Stel je hebt een tabel met de naam 'student' en je wilt hier een record aan toevoegen met de twee kolommen 'naam', 'jaar':

```
$sql = "INSERT INTO student (naam, jaar) VALUES (:naam, :jaar)";
$params = array(":naam" => "Jan", ":jaar" => "2019");

$sth = $db->prepare($sql);
$sth->execute($params);
```

## Met PHP de records uit een tabel ophalen

Stel je hebt de tabel 'student' en je wilt met PHP alle records (rijen) uit deze tabel ophalen en de gegevens met een echo weergeven:

```
$sql = "SELECT * FROM student";
$sth = $db->prepare($sql);
$sth->execute();

while($row = $sth->fetch()) {
    $naam = $row["naam"];
    $jaar = $row["jaar"];
    echo "Naam student: $naam Leerjaar: $jaar";
}
```

## Controleren of alle gewenste input aanwezig is in de $_POST array

Als je tijdens het testen wilt weten welke gegevens in de de $_POST array terecht zijn gekomen kan je met de functie print_r() alle elementen van de $_POST array tonen:

```
$voornaam = empty($_POST["voornaam"]) ? "onbekend" : $_POST["voornaam"];
$achternaam = empty($_POST["achternaam"]) ? "onbekend" : $_POST["achternaam"];

// Laten zien welke gegevens in de $_POST zitten
echo print_r($_POST);
```

## Fouten afvangen met try - catch

Met try - catch kan je fouten bij het uitvoeren van de code netjes afvangen. Ze de code om uit te voeren tussen het code block na de try en vang eventuele fouten af tussen het code block na de catch:

```
$sql = "INSERT INTO student (naam, jaar) VALUES (:naam, :jaar)";
$params = array(":naam" => "Jan", ":jaar" => "2019");

try {
  // Dit stukje code wil je beschermen tegen een fout
  $sth = $db->prepare($sql);
  $sth->execute($params);
} catch (PDOException $e) {
  // In de catch wordt de fout afgevangen en kan je iets met de foutmelding
  // doen, bijvoorbeeld tonen of loggen
  echo $e->getMessage();
}

```
Let op! Om een PDO exception (fouten bij het uitvoeren van database commandos's) af te vangen moet je het volgende toevoegen na het maken van de database connectie:

```
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

## Input veilig verwerken

Input van een formulier moet je veilig verwerken. Zeker als je de input ook weer laat zien met een echo moet je ervoor zorgen dat er geen Cross Site Scripting (XSS) gebruikt kan worden door een hacker. Dit doe je met de htmlspecialchars() functie :
```
$voornaam = empty($_POST["voornaam"]) ? "onbekend" : $_POST["voornaam"];
$achternaam = empty($_POST["achternaam"]) ? "onbekend" : $_POST["achternaam"];

// Dit is NIET veilig
echo $voornaam . " " . $achternaam

// Zo wordt het veilig
$voornaam = htmlspecialchars($voornaam);
$achternaam = htmlspecialchars($achternaam);
echo $voornaam . " " . $achternaam;
```

## Tablerows in een php loop maken

Als je records uit een SELECT wilt afdrukken in een tabel gebruik je voor de tablerows de onderstaande code. 
```
<?php while($row = $sth->fetch()) { ?>
    <tr>
        <td><?php echo $row["voornaam"]; ?></td>
        <td><?php echo $row["achternaam"]; ?></td>
    </tr>
<?php } ?>
```

## ID meegeven in een link

Als je een id van een record wilt meegeven als parameter in een url gebruik je onderstaande code. Het id komt uiteindelijk in de $_GET array van PHP
```
<a href="update-student-form.php?id=<?php echo $row["id"]?>"
```

## Met PHP een UPDATE statement maken

Stel je wilt de tabel student updaten. Je wilt de kolommen **voornaam** en **achternaam** wijzigen van een student met een bepaalde id als primary key:
```
// Maak eerst het sql update statement in een string
$sql = "UPDATE student 
   SET voornaam = :voornaam, achternaam = :achternaam
   WHERE id = :id";

// Vul een array met waarden voor de placeholders
$params = array(
    ":id" => $id,
    ":voornaam" => $voornaam,
    ":achternaam" => $achternaam
);

// Voer het statement uit op de database
$sth = $db->prepare($sql);
$sth->execute($params);
```

## Met PHP een specifiek record selecteren

Om een specifiek record te selecteren moet je in je SELECT statement een **WHERE** gebruiken. Stel je wilt een student selecteren met een specifieke id:
```
// Maak het sql select statement als string
$sql = "SELECT * FROM student WHERE id=:id";

// Maak een array met de waarden bij de placeholder
$params = array(
    ":id" => $id
);

// Voer uit op de database
// De gegevens van de student komen in de array $student
$sth = $db->prepare($sql);
$sth->execute($params);
$student = $sth->fetch();
```

## Met PHP een specifiek record verwijderen uit een tabel

Om een specifiek record te vewijderen uit een tabel gebruik je een **DELETE** statement in combinatie met een WHERE. Stel je wilt uit de tabel student een record met een specifiek id verwijderen:
```

// Maak het sql delete statement als string
$sql = "DELETE FROM student WHERE id=:id";

// Maak een array met de waarden bij de placeholder
$params = array(
    ":id" => $id
);

// Voer uit op de database
$sth = $db->prepare($sql);
$sth->execute($params);

```