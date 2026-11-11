# Arhitektura sistema SKInstructor

## 1. Pregled arhitekture
Sistem **SKInstructor** je zgrajen na porazdeljeni **arhitekturi mikrostoritev (Microservices Architecture)**. Posamezne storitve so med seboj neodvisne, imajo lastne baze podatkov in komunicirajo preko sinhronih **REST API** klicev.

## 2. Seznam mikrostoritev in domene
* **Katalog učiteljev (`catalog-service`):** Upravlja profile učiteljev, njihove lokacije (smučišča), cene in jezike. Vsebuje lastno podatkovno bazo.
* **Rezervacije in urniki (`booking-service`):** Skrbi za jedrno poslovno logiko, preverjanje razpoložljivosti terminov in ustvarjanje rezervacij. Vsebuje lastno bazo podatkov.
* **Mock plačila (`payment-service`):** Zunanja simulacija plačilnega sistema (npr. Stripe/PayPal) za obdelavo transakcij. Deluje brez lastne baze podatkov.
* **Notification (`notification-service`):** Pošilja sistemska obvestila in potrditve uporabnikom prek elektronske pošte ali SMS-sporočil.

## 3. Komunikacija med storitvami
1. Uporabnik išče učitelje preko `catalog-service`.
2. Ob rezervaciji se pošlje zahtevek na `booking-service`.
3. `booking-service` preveri razpoložljivost in izvede sinhronski HTTP klic na `payment-service` (`POST /payments/process`).
4. Po uspešnem plačilu `booking-service` potrdi rezervacijo v bazi.
5. Uporabnik lahko preko `review-service` odda oceno učitelja.

## 4. Tehnološki sklad in zagon
* Vse storitve so containerizirane in se skupaj zaženejo z orodjem **Docker Compose** (`docker-compose.yml` v korenski mapi repozitorija).
```[cite: 2]    