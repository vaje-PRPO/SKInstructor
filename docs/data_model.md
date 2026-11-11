# Podatkovni model (Data Model) - SKInstructor

Tukaj so opisane podatkovne baze in strukture tabel za posamezne mikrostoritve, ki uporabljajo lastno shrambo podatkov.

## 1. Katalog učiteljev (`catalog-service`)
Baza hrani profile smučarskih učiteljev in njihove osnovne podatke za filtriranje in iskanje.

* **Tabela: `teachers`**
  * `id` (PK, Long / UUID) - Enolični identifikator učitelja
  * `name` (String) - Ime učitelja
  * `surname` (String) - Priimek učitelja
  * `resort` (String) - Smučišče, kjer učitelj deluje (npr. Kranjska Gora, Vogel)
  * `price_per_hour` (Decimal) - Cena ure poučevanja v EUR
  * `languages` (String / List) - Jeziki, ki jih učitelj govori (npr. SLO, ENG, ITA)
  * `license_level` (String) - Stopnja licence (npr. Učitelj 3, Demonstrator)
  * `bio` (Text) - Opis izkušenj in biografija
  * `contact_email` (String) - Kontaktni e-naslov

---

## 2. Rezervacije in urniki (`booking-service`)
Baza hrani podatke o rezervacijah terminov med uporabniki in učitelji.

* **Tabela: `bookings`**
  * `id` (PK, Long / UUID) - Enolični identifikator rezervacije
  * `teacher_id` (Long) - ID učitelja iz katalog-storitve
  * `user_id` (Long) - ID uporabnika, ki je opravil rezervacijo
  * `date` (Date) - Datum izvedbe smučarske ure
  * `start_time` (Time) - Ura začetka
  * `duration_hours` (Integer) - Število ur trajanja
  * `total_price` (Decimal) - Skupni znesek za plačilo
  * `status` (String) - Trenutni status (`PENDING`, `CONFIRMED`, `CANCELLED`)

---

## 3. Ocene in mnenja (`review-service`)
Baza hrani ocene in komentarje, ki jih uporabniki oddajo po opravljenih urah.

* **Tabela: `reviews`**
  * `id` (PK, Long / UUID) - Enolični identifikator ocene
  * `teacher_id` (Long) - ID ocenjenega učitelja
  * `user_id` (Long) - ID uporabnika, ki je oddal oceno
  * `booking_id` (Long) - ID povezane rezervacije (preprečuje lažne ocene)
  * `rating` (Integer) - Ocena od 1 do 5
  * `comment` (Text) - Besedilo mnenja / komentarja
  * `created_at` (Timestamp) - Čas oddaje ocene

*(Opomba: `payment-service` deluje kot mock storitev brez lastne baze podatkov, zato podatkovnega modela nima.)*
```[cite: 2]