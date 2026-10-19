Ekran Sign up — registracija

## 1. Svrha

Omogućava novom korisniku da kreira nalog brzo i bezbedno.
Cilj je da osnovna registracija traje manje od 60 sekundi.

## 2. Elementi interfejsa

1. Dugme Nazad.
2. Naslov Napravi nalog.
3. Polje Ime.
4. Polje Email.
5. Polje Lozinka i indikator jačine.
6. Polje Potvrdi lozinku.
7. Izbor podrazumevane kategorije.
8. Checkbox za prihvatanje uslova.
9. Dugme Napravi nalog.
10. Google i Apple registracija.
11. Link za postojeće korisnike.

## 3. Validacija polja

### Ime

- Dozvoljeno je 2–50 karaktera.
- Uklanjaju se višestruki razmaci.
- Podržana su slova latinice i ćirilice.
- Server ponavlja validaciju.

### Email

- Proverava se format adrese.
- Email se normalizuje.
- Dostupnost se može proveriti nakon prestanka kucanja.
- Provera mora biti ograničena da se ne bi zloupotrebila
  za otkrivanje registrovanih korisnika.

### Lozinka

- Najmanje 8 karaktera.
- Najmanje jedno slovo i jedan broj.
- Prikazuje se indikator jačine.
- Server proverava pravila i odbija poznate slabe lozinke.
- U bazi se čuva samo heš lozinke.

### Potvrda lozinke

- Mora da se podudara sa lozinkom.
- Provera se vrši na klijentu.
- Poruka: Lozinke se ne poklapaju.

### Podrazumevana kategorija

Korisnik može izabrati jednu kategoriju.
Ako izbor preskoči, podrazumevana kategorija je Život.

### Prihvatanje uslova

- Checkbox je obavezan.
- Linkovi vode do uslova korišćenja i politike privatnosti.
- Beleže se vreme i verzija prihvaćenih uslova.

## 4. Kreiranje naloga

1. Klijent validira formu.
2. Server ponovo proverava sva polja.
3. Korisnik i podešavanja kreiraju se u transakciji.
4. Lozinka se bezbedno hešira.
5. Kreira se token za potvrdu emaila.
6. Email se šalje preko servisa za slanje poruka.
7. Korisniku se prikazuje poruka o potvrdi emaila.

## 5. API

- `POST /api/v1/auth/register`
- `GET /api/v1/auth/check-email`
- `POST /api/v1/auth/verify-email`
- `POST /api/v1/auth/resend-verification`
- `POST /api/v1/auth/social`

## 6. Bezbednost i privatnost

- Zahtevi se šalju preko HTTPS-a.
- Lozinke se nikada ne čuvaju u otvorenom tekstu.
- Token za potvrdu ima ograničeno vreme važenja.
- Endpointi za registraciju imaju rate limit.
- Prihvatanje uslova se evidentira.
- Korisnik mora imati mogućnost izvoza i brisanja podataka
  u skladu sa važećim propisima.

## 7. Stanja ekrana

- Neispravna polja: poruka ispod odgovarajućeg polja.
- Zauzet email: poruka sa opcijom prijave.
- Učitavanje: spinner na dugmetu.
- Uspeh: ekran Potvrdi email.
- Greška servera: poruka i mogućnost ponovnog pokušaja.

## 8. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Korisnici, podešavanja i tokeni za verifikaciju |
| UX | Tok registracije i validacija |
| UI | Forma, indikator lozinke i checkbox uslova |
| BE | Registracija, heširanje i verifikacija emaila |
| FE | Forma, provere polja i slanje zahteva |
| DO | Email servis, tajne, rate limit i monitoring |
