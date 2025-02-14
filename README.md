![dobbelsteen](dice.png)
# Roll The Dice - Opdracht Kennismakingsdag

## Doelstelling

Het aanpassen van een HTML-pagina met daarin CSS en Javascript code zodat deze weer naar behoren werkt.

## Opdracht

In deze opdracht begin je met een webpagina waar een dobbelsteen op wordt getoond. Deze dobbelsteen doet nog niets; het is de bedoeling dat je deze laat rollen door op de knop te drukken. Aan jou de taak om uit te zoeken hoe je dit voor elkaar krijgt.

## Benodigd Materiaal

- Een PC / Mac met een code-/teksteditor (Notepad++, Sublime, UltraEdit).
- Een webbrowser (Chrome, Firefox, Edge).
- Het internet (om dingen op te zoeken).
- Het stappenplan.

## Bestandenstructuur

De benodigde bestanden kun je terugvinden op de USB-stick of op je computer. Het is verstandig om de inhoud van de USB-stick ergens op je harde schijf te kopiëren.

```
│   dice.html
└───[Images]
        1.jpg
        2.jpg
        3.jpg
        4.jpg
        5.jpg
        6.jpg
        round_dice_1.png
        round_dice_2.png
        round_dice_3.png
        round_dice_4.png
        round_dice_5.png
        round_dice_6.png
```

## Werking van het HTML-bestand

Het bestand `dice.html` bevat HTML in combinatie met CSS en Javascript. Je kunt dit bestand openen in een webbrowser om te zien hoe het eruitziet. De broncode kan bekeken worden met een teksteditor zoals Notepad++.

### Belangrijke Code Secties

- **CSS-code**: Staat tussen `<style> ... </style>`-tags.
- **HTML-code**: Staat tussen `<body> ... </body>`-tags.
- **Javascript-code**: Staat tussen `<script> ... </script>`-tags.

De HTML-code bepaalt de structuur van de pagina, de CSS-code zorgt voor de styling en de Javascript-code bevat de logica, zoals het stoppen van de dobbelsteen en de keuze van het nummer.

## Level 1 - Opdrachten

### Stap 1: Correcte afbeeldingen toevoegen

Op dit moment worden groene, ronde afbeeldingen weergegeven op de zijden van de dobbelsteen. Dit moet aangepast worden naar normale dobbelsteenafbeeldingen.

![6 dices](dice6.png)

- Zoek in de CSS-code waar de dobbelsteenafbeeldingen worden ingesteld.
- Vervang de groene ronde afbeeldingen met de juiste afbeeldingen uit de `Images`-map.

### Stap 2: Knop laten werken

Momenteel doet de knop niets. Voeg een `onclick`-attribuut toe aan de HTML-knop:

```html
onclick="alert('Werp de steen');"
```
Je ziet nu een melding verschijnen:
![alert](alert.png)

Na het testen vervang je de `alert()` door een verwijzing naar de `StopDice()` functie.

```html
onclick="StopDice();"
```

Je kunt testen of het werkt door het HTML-bestand opnieuw te laden en op de knop te drukken.

### Stap 3: Willekeurig getal genereren

De functie `getRandomNr()` genereert een willekeurig getal tussen 1 en 6:

```js
function getRandomNr() {
   let r = Math.floor((Math.random() * 6) + 1);  
   return r;
}
```

Gebruik deze functie in plaats van de vaste waarde in `StopDice()`, zodat de dobbelsteen een willekeurig nummer toont bij elke worp:

```html
onclick="StopDice(getRandomNr());"
```

## Level 2 - Opdrachten

### Stap 4: Tweede dobbelsteen toevoegen

- Kopieer het `<div>`-element van de eerste dobbelsteen en plak het eronder.
- Zorg ervoor dat de tweede dobbelsteen een uniek `id` krijgt, bijvoorbeeld `cube2`.
- In CSS moet je `#cube1` en `#cube2` afzonderlijk stijlen en ze uit elkaar zetten met de `left`-eigenschap.

```css
#cube1 { left: -100px; }
#cube2 { left: 100px; }
```

### Stap 5: Beide dobbelstenen laten werken

Pas de functie `StopDice()` aan zodat deze voor beide dobbelstenen werkt:

```js
function StopDice(a, b) {
   let ec1 = document.getElementById("cube1");
   let ec2 = document.getElementById("cube2");

   ec1.classList.remove("stopanim");
   ec1.classList.add("simpleanim");
   ec2.classList.remove("stopanim");
   ec2.classList.add("simpleanim");

   setTimeout(function(){ 
      ec1.classList.remove("simpleanim");
      ec1.classList.add("stopanim");
      ec1.style.setProperty("--spinnr","spin" + a);
      
      ec2.classList.remove("simpleanim");
      ec2.classList.add("stopanim");
      ec2.style.setProperty("--spinnr","spin" + b);
   }, 500);
}
```

De knop moet nu beide dobbelstenen laten rollen:

```html
onclick="StopDice(getRandomNr(), getRandomNr());"
```

## Eindresultaat

Als alles correct is geïmplementeerd:

- Worden de juiste afbeeldingen getoond.
- Reageert de knop op een klik.
- Stoppen beide dobbelstenen op een willekeurig getal.

Veel succes met het maken van deze opdracht!
