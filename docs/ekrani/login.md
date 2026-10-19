Ekran Log in — prijava

## 1. Svrha

Omogućava postojećem korisniku prijavu emailom i lozinkom
ili putem Google i Apple naloga.

## 2. Elementi interfejsa

1. Dugme Nazad ili Zatvori.
2. Logo i naslov Dobrodošao nazad.
3. Polje Email.
4. Polje Lozinka sa ikonom za prikaz.
5. Link Zaboravljena lozinka?
6. Dugme Prijavi se.
7. Separator ili.
8. Dugmad Nastavi sa Google i Nastavi sa Apple.
9. Link za registraciju.
10. Link Nastavi kao gost.

## 3. Ponašanje i validacija

### Email

- Uklanjaju se razmaci sa početka i kraja.
- Email se normalizuje pre slanja.
- Proverava se format adrese.
- Poruka greške: Unesi ispravnu email adresu.

### Lozinka

- Podrazumevano je skrivena.
- Ikona oka uključuje ili isključuje prikaz.
- Lozinka se ne čuva u logovima niti običnom lokalnom skladištu.

### Prijava

- Dugme prikazuje indikator učitavanja.
- Višestruko slanje istog zahteva sprečava se.
- Pri uspehu korisnik se vraća na prethodno odredište
  ili odlazi na Home.
- Pogrešni podaci daju istu poruku radi bezbednosti.

### Zaboravljena lozinka

Korisnik unosi email adresu. Odgovor ne otkriva da li nalog
postoji.

Poruka: Ako nalog postoji, poslali smo uputstvo na email.

### Google i Apple

Server mora proveriti identitetski token kod provajdera.
Klijent ne sme samostalno da proglasi korisnika prijavljenim.

### Nastavi kao gost

Gost može da pregleda, pretražuje, filtrira i deli citate.
Čuvanje omiljenih citata zahteva nalog.

## 4. API

- `POST /api/v1/auth/login`
- `POST /api/v1/auth/social`
- `POST /api/v1/auth/refresh`
- `POST /api/v1/auth/logout`
- `POST /api/v1/auth/forgot-password`
- `POST /api/v1/auth/reset-password`

## 5. Bezbednost

- HTTPS je obavezan.
- Lozinke se proveravaju u odnosu na bezbedan heš.
- Refresh token se čuva u sigurnom skladištu na uređaju.
- Server čuva heš refresh tokena i podržava njegovo opozivanje.
- Neuspele prijave podležu ograničenju broja pokušaja.
- Greške ne smeju otkrivati da li email postoji.
- Tokeni i lozinke ne smeju se upisivati u logove.

## 6. Stanja ekrana

- Učitavanje: spinner na dugmetu.
- Validacija: poruke ispod polja.
- Neispravni podaci: Netačan email ili lozinka.
- Previše pokušaja: poruka o privremenom ograničenju.
- Offline: Proveri internet vezu.
- Nepotvrđen email: poziv da se email potvrdi.

## 7. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Korisnici, refresh tokeni i reset lozinke |
| UX | Tok prijave, greške i povratak na prethodni ekran |
| UI | Polja, dugmad, ikone i stanja učitavanja |
| BE | Prijava, tokeni, reset lozinke i socijalna autentikacija |
| FE | Forma, validacija i sigurno čuvanje tokena |
| DO | HTTPS, tajne, rate limit i monitoring |

## 8. Napomena

Ako se omogući prijava preko Google naloga, treba proveriti
važeće zahteve Apple App Store-a za prijavu preko Apple naloga.
