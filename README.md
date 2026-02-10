# 100-Dagen Workshop

Een hands-on webontwikkeling workshop waarin leerlingen een "100 dagen" website bouwen met **Tailwind CSS v4** en **jQuery**.

## Leerdoelen

Op het einde van deze workshop kan je:

- Tailwind CSS via CDN gebruiken om een website te stylen zonder zelf CSS te schrijven
- Utility classes toepassen voor layout (flexbox), typografie, kleuren, gradienten en achtergrondafbeeldingen
- Werken met lineaire en radiale gradienten via Tailwind's gradient-utilities
- Externe content (zoals Google Maps) toevoegen via iframes
- Media (audio en video) koppelen aan een webpagina met JavaScript
- Scroll-gebaseerde events in jQuery begrijpen

## Vereisten

- [Visual Studio Code](https://code.visualstudio.com/) of een andere code-editor
  - Indien je Visual Studio Code gebruikt, installeer de [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extensie voor een betere ontwikkelervaring
- Een moderne webbrowser (Chrome, Firefox of Edge)
- Basiskennis van HTML & CSS
- Basiskennis van JavaScript

## Projectstructuur

```plaintext
├── Start 2025/          # Startbestanden (werk hierin!)
│   ├── index.html       # Het HTML-bestand met TODO's om te voltooien
│   ├── img/             # Afbeeldingen voor de website
│   ├── audio/           # Audiobestanden
│   ├── video/           # Videobestanden
│   └── js/              # JavaScript-bibliotheken voor scroll-animaties
│
├── Solution 2025/       # Voltooide oplossing (ter referentie)
│   └── ...              # Zelfde structuur met alle TODO's opgelost
```

## Aan de slag

1. Open de map `Start 2025/` in je code-editor
2. Open `Start 2025/index.html` in je browser of start een Live Server sessie (via de "Go Live" knop rechtsonder in VS Code)
3. Volg onderstaande stappen — elke stap komt overeen met een `TODO`-commentaar in de code
4. Ververs je browser na elke wijziging om het resultaat te zien

> **Tip:** Gebruik de Developer Tools van je browser (F12) om elementen te inspecteren en problemen op te sporen.

---

## Workshop

### Stap 1: Tailwind CSS CDN toevoegen

**Locatie:** `<head>` sectie, na de Google Fonts links

Zoek het TODO-commentaar over het toevoegen van Tailwind CSS en voeg het CDN-script eronder toe:

```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

Ververs hierna de pagina. Je zal merken dat de standaard browserstijlen verdwijnen - dat zijn de basisstijlen van Tailwind die nu actief zijn.

Kijk eens naar de `class` attributen in de HTML — je kan al heel wat Tailwind utility classes zien, die hebben wij voorzien als startpunt. We zullen onze pagina stap voor stap uitbreiden met extra Tailwind utility classes!

---

### Stap 2: Een websitetitel toevoegen

**Locatie:** `<title>` tag in de `<head>` sectie

Zoek de TODO over de titel en voeg toe:

```html
<title>100-dagen website</title>
```

Kijk naar je browsertabblad — daar zou nu de titel moeten staan.

---

### Stap 3: Een standaard lettertype instellen voor de pagina

**Locatie:** `<body>` tag

Voeg de `font-[Bokor]` class toe aan het body-element zodat de hele pagina het Bokor-lettertype gebruikt (automatisch ingeladen via [Google Fonts](https://fonts.google.com/)):

```html
<body class="flex flex-col font-[Bokor]"></body>
```

> **Hoe werkt dit?** [Tailwind's arbitrary value-syntax](https://tailwindcss.com/docs/adding-custom-styles#using-arbitrary-values) kan je gebruiken om zelf gekozen waarden in te vullen voor bestaande utility classes. In dit geval gebruiken we `font-[]` om een Google Font toe te passen die niet standaard in Tailwind zit.

---

### Stap 4: De secondenteller starten

**Locatie:** Binnen de `$(document).ready()` functie in de `<script>` tag

Zoek de TODO over het tellen van seconden. Voeg deze regel toe om de live teller te starten:

```javascript
setTimeout(() => countSecondsSinceBirth(), 1000);
```

De `countSecondsSinceBirth()` functie is al hierboven gedefinieerd — deze berekent het aantal seconden sinds 2 september 2020 en werkt de pagina elke seconde bij.

---

### Stap 5: Zone 1 stylen (Scroll Down sectie)

**Locatie:** `<div id="zone1">`

Dit is de hero-sectie die de gebruiker als eerste ziet. Voeg deze classes toe aan de `zone1` div:

- Een horizontale gradient-achtergrond: `bg-linear-to-r from-red-300 to-amber-500`
- Inhoud centreren met flexbox: `flex flex-col items-center justify-center`
- Een marge onderaan: `mb-5`

Pas daarna de `<h1>` erin aan:

- Wijzig het lettertype: `font-[Indie_Flower]`
- Wijzig de tekstkleur: `text-lime-600`

**Resultaat:**

```html
<div
  id="zone1"
  class="block w-full h-screen flex flex-col items-center justify-center bg-linear-to-r from-red-300 to-amber-500 mb-5"
>
  <h1 class="font-[Indie_Flower] text-3xl text-lime-600 font-extrabold">
    Scroll zachtjes naar beneden
  </h1>
  <img src="img/navigate-down.png" alt="pijl naar beneden" />
</div>
```

> **Meer info:** [Tailwind CSS — Lineaire Gradienten](https://tailwindcss.com/docs/background-image#adding-a-linear-gradient)

---

### Stap 6: Zone 2 stylen (Schoolstart sectie)

**Locatie:** `<div id="zone2">`

Voeg deze classes toe aan de `zone2` div:

- Omgekeerde rij-layout met verticale centrering: `flex flex-row-reverse items-center`
- Een horizontale gradient-achtergrond: `bg-linear-to-r from-cyan-500 to-blue-500`

**Resultaat:**

```html
<div
  id="zone2"
  class="flex flex-row-reverse items-center bg-linear-to-r from-cyan-500 to-blue-500"
></div>
```

> **Wat doet `flex-row-reverse`?** Het plaatst de kinderen in een rij maar in omgekeerde volgorde — de afbeeldingen verschijnen links en de tekst rechts.

---

### Stap 7: Zone 3 stylen (100 Dagen sectie)

**Locatie:** `<div id="zone3">`

Voeg een radiale gradient-achtergrond toe aan de `zone3` div:

- `bg-radial from-yellow-300 from-0% to-yellow-500`

Pas vervolgens de **eerste `<h1>`** aan ("Nog 100 dagen"):

- Voeg lettertype toe: `font-[Impact]`
- Stel tekstkleur in: `text-white`
- Kleur de `<span>` met "100": `text-orange-500`

Pas de **tweede `<h1>`** aan ("En dat moeten we vieren!!!"):

- Voeg lettertype toe: `font-[Impact]`
- Stel tekstkleur in: `text-orange-500`

**Resultaat:**

```html
<div
  id="zone3"
  class="w-full h-screen bg-radial from-yellow-300 from-0% to-yellow-500"
>
  <h1 class="pt-10 font-[Impact] text-white text-6xl font-extrabold text-right">
    Nog <span class="special text-orange-500">100</span> dagen
  </h1>
  <h1
    class="vieren pt-28 font-[Impact] text-orange-500 text-6xl font-extrabold text-center"
  >
    En dat moeten<br />we vieren!!!
  </h1>
</div>
```

> **Meer info:** [Tailwind CSS — Radiale Gradienten](https://tailwindcss.com/docs/background-image#adding-a-radial-gradient)

---

### Stap 8: Een achtergrondafbeelding toevoegen aan zone 4

**Locatie:** `<div id="zone4">`

Stel een achtergrondafbeelding in op de `zone4` div met Tailwind's arbitrary value-syntax:

- `bg-[url('img/feest.jpg')]`

Geef ook het woord "feestje" in de `<span>` een kleur:

- `text-red-600`

**Resultaat:**

```html
<div
  id="zone4"
  class="flex justify-center items-start w-full h-screen bg-[url('img/feest.jpg')] bg-cover"
>
  <div class="w-2/5 bg-black opacity-70 p-12 text-white mt-24">
    <h1 class="text-3xl text-center mb-12">
      Wat dacht je van een <span class="text-red-600">feestje</span>?
    </h1>
    <h2 class="text-2xl text-center">
      breng je dansschoenen mee, en je goed humeur! :)
    </h2>
  </div>
</div>
```

> **Meer info:** [Tailwind CSS — Achtergrondafbeelding](https://tailwindcss.com/docs/background-image)

---

### Stap 9: Zone 5 stylen (Wanneer sectie)

**Locatie:** `<div id="zone5">`

Voeg een verticale gradient-achtergrond toe:

- `bg-linear-to-b from-red-500 to-orange-500`

**Resultaat:**

```html
<div
  id="zone5"
  class="w-full flex justify-between items-center p-16 text-white bg-linear-to-b from-red-500 to-orange-500"
></div>
```

---

### Stap 10: Zone 6 stylen (Waar sectie)

**Locatie:** `<div id="zone6">`

Voeg een verticale gradient-achtergrond toe:

- `bg-linear-to-b from-neutral-600 to-neutral-900`

Vervang vervolgens het TODO-commentaar over Google Maps door een ingebedde kaart. Gebruik een generator zoals [mapembed.org](https://www.mapembed.org/) om de embed-code te genereren voor het gewenste adres.

**Resultaat:**

```html
<div
  id="zone6"
  class="w-full py-20 px-10 text-white bg-linear-to-b from-neutral-600 to-neutral-900"
>
  <h1 class="text-6xl mb-10">Waar</h1>
  <h2 class="text-3xl mb-6">Arbeidstraat 14, 9300 Aalst</h2>

  <div id="maps" class="embed-map-responsive">
    <div class="embed-map-container">
      <iframe
        class="embed-map-frame"
        frameborder="0"
        scrolling="no"
        marginheight="0"
        marginwidth="0"
        src="https://maps.google.com/maps?width=600&height=400&hl=en&q=arbeidstraat%2014%2C%209300%20Aalst&t=&z=16&ie=UTF8&iwloc=B&output=embed"
      ></iframe>
    </div>
    <style>
      .embed-map-responsive {
        position: relative;
        text-align: right;
        width: 100%;
        height: 0;
        padding-bottom: 66.66%;
      }
      .embed-map-container {
        overflow: hidden;
        background: none !important;
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
      }
      .embed-map-frame {
        width: 100% !important;
        height: 100% !important;
        position: absolute;
        top: 0;
        left: 0;
      }
    </style>
  </div>
</div>
```

> **Let op:** Geef de buitenste `<div>` van je kaart het id `maps`, zodat de scroll-animaties deze kunnen aansturen.

---

### Stap 11: Het audiobestand toevoegen

**Locatie:** Binnen de zone4 scroll event handler in de `<script>` tag

Zoek de lege `audio.src = ""` regel en stel deze in op het feest-audiobestand:

```javascript
audio.src = "audio/feest.mp3";
```

Als je nu naar zone 4 scrollt, begint de feestmuziek te spelen!

---

### Stap 12: Het videobestand toevoegen

**Locatie:** `<video id="danceVideo">` element, in de `<source>` tag

Voeg het pad naar het videobestand toe:

```html
<source src="video/city.mp4" type="video/mp4" />
```

De video speelt automatisch af wanneer je naar de laatste sectie scrollt.

---

### Stap 13: Je website online zetten met GitHub Pages

Nu gaan we je website publiceren zodat iedereen deze kan bekijken!

1. **Maak een GitHub-account** aan op [github.com](https://github.com/signup) (sla dit over als je er al een hebt)
2. **Maak een nieuwe repository** aan met als naam exact je GitHub-gebruikersnaam gevolgd door `.github.io` (bijv. gebruikersnaam `janneke` → repository met naam `janneke.github.io`)
3. **Upload je bestanden** via de knop **"Add file" > "Upload files"** op de repository-pagina. Sleep je `index.html`, de `img/`, `audio/`, `video/` en `js/` mappen erin en klik op **"Commit changes"**
4. **Wacht even** — GitHub deployt automatisch je statische website
5. **Bezoek je website** op `https://JOUW-USERNAME.github.io` (in het voorbeeld van Janneke: `https://janneke.github.io`)

> **Let op:** De repository-naam moet exact `username.github.io` zijn (met je eigen gebruikersnaam), anders werkt de automatische deployment niet.

---

### Stap 14: Nu zelf aan de slag

Pas de website aan voor jouw feest, fuif, verjaardag, ... Voeg extra secties toe, pas de kleuren en lettertypen aan, voeg meer media toe, experimenteer met andere Tailwind utilities!

---

## Samenvatting van wat je hebt gebouwd

| Categorie        | Wat je hebt gedaan                                                                            |
| ---------------- | --------------------------------------------------------------------------------------------- |
| **Tailwind CSS** | CDN toegevoegd, utility classes gebruikt voor layout, typografie, gradienten en achtergronden |
| **Flexbox**      | Content gecentreerd, rijvolgorde omgekeerd, items uitgelijnd                                  |
| **Gradienten**   | Lineaire gradienten (horizontaal & verticaal) en een radiale gradient                         |
| **Lettertypen**  | Google Fonts (Bokor, Indie Flower, Impact) toegepast via arbitrary values                     |
| **Media**        | Een audiobestand en een videobestand gekoppeld                                                |
| **Embeddings**   | Een Google Maps iframe toegevoegd                                                             |
| **JavaScript**   | Een live secondenteller gestart met `setTimeout`                                              |

---

## Bonusopdracht

De startercode bevat een hint voor een extra oefening:

> _"Wat als je een website maakt die AFTELT naar een datum in de toekomst? Hoe zou je het script aanpassen?"_

Probeer de `countSecondsSinceBirth()` functie aan te passen zodat deze aftelt naar een datum in de toekomst in plaats van optelt vanaf het verleden!
