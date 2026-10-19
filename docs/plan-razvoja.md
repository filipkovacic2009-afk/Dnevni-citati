 Plan razvoja aplikacije Dnevni citati

## 1. Faze razvoja

### Faza 1 — Temelji

Zadaci:

- Potvrda tehnologija.
- Definisanje modela baze podataka.
- Priprema osnovnog API projekta.
- Podešavanje repozitorijuma i CI/CD procesa.
- Izrada dizajn sistema.
- Postavljanje osnovne navigacije.

Rezultat: pripremljena osnova za razvoj.

### Faza 2 — Citati bez naloga

Zadaci:

- Home ekran.
- Prikaz dnevnog citata.
- Izbor kategorija.
- Nasumični citati.
- Kopiranje i deljenje.
- Osnovni offline prikaz.

Rezultat: gost može da koristi glavne funkcije citata.

### Faza 3 — Korisnički nalozi

Zadaci:

- Registracija.
- Prijava i odjava.
- Potvrda emaila.
- Resetovanje lozinke.
- Osnovni profil.
- Osnovna podešavanja korisnika.

Rezultat: korisnici mogu da kreiraju i koriste nalog.

### Faza 4 — Omiljeni i pretraga

Zadaci:

- Dodavanje i uklanjanje omiljenih citata.
- Lista omiljenih.
- Pretraga citata i autora.
- Predlozi pretrage.
- Filteri.
- Istorija pretrage.
- Paginacija i optimizacija upita.

Rezultat: implementirane su glavne funkcije pronalaženja
i organizovanja citata.

### Faza 5 — Angažovanje korisnika

Zadaci:

- Dnevna push obaveštenja.
- Podešavanje vremena obaveštenja.
- Svetla i tamna tema.
- Statistika aktivnosti.
- Niz dana korišćenja.
- Brisanje naloga i obrada zahteva za privatnost.

Rezultat: kompletirana su dodatna korisnička podešavanja.

### Faza 6 — Stabilizacija i objava

Zadaci:

- Funkcionalno testiranje.
- Testiranje bezbednosti.
- Testiranje performansi i opterećenja.
- Testiranje rada bez interneta.
- Testiranje različitih uređaja i veličina ekrana.
- Provera pravnih stranica i privatnosti.
- Priprema objave u prodavnicama.
- Monitoring produkcije.

Rezultat: aplikacija je spremna za kontrolisano objavljivanje.

## 2. Otvorena pitanja

Pre konačne implementacije potrebno je odlučiti:

1. Da li aplikacija podržava samo srpski ili više jezika?
2. Odakle dolaze citati i ko odobrava njihov sadržaj?
3. Da li je potreban administratorski panel?
4. Da li se razvija i web verzija?
5. Da li je dnevni citat isti za sve korisnike?
6. Koje tehnologije se konačno biraju?
7. Koji su konačni zahtevi za brisanje i čuvanje podataka?
8. Koji su kriterijumi za uspešan završetak svake faze?

## 3. Predlog testiranja

### Funkcionalni testovi

- Prikaz dnevnog citata.
- Promena kategorije.
- Registracija i prijava.
- Čuvanje omiljenih.
- Pretraga i filteri.
- Promena podešavanja.
- Odjava i brisanje naloga.

### Bezbednosni testovi

- Validacija ulaznih podataka.
- Provera autentikacije i autorizacije.
- Ograničenje broja zahteva.
- Bezbedno čuvanje tokena.
- Zaštita privatnih podataka.

### Testovi performansi

- Vreme odgovora API-ja.
- Brzina pretrage.
- Paginacija velikih lista.
- Opterećenje pri slanju obaveštenja.
- Ponašanje sistema pri većem broju korisnika.

### Testovi pouzdanosti

- Gubitak internet veze.
- Oporavak nakon greške servera.
- Vraćanje baze iz rezervne kopije.
- Istek i opoziv tokena.

## 4. Kriterijumi završetka projekta

Projekat se smatra spremnim za objavu kada:

- Sve dogovorene funkcionalnosti rade.
- Kritične greške su otklonjene.
- Bezbednosne provere su završene.
- Baza ima proverene migracije i rezervne kopije.
- Ključni korisnički tokovi su testirani.
- Privatnost i uslovi korišćenja su dostupni.
- Monitoring i procedura oporavka su pripremljeni.
