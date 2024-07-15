<div class="sdcs-header">
  <img src="/assets/images/Tux.png">
</div>

# Linux Cheat Sheet

Een Cheat Sheet met veelgebruikte commando's en tools in Linux

Klik op de 'explainshell' links om uitvoerige informatie te krijgen over een commando

## Packages installeren en beheren met apt
De Advanced Package Tool, apt, bestaat uit een aantal tools waarmee je in Debian en Ubuntu packages/programma's kan installeren. Andere Linux distributies kunnen andere tools gebruiken. Vaak zie je nog tutorials waarin apt-get wordt gebruikt in plaats van apt. apt is de nieuwe versie van apt-get.

### Package database updaten
```
apt update
```
Hiermee haal je informatie op over de nieuwste versies van programma's

### Nieuwe versie van package installeren
```
apt upgrade
```
Hiermee installeer je de nieuwste versies van programma's. Doe altijd eerst een apt-get update en daarna een apt-get upgrade

### Nieuwe versie van Linux installeren
```
apt dist-upgrade
```
Hiermee installeer je de nieuwste versies van de distributie.

### Een package installeren
```
apt install <package-name>
```
Met apt-get install installeer je een programma. Bijvoorbeeld de Midnight Commander:

### Een package verwijderen
```
apt remove <package-name>
```
Verwijder de binaries van de package, maar niet de configuratie bestanden

### Een package verwijderen en opschonen
```
apt purge <package-name>
```
Verwijder de binaries van de package en ook de bijbehorende configuratie bestanden


## ls (list)

Het list commando ls geeft een lijst van de files in een directory. 

```
ls
```

Met verschillende switches/opties kan de lijst in allerlei formaten worden getoond. De switch -a toont bijvoorbeeld alle bestanden, ook de verborgen.

```
ls -a 
```

De switch -l geeft meer informatie over de bestanden, zoals eigenaar, rechten, datum tijd

```
ls -l
```

Door ls te pipen naar andere commando’s en tools kan je nog meer met de lijst doen:

### Tel het aantal bestanden in een directory

```
ls | wc -l
```
[explainshell](https://explainshell.com/explain?cmd=ls+%7C+wc+-lwc+-l)

### Toon de 10 nieuwste bestanden in een directory

```
ls -lt | head -10
```
[explainshell](https://explainshell.com/explain?cmd=ls -lt | head -10)

### Toon de 10 oudste bestanden in een directory

```
ls -ltr | head -10
```
[explainshell](https://explainshell.com/explain?cmd=ls -ltr | head -10)

## df (disk free)
Het commando df, disk free, geeft een overzicht van disks en de gebruikte en vrije ruimte. 
df kijk naar de gebruikte blocks op de disks. Met de switch -h toon je de grootte in MB en GB

```
df -h
```

## du (disk usage)
Het commando du, disk usage, doorloopt de bestanden in een directory en toont de grootte van de bestanden. du telt geen hardlinks en geen bestanden waar je geen rechten voor voor hebt.

Met de switch --max-depth kan je aangeven hoe diep je in de directory boom wilt zoeken. max-depth=1 zoekt alleen in de hoofd directory

```
du -h --max-depth=1
```
[explainshell](https://explainshell.com/explain?cmd=du -h --max-depth=1)

## cat (concatenate)
Met het commando cat kan je de inhoud van bestanden tonen in de console. 

```
cat info.txt
```
toont de inhoud van het bestand info.txt op het scherm

```
cat /proc/meminfo
```
Toont het interne geheugengebruik

## man (manual)
Het commando man geeft informatie over een commando
```
man cat
```
Geeft uitgebreide informatie over het commando cat

## grep (zoeken naar tekst in een bestand)
Met grep kan je zoeken naar tekst in bestanden. Het command print de regels waarin het gezochte woord voorkomt naar de console

```
grep 'minecraft' index.html
```
Zoekt naar het woord minecraft in het bestand index.html

## history
Met de pijltjes up en down krijg je de commando’s die je eerder hebt uitgevoerd in de shell terug.

Met het commando history vraag je alle eerder uitgevoerde commando’s op. Je krijgt een lijst met alle commando’s die in de history zijn opgeslagen.

Door grep te gebruiken op de output van history kan je eenvoudig zoeken naar een commando dat je eerder hebt uitgevoerd.

Let op, gevoelige informatie zoals wachtwoorden wordt ook in de history opgeslagen. Daarom is het een goed gebruik om nooit wachtwoorden in commando’s mee te geven. Als je toch gevoelige informatie in de history hebt staan kan je die beter weer verwijderen voordat je de shell verlaat.

### Toon de history met de regel nummers
```
history
```

### Zoek naar een eerder uitgevoerd commando in history
```
history | grep cat
```
Zoekt in de history naar commando's waarin het woord 'cat' voorkomt

### Verwijder een regel uit history
```
history -d <regelnum>
```

### Verwijder alles uit history
```
history -c
```

### Voer een regel uit de history opnieuw uit
```
!<regelnum>
```

## Processen

### Toon een lijst met processen met een bepaalde naam
```bash
ps -e | grep <name>
```

### Toon geheugen gebruik per process
```bash
ps -eo size,pid,user,command --sort -size | awk '{ hr=$1/1024 ; printf("%13.2f Mb ",hr) } { for ( x=4 ; x<=NF ; x++ ) { printf("%s ",$x) } print "" }' |cut -d "" -f2 | cut -d "-" -f1
```

## Achtergrond taken
Als je meerdere taken tegelijkertijd wilt uitvoeren in de terminal heb je een aantal opties. De eerste optie is gewoon een nieuwe terminal sessie openen. Maar wat als je even snel iets anders wilt doen terwijl je bijvoorbeeld een bestand aan het editen bent? Dan gebruik je Ctrl+z en fg:

```
Ctrl+z
```
Stuurt het huidige programma (bijvoorbeel een editor) tijdelijk naar de achtergrond.

```
fg
```
Type 'fg' als je klaar bent om het programma weer naar de voorgrond te brengen

## Achtergrond taken met 'screen'
Een andere manier om programma’s in de background uit te voeren is screen. Het voordeel van screen is dat programma’s die in een screen sessie zijn gestart ook beschikbaar blijven als je de terminal sluit. Je kan altijd weer terug naar je screen sessies. Handig als je een langdurig proces wilt starten, maar niet de hele tijd de terminal open wilt houden.

Screen is geen standaard package en moet je meestal wel nog installeren: **apt-get install screen**

### create new screen
```
Ctrl+a+c
```
### detatch from screen
```
Ctrl+a+d
```
### reatach to screen
```
screen -r
```
### switch to next screen
```
Ctrl+a+n
```
### switch to previous screen
```
Ctrl+a+p
```
### exit screen
```
exit
```