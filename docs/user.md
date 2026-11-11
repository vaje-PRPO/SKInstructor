# Uporabniške zgodbe (User Stories) - SKInstructor

Tukaj so zbrane ključne uporabniške zgodbe za aplikacijo SKInstructor, razdeljene po posameznih mikrostoritvah in funkcionalnostih.

## 1. Katalog učiteljev (`catalog-service`)
* **US1.1:** Kot smučar/stranka želim pregledati seznam vseh razpoložljivih učiteljev, da izberem ustreznega glede na svoje potrebe.
* **US1.2:** Kot smučar/stranka želim filtrirati učitelje glede na smučišče, ceno na uro in jezike, ki jih govorijo, da hitreje najdem ustreznega ponudnika.
* **US1.3:** Kot smučar/stranka želim videti podrobnosti posameznega učitelja (biografija, licenca, ocena), preden ga rezerviram.
* **US1.4:** Kot administrator/učitelj želim vnesti nov profil učitelja v sistem ali posodobiti obstoječe podatke.

## 2. Rezervacije in urniki (`booking-service`)
* **US2.1:** Kot smučar/stranka želim rezervirati termin z izbranim učiteljem za določen datum in uro.
* **US2.2:** Kot sistem moram preveriti zasedenost učitelja, preden potrdim novo rezervacijo, da preprečim prekrivanje terminov.
* **US2.3:** Kot smučar/stranka želim pregledati seznam svojih preteklih in aktivnih rezervacij.
* **US2.4:** Kot smučar/stranka želim preklicati rezervacijo, če se moji načrti spremenijo.

## 3. Mock plačila (`payment-service`)
* **US3.1:** Kot sistem moram ob oddaji rezervacije samodejno sprožiti simuliran postopek plačila (preklic ali potrditev transakcije).
* **US3.2:** Kot smučar/stranka želim prejeti takojšnjo povratno informacijo o uspešnosti plačila, da se status rezervacije ustrezno posodobi.

## 4. Ocene in mnenja (`review-service`)
* **US4.1:** Kot smučar/stranka želim po opravljeni uri smučanja oddati oceno (1–5 zvezdic) in komentar za učitelja.
* **US4.2:** Kot sistem moram preveriti, ali ima uporabnik resnično potrjeno rezervacijo pri tem učitelju, preden mu dovolim oddajo ocene.
* **US4.3:** Kot smučar/stranka želim videti izračunano povprečno oceno učitelja na njegovem profilu v katalogu.