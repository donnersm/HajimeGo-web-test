# Fase 3 — handmatig testen

Status: **afgerond** (6 september 2026).

Doel: controleren of round-robinwedstrijden, uitslag + stand, wedstrijdregels (duur en technieken), bevestigen-op-slot, waarschuwing bij een nieuw voorstel, geboortejaar op de poulekaart en uitvallers kloppen. Matplanning, live-regie, printen en auditlog horen **niet** bij deze ronde.

App: lokaal [http://localhost:8090](http://localhost:8090) (Chrome of Edge). Blijf op die poort; een andere poort of browser is een lege database. De bevroren fase-2-test op GitHub Pages heeft **geen** wedstrijden.

Testdata: dezelfde Excel-bestanden als fase 1 en 2, in `docs/testdata/` (`JC-Noord.xlsx`, `JC-Zuid.xlsx`). Fictieve namen.

Tijd: ongeveer 20–30 minuten. Vink af wat klopt; noteer bij een fout wat je deed en wat je zag.

---

## Voorbereiding

- [ ] App open (`cd app` → `flutter run -d chrome --web-port 8090`)
- [ ] Startscherm toont “Klaar voor de mat” en noemt poules **en** wedstrijden
- [ ] Bestanden aanwezig: `JC-Noord.xlsx`, `JC-Zuid.xlsx`

---

## 1. Toernooi, deelnemers en poules

Iedereen moet Ingeschreven blijven met gewicht (Kim dus **niet** op Niet aanwezig; geen Teun zonder kg). Dan zijn er 5 dames en 5 heren — twee poules van 5, nodig voor de uitvaller-check.

1. Home → **Nieuw toernooi**.
2. Naam `Fase 3 test`, datum morgen, locatie `Sporthal Test`, organisator `JC Demo`, tatami `3`. Opslaan.
3. Open het toernooi.
   - [ ] Kaart **Poules** en kaart **Wedstrijden** zijn allebei zichtbaar
4. **Deelnemers** → Excel importeren → `JC-Noord.xlsx` → importeren.
5. Importeer daarna `JC-Zuid.xlsx` (dubbele namen overslaan **aan**).
   - [ ] **10 deelnemers**
6. Open **Wedstrijden** terwijl er nog geen bevestigde poules zijn.
   - [ ] Tekst dat je eerst een poulevoorstel moet bevestigen
7. Terug → **Poules** → **Voorstel maken**.
   - [ ] Twee poules van 5 (dames en heren)
   - [ ] Bij elke judoka: gewicht, **geboortejaar**, band, categorie, club
   - [ ] Per poule: pouleklasse (volgt de oudste) en vinkjes Armklemmen / Omstrengelingen / Sutemi’s
8. Open een poulekaart van de dames (jongste groep, waarschijnlijk -10 of -12 jaar).
   - [ ] Armklemmen, omstrengelingen en sutemi’s staan **uit**
9. Open een poulekaart van de heren (oudste is 2012 → -15 jaar).
   - [ ] Omstrengelingen **aan**, armklemmen en sutemi’s **uit**
   - [ ] Wedstrijdduur bij die klasse is **3 min**

---

## 2. Nieuw voorstel waarschuwt; bevestigen zet alles op slot

1. Nog steeds op Poules, status **Voorstel**. Druk opnieuw op **Voorstel maken**.
   - [ ] Dialoog: *Er is al een poule indeling gemaakt, alle poulen welke niet vergrendeld zijn kunnen verloren gaan*
2. **Terug**.
   - [ ] Poules blijven staan, niemand is weg
3. Opnieuw **Voorstel maken** → **Doorgaan**.
   - [ ] Er komt weer een voorstel; niet-vergrendelde poules mogen opnieuw zijn ingedeeld
4. **Bevestigen**.
   - [ ] Status **Bevestigd**
   - [ ] Elke poule heeft een **dicht slot**
5. Klik het slot van één poule open (heropenen).
   - [ ] Die poule is ontgrendeld, de andere blijven op slot
6. **Voorstel maken** → in de waarschuwing **Doorgaan**.
   - [ ] De ontgrendelde poule mag verdwijnen of opnieuw worden gemaakt
   - [ ] De nog vergrendelde poule blijft hetzelfde (zelfde mensen)
7. Zet zo nodig opnieuw een volledig voorstel (beide poules van 5) en **Bevestigen**, zodat beide weer op slot staan.
   - [ ] Beide poules bevestigd en vergrendeld

---

## 3. Wedstrijdregels per pouleklasse

1. Toernooi → **Wedstrijden** → kaart **Wedstrijdregels**.
   - [ ] Transitietijd (standaard 30 s) en gelijkspel / golden score
   - [ ] Sectie **Heren** en **Dames**, per klasse een duur **en** drie vinkjes
2. Standaard (niets wijzigen, alleen kijken):
   - [ ] -8 / -10 / -12: **2 min**, alle technieken uit
   - [ ] -15: **3 min**, alleen omstrengelingen aan
   - [ ] -18 / -20 / Senioren: **4 min**, alle drie aan
3. Zet bij **Dames -10 jaar** (of de klasse van jouw damespoule) **Armklemmen** aan. Zet de transitietijd op **45 s**. Opslaan.
4. Terug op Wedstrijden, kijk naar de damespoule.
   - [ ] Armklemmen staat **aan** (overgenomen uit de klasse)
   - [ ] Maximale pouleduur is herberekend (wedstrijden + transitie ertussen)
5. Open Wedstrijdregels opnieuw.
   - [ ] Armklemmen bij die damesklasse en transitie 45 s zijn bewaard
6. Zet armklemmen bij die klasse weer **uit** en transitie terug op **30 s**. Opslaan.

Pouleklasse handmatig wijzigen (rood) en **Default** horen ook: de vinkjes volgen dan weer de (nieuwe) klasse. Optioneel meenemen als je tijd hebt.

---

## 4. Round-robin, uitslag en stand

Een poule van *n* heeft `n×(n−1)/2` wedstrijden: 5 judoka’s → **10** fights, allemaal status **Gepland**.

1. Wedstrijden, herenpoule.
   - [ ] **0/10 klaar** en 10 regels A–B, A–C, …
2. Tik de eerste wedstrijd. Kies een winnaar en methode **Ippon**. Bevestig.
   - [ ] Die wedstrijd is **Afgerond** (naam + Ippon)
   - [ ] Stand: die winnaar **W 1**, **Ptn 10**, teller **1/10 klaar**
3. Tik dezelfde wedstrijd opnieuw.
   - [ ] Geen nieuwe uitslag; hij blijft zoals hij was
4. Voer een tweede fight in met **Waza-ari** voor een andere winnaar.
   - [ ] Die heeft **W 1**, **Ptn 7**
   - [ ] De ippon-winnaar staat boven de waza-ari-winnaar bij gelijke overwinningen (punten). Bij twee judoka’s met gelijke winst én punten telt de onderlinge wedstrijd. Bij drie of meer met gelijke stand: rode melding handmatige beoordeling, geen verzonnen mini-poule.
5. Methoden **Yuko** (5 punten), **Hantei** (1), **Fusen** (10, kies wie wint omdat de ander niet opdaagt) en **Waza-ari-awasete-ippon** (10, telt als ippon) kort proberen.
   - [ ] Punten in de stand kloppen
   - [ ] Bij Fusen staat de toelichting over niet opdagen

---

## 5. Uitvaller (poule van 5, klaar-criterium)

Kies in de **herenpoule** één judoka die nog open fights heeft. Noteer de naam: _______________

1. Voer **twee** uitslagen in van fights waar die judoka in zit (als die twee nog Gepland waren).
   - [ ] Die twee staan op Afgerond
2. In de stand: icoon persoon-uit → **Uitvallen** (niet Terug).
   - [ ] Waarschuwing: toekomstige wedstrijden worden geannuleerd, afgeronde blijven
3. Controleer de 10 fights van die poule:
   - [ ] De **2** afgeronde fights van de uitvaller blijven Afgerond
   - [ ] De **2** overige fights van de uitvaller zijn **Geannuleerd**
   - [ ] De **6** fights zonder de uitvaller blijven **Gepland**
4. Probeer een geannuleerde fight aan te tikken.
   - [ ] Geen uitslag mogelijk
5. Voer nog één fight in tussen twee achterblijvers.
   - [ ] Stand van die twee loopt bij; de uitvaller blijft in de tabel

De damespoule kun je met rust laten (alle 10 nog Gepland) als extra controle dat uitval in de ene poule de andere niet raakt.

---

## 6. F5

1. **F5** (zelfde http://localhost:8090), open `Fase 3 test` → Poules en Wedstrijden.
   - [ ] Bevestigde poules, slotjes, geboortejaren
   - [ ] Zelfde uitslagen, stand, geannuleerde fights van de uitvaller
   - [ ] Wedstrijdregels (tijden / vinkjes) nog zoals opgeslagen

---

## Buiten scope (niet testen)

Statussen *klaargezet* en *bezig* (datamodel wel, geen knoppen; geen HajimeGo-matttafel). Live-regie, printen, accounts, auditlog. iPads en wifi horen bij fase 9.

---

## Resultaat

| Onderdeel | Ok | Probleem (kort) |
| --- | --- | --- |
| Kaart Wedstrijden op het toernooi | | |
| Geboortejaar op poulekaart | | |
| Technieken uit pouleklasse | | |
| Waarschuwing bij nieuw voorstel | | |
| Bevestigen zet alle poules op slot | | |
| Slotje heropent | | |
| Wedstrijdregels: tijd + 3 vinkjes per klasse | | |
| Klasse-vinkjes komen op de poule | | |
| 10 fights in poule van 5 | | |
| Uitslag + stand (ippon 10 / waza-ari 7) | | |
| Afgeronde fight niet overschrijven | | |
| Uitvaller: 2 blijven, 2 vervallen, 6 gaan door | | |
| F5 houdt wedstrijden | | |

Getest door: _______________  Datum: _______________
