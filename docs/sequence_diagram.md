# Sekvenčni diagram (Sequence Diagram) - SKInstructor

Tukaj je predstavljen časovni in zaporedni potek interakcij med akterji in mikrostoritvami v sistemu SKInstructor (primer rezervacije ure s plačilom).

## Scenarij: Uspešna rezervacija učitelja in plačilo

1. **Uporabnik / Frontend** pošlje zahtevek za iskanje učiteljev na `catalog-service` (`GET /teachers?resort=KranjskaGora`).
2. **Katalog učiteljev** vrne seznam razpoložljivih učiteljev z njihovimi podatki in povprečno oceno.
3. **Uporabnik** izbere učitelja in pošlje zahtevo za rezervacijo termina na `booking-service` (`POST /bookings`).
4. **Booking-service** preveri svojo bazo, ali je učitelj v tistem terminu prost.
   * *Če je zaseden:* Vrne napako (400 Bad Request).
   * *Če je prost:* Nadaljuje s postopkom.
5. **Booking-service** pošlje sinhronski HTTP zahtevek na `payment-service` (`POST /payments/process`) z zneskom in podatki o rezervaciji.
6. **Payment-service** simulira obdelavo plačila (z zamikom) in vrne status `SUCCESS`.
7. **Booking-service** prejme potrditev plačila, posodobi status rezervacije v svoji bazi iz `PENDING` v `CONFIRMED` in vrne uspešen odziv uporabniku.
8. **Uporabnik** lahko kasneje preko `review-service` odda oceno (`POST /reviews`), pri čemer servis preveri, ali ima uporabnik potrjeno rezervacijo.