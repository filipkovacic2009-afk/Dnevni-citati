Pregled API-ja

## 1. Opšti standardi

Osnovna putanja API-ja je `/api/v1`.

API koristi HTTP metode i JSON format.

Predloženi format odgovora:

{
  "data": {},
  "error": null,
  "meta": {}
}

Polja se prilagođavaju konkretnom endpointu.

Za greške se koriste odgovarajući HTTP statusi, na primer:

- 200 — zahtev je uspešan.
- 201 — resurs je kreiran.
- 400 — neispravan zahtev.
- 401 — potrebna je autentikacija.
- 403 — pristup nije dozvoljen.
- 404 — resurs nije pronađen.
- 409 — konflikt, na primer duplirani resurs.
- 429 — previše zahteva.
- 500 — interna greška servera.

## 2. Autentikacija

| Metoda | Endpoint | Opis | Prijava |
|---|---|---|---|
| POST | `/api/v1/auth/register` | Registracija | Ne |
| POST | `/api/v1/auth/login` | Prijava | Ne |
| POST | `/api/v1/auth/social` | Google/Apple prijava | Ne |
| POST | `/api/v1/auth/refresh` | Obnova tokena | Refresh token |
| POST | `/api/v1/auth/logout` | Odjava | Da |
| POST | `/api/v1/auth/forgot-password` | Zahtev za reset lozinke | Ne |
| POST | `/api/v1/auth/reset-password` | Postavljanje nove lozinke | Token za reset |
| POST | `/api/v1/auth/verify-email` | Potvrda emaila | Token za potvrdu |
| POST | `/api/v1/auth/resend-verification` | Ponovno slanje potvrde | Prema implementaciji |
| GET | `/api/v1/auth/check-email` | Provera dostupnosti emaila | Ne |

## 3. Citati i kategorije

| Metoda | Endpoint | Opis | Prijava |
|---|---|---|---|
| GET | `/api/v1/categories` | Lista kategorija | Ne |
| GET | `/api/v1/quotes/daily` | Dnevni citat | Ne |
| GET | `/api/v1/quotes/random` | Nasumični citat | Ne |
| GET | `/api/v1/quotes/search` | Pretraga citata | Ne |
| GET | `/api/v1/quotes/count` | Broj rezultata | Ne, osim za zaštićene filtere |
| POST | `/api/v1/quotes/{id}/share` | Evidencija deljenja | Ne |
| GET | `/api/v1/authors` | Lista autora | Ne |
| GET | `/api/v1/search/suggestions` | Predlozi pretrage | Ne |

## 4. Omiljeni citati

| Metoda | Endpoint | Opis | Prijava |
|---|---|---|---|
| GET | `/api/v1/favorites` | Lista omiljenih | Da |
| POST | `/api/v1/favorites` | Dodavanje u omiljene | Da |
| DELETE | `/api/v1/favorites/{quote_id}` | Uklanjanje iz omiljenih | Da |

Dodavanje u omiljene treba da bude idempotentno.
Duplirani zahtev ne sme napraviti duplirani zapis.

## 5. Profil i podešavanja

| Metoda | Endpoint | Opis | Prijava |
|---|---|---|---|
| GET | `/api/v1/me` | Podaci profila | Da |
| PATCH | `/api/v1/me` | Izmena profila | Da |
| DELETE | `/api/v1/me` | Brisanje naloga | Da |
| POST | `/api/v1/me/avatar` | Postavljanje avatara | Da |
| DELETE | `/api/v1/me/avatar` | Uklanjanje avatara | Da |
| GET | `/api/v1/me/preferences` | Čitanje podešavanja | Da |
| PATCH | `/api/v1/me/preferences` | Izmena podešavanja | Da |
| GET | `/api/v1/me/stats` | Statistika korisnika | Da |
| POST | `/api/v1/me/devices` | Registracija uređaja | Da |
| POST | `/api/v1/me/change-password` | Promena lozinke | Da |
| POST | `/api/v1/me/change-email` | Zahtev za promenu emaila | Da |

## 6. Istorija pretrage

| Metoda | Endpoint | Opis | Prijava |
|---|---|---|---|
| GET | `/api/v1/me/search-history` | Čitanje istorije | Da |
| POST | `/api/v1/me/search-history` | Dodavanje upita | Da |
| DELETE | `/api/v1/me/search-history/{id}` | Brisanje upita | Da |
| DELETE | `/api/v1/me/search-history` | Brisanje cele istorije | Da |

Gosti čuvaju istoriju lokalno.

## 7. Primer zahteva

Dnevni citat:

GET `/api/v1/quotes/daily?category=vera`

Pretraga:

GET `/api/v1/quotes/search?q=ljubav&page=1&limit=20`

Filteri:

GET `/api/v1/quotes/search?category=vera,sport&length=short&sort=popular`

Nasumični citat:

GET `/api/v1/quotes/random?category=sport&exclude=12,45,78`

## 8. Paginacija

Liste koriste parametre `page` i `limit`.
Podrazumevana veličina stranice može biti 20 stavki.

Odgovor treba da sadrži podatke o ukupnom broju rezultata
i paginaciji kada su dostupni.

## 9. Bezbednosni zahtevi

- Validacija svih ulaznih podataka.
- Autorizacija za privatne podatke.
- Rate limiting prema riziku endpointa.
- HTTPS za sve zahteve.
- Bezbedno rukovanje tokenima.
- Bez logovanja lozinki i tajnih tokena.
- Dosledne poruke grešaka.

## 10. Napomena

Ovo je predlog ugovora API-ja. Pre implementacije potrebno je
uskladiti nazive polja, šeme zahteva i odgovora, statusne
kodove i ponašanje svih endpointa.
