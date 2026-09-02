# Fase 2 — handmatig testen

Status: **te doen**.

Doel: controleren of poules, voorstel, kwaliteitsscore, indelingsregels, slepen, lock, splitsen/samenvoegen en bevestigen/annuleren kloppen. Wedstrijden, matplanning en live-regie horen **niet** bij deze ronde.

App: [https://donnersm.github.io/HajimeGo/](https://donnersm.github.io/HajimeGo/) (Chrome of Edge) of lokaal [http://localhost:8090](http://localhost:8090). Data zit in die browser op die URL; een andere browser of privévenster is een lege database.

Testdata: dezelfde Excel-bestanden als fase 1, in `docs/testdata/` (`JC-Noord.xlsx`, `JC-Zuid.xlsx`). Fictieve namen.

Tijd: ongeveer 20–30 minuten. Vink af wat klopt; noteer bij een fout wat je deed en wat je zag.

---

## Voorbereiding

- [ ] App open (testversie-URL of `cd app` → `flutter run -d chrome --web-port 8090`)
- [ ] Startscherm toont “Klaar voor de mat”
- [ ] Bestanden aanwezig: `JC-Noord.xlsx`, `JC-Zuid.xlsx`

---

## 1. Toernooi en deelnemers

1. Home → **Nieuw toernooi**.
2. Naam `Fase 2 test`, datum morgen, locatie `Sporthal Test`, organisator `JC Demo`, tatami `3`. Opslaan.
3. Open het toernooi → **Deelnemers** → Excel importeren → `JC-Noord.xlsx` → importeren.
4. Importeer daarna `JC-Zuid.xlsx` (dubbele namen overslaan **aan**).
   - [ ] **10 deelnemers** (6 Noord + 4 Zuid, Sem één keer)
5. Open **Kim de Wit**. Zet status op **Niet aanwezig**. Opslaan.
6. Voeg met de hand **Teun Los** toe: man, geboortejaar `2016`, **geen gewicht**, status Ingeschreven.
   - [ ] Teun staat in de lijst zonder kg

Verwacht na import (voor Kim’s statuswijziging):

| Naam | Kg | Band | Cat. | Jaar | G |
| --- | --- | --- | --- | --- | --- |
| Kim de Wit | 28 | geel | B | 2018 | V |
| Finn van der Burgt | 46 | blauw | C | 2013 | M |
| Jolien Cuenen | 25 | oranje | A | 2018 | V |
| Daan Bakker | 32 | groen | B | 2016 | M |
| Sara El Idrissi | 30 | geel | A | 2017 | V |
| Luca Vermeulen | 40 | bruin | C | 2012 | M |
| Sem de Groot | 27 | wit | A | 2019 | M |
| Noor Janssen | 29 | geel | B | 2018 | V |
| Yosef Karimi | 35 | oranje | B | 2015 | M |
| Lotte Hendriks | 24 | geel | A | 2018 | V |

---

## 2. Leeg poules-scherm en wie meedoet

1. Terug naar het toernooi → **Poules**.
   - [ ] Tekst dat er nog geen poules zijn
   - [ ] Kaart **Indelingsregels** met o.a. “mannen en vrouwen apart” en percentages
2. **Voorstel maken**.
   - [ ] Er ontstaan poules (dames en heren gescheiden)
   - [ ] Kim zit **niet** in een poule (Niet aanwezig) en **niet** in het rode kader Niet ingedeeld
   - [ ] Teun zit **niet** in een poule (geen gewicht) en staat onderaan in het rode kader **Niet ingedeeld** onder Gegevens ontbreken
   - [ ] Per poule: letters A…, namen, kg, band, niveau (A/B/C), club, kwaliteitsscore / 100 en breakdown (Gewicht, Leeftijd, Band, Categorie)
   - [ ] Poules waarvan een gewicht meer dan 10% van het poulegemiddelde afwijkt, hebben een oranje markering
   - [ ] De naam (en letter) van die judoka’s is rood; de anderen in de poule blijven zwart

Met Kim en Teun buiten: 4 dames + 5 heren. Verwacht grofweg één damespoule van 4 en één of twee herenpoules (afhankelijk van min/voorkeur/max, standaard 3–5 voorkeur 5).

---

## 3. Indelingsregels

1. Poules → **Indelingsregels** (tandwiel of de kaart).
   - [ ] Schakelaar mannen/vrouwen apart **aan**
   - [ ] Min / voorkeur / max zichtbaar; max gaat tot **10**
   - [ ] Gewichtsspreiding staat op **10%** (of de laatst opgeslagen waarde)
   - [ ] Bij elk percentage staat hoe gescoord wordt (100 / 0, treden, kg, enz.)
2. Kies snelkeuze **Leeftijd en niveau**. Opslaan.
   - [ ] Terug op poules: samenvatting toont geboortejaar zwaarder dan gewicht (gewicht 0%)
3. **Voorstel maken**.
   - [ ] Poules worden opnieuw gemaakt
   - [ ] Scores/breakdown volgen de nieuwe gewichten (geen of nauwelijks “Gewicht” als het 0% is)
4. Open de regels weer. Zet **Mannen en vrouwen apart** uit. Controleer dat **Geslacht** een slider krijgt. Zet geslacht ±20% of laat de default. Opslaan. **Voorstel maken**.
   - [ ] Mix is toegestaan: er kan een poule met M en V in ontstaan (niet verplicht als de andere scores dat afstraffen; noteer wat je ziet)
5. Zet de schakelaar weer **aan**, snelkeuze **Standaard (gewicht)**, min `3`, voorkeur `5`, max `6`. Opslaan. **Voorstel maken**.
   - [ ] Samenvatting: apart, poules 3–6 voorkeur 5, spreiding 10%, gewicht eerst

---

## 4. Slepen, lock, splitsen, samenvoegen

Gebruik de poules na stap 3.5 (standaardregels). Als een poule te klein is om te splitsen: sleep eerst iemand bij tot er minstens **4** in zitten, of maak een poule van 5 via een extra dames-deelnemer (Anna Pieters, 30 kg, 2016, Ingeschreven) en opnieuw voorstel.

1. Sleep een judoka van de ene poule naar een andere poule van **hetzelfde geslacht**.
   - [ ] Naam verhuist, letters en scores van beide poules worden bijgewerkt
2. Sleep naar een **vergrendelde** poule (eerst slot dicht, dan sleep).
   - [ ] Drop wordt geweigerd of de poule neemt niemand aan
3. **Slot open** op die poule. Split een poule met minstens 4 judoka’s (menu ⋮ → **Splitsen**).
   - [ ] Twee poules; samen evenveel mensen als daarvoor
4. Menu ⋮ → **Samenvoegen met …** terug naar de andere helft (of een poule die onder het maximum blijft).
   - [ ] Eén poule; weigert als het boven max (nu 6) zou komen
5. Sleep extra judoka’s in één poule tot die **boven het maximum** zit (slepen mag dat).
   - [ ] Die poule wordt rood
   - [ ] Tekst in de trant van: “Let op: maximum aantal judoka’s per poule is met … overschreden”
6. Vergrendel één poule (slot dicht). **Voorstel maken**.
   - [ ] Vergrendelde poule blijft hetzelfde (zelfde mensen)
   - [ ] Overige poules mogen veranderen

---

## 5. Bevestigen en annuleren

1. Zorg dat er poules met status **Voorstel** zijn (nieuw voorstel als nodig). **Annuleren** → in de dialoog **Terug**.
   - [ ] Poules blijven staan
2. **Annuleren** → nu echt **Annuleren**.
   - [ ] Niet-vergrendelde voorstel-poules zijn weg
   - [ ] Vergrendelde poules blijven (als je er een had)
3. **Voorstel maken**, daarna **Bevestigen**.
   - [ ] Status wordt **Bevestigd**
4. **F5** (zelfde http://localhost:8090), open het toernooi → Poules.
   - [ ] Bevestigde poules en scores komen terug

---

## 6. Restgroep en buiten scope

1. Zet alle deelnemers die in een poule mogen (Ingeschreven + gewicht) op één geslacht-groep van **1** persoon: bijv. alle heren op Niet aanwezig, één dame Ingeschreven met gewicht. **Voorstel maken**.
   - [ ] Die ene persoon wordt **niet geplaatst**
   - [ ] Onder de poules (of in plaats daarvan) een rood kader **Niet ingedeeld** met die naam onder Geen tegenstanders
2. Zet twee heren weer op Ingeschreven met gewicht, rest heren Niet aanwezig. **Voorstel maken**.
   - [ ] Een poule van 2 mag als restgroep, met lagere kwaliteit / aantekening rest

---

## Buiten scope (niet testen)

Wedstrijden, round-robin, uitslagen, matplanning, live-regie, iPad, printen, accounts.

**Later (fase 6):** algehele auditlog van handelingen en resultaten. Staat als actiepunt in `docs/ARCHITECTURE.md`.

---

## Resultaat

| Onderdeel | Ok | Probleem (kort) |
| --- | --- | --- |
| Deelnemers voor poules | | |
| Wie wel/niet in een voorstel | | |
| Rood kader niet-ingedeeld | | |
| Score en breakdown zichtbaar | | |
| 10%-regel / spreiding | | |
| Indelingsregels + presets | | |
| Sleep | | |
| Rode melding boven max | | |
| Lock + nieuw voorstel | | |
| Splitsen / samenvoegen | | |
| Annuleren / bevestigen | | |
| F5 houdt poules | | |
| Restgroep van 1 en 2 | | |

Getest door: _______________  Datum: _______________
