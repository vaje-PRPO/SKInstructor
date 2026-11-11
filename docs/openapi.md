# OpenAPI / REST API Specifikacija - SKInstructor

Pregled osnovnih končnih točk (Endpoints) za posamezne mikrostoritve sistema SKInstructor.

## 1. Katalog učiteljev (`catalog-service`)
* `GET /teachers` – Pridobi seznam vseh učiteljev (možnost filtriranja po smučišču, ceni, jeziku).
* `GET /teachers/{id}` – Pridobi podrobne podatke posameznega učitelja.
* `POST /teachers` – Dodajanje novega učitelja v sistem.

## 2. Rezervacije (`booking-service`)
* `POST /bookings` – Ustvarjanje nove rezervacije (sproži preverjanje razpoložljivosti in plačilo).
* `GET /bookings/user/{userId}` – Pregled vseh rezervacij posameznega uporabnika.
* `PATCH /bookings/{id}/status` – Posodobitev statusa rezervacije (npr. potrditev po plačilu).

## 3. Mock plačila (`payment-service`)
* `POST /payments/process` – Simulacija obdelave plačila (vrne status uspeha ali neuspeha).
* `GET /payments/status/{transactionId}` – Preverjanje stanja izvedene transakcije.

## 4. Ocene in mnenja (`review-service`)
* `POST /reviews` – Oddaja ocene in komentarja za učitelja (ob predhodno potrjeni rezervaciji).
* `GET /reviews/teacher/{teacherId}` – Seznam vseh mnenj za določenega učitelja.
* `GET /reviews/teacher/{teacherId}/average` – Izračun povprečne ocene učitelja.