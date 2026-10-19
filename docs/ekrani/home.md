 Ekran Home — početna stranica

## 1. Svrha

Home je glavni ekran aplikacije. Prikazuje dnevni citat iz
izabrane kategorije i omogućava pristup ostalim funkcijama.

## 2. Elementi interfejsa

1. Zaglavlje sa nazivom aplikacije, zvonom i avatarom.
2. Pozdrav korisniku i datum.
3. Selektor kategorija: Vera, Sport, Život i Ljubav.
4. Kartica dnevnog citata.
5. Dugmad Sačuvaj, Podeli, Kopiraj i Novi citat.
6. Polje za pretragu.
7. Donja navigacija: Home, Pretraga, Omiljeni i Profil.

## 3. Ponašanje elemenata

### 3.1. Avatar

- Prijavljen korisnik otvara Profil.
- Gost se preusmerava na prijavu.
- Ako slika ne postoji, prikazuju se inicijali.

### 3.2. Obaveštenja

- Ikona otvara podešavanja obaveštenja.
- Korisnik može uključiti dnevni podsetnik.
- Sistem mora proveriti dozvole za push obaveštenja.

### 3.3. Izbor kategorije

- Korisnik bira jednu od četiri kategorije.
- Izbor odmah osvežava citat.
- Podrazumevano se koristi poslednja izabrana kategorija
  ili kategorija iz korisničkih podešavanja.
- Izbor se lokalno pamti, a za prijavljene korisnike
  može se sinhronizovati sa serverom.

### 3.4. Kartica citata

Prikazuje tekst citata, autora i kategoriju.

- Dugi citati mogu se skratiti uz opciju Prikaži više.
- Dodir na autora može otvoriti pretragu tog autora.
- Kartica prikazuje stanje učitavanja i greške.

### 3.5. Sačuvaj

- Dodir dodaje citat u omiljene.
- Ponovni dodir uklanja citat iz omiljenih.
- Gost dobija poruku da se prijavi.
- Greška pri čuvanju vraća prethodno stanje.

### 3.6. Podeli

- Otvara sistemski meni za deljenje.
- Tekst sadrži citat, autora i link ka aplikaciji.
- Deljenje može da se evidentira radi statistike.

### 3.7. Kopiraj

- Kopira tekst citata i autora u clipboard.
- Prikazuje poruku Kopirano.
- Za ovu akciju nije potreban API poziv.

### 3.8. Novi citat

- Učitava nasumičan citat iz izabrane kategorije.
- Poslednjih deset prikazanih citata treba isključiti
  iz sledećih rezultata kada je to moguće.
- Korisnik može da se vrati na dnevni citat.
- Dugme je onemogućeno tokom učitavanja.

### 3.9. Pretraga i navigacija

- Dodir na polje za pretragu otvara ekran Pretraga.
- Donja navigacija omogućava pristup glavnim ekranima.
- Gost može da pregleda citate, ali ne može da ih sačuva.

## 4. API

- `GET /api/v1/categories`
- `GET /api/v1/quotes/daily?category=vera`
- `GET /api/v1/quotes/random?category=vera`
- `POST /api/v1/favorites`
- `DELETE /api/v1/favorites/{quote_id}`
- `POST /api/v1/quotes/{id}/share`

Javni endpointi rade bez prijave. Omiljeni citati zahtevaju
autentikaciju.

## 5. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Tabele citata, autora, kategorija i omiljenih; indeksi |
| UX | Tok korisnika, izbor kategorije i stanja ekrana |
| UI | Kartica citata, čipovi, dugmad i navigacija |
| BE | Dnevni i nasumični citati, kategorije i omiljeni |
| FE | Home ekran, interakcije, clipboard i deljenje |
| DO | Keširanje, monitoring i infrastruktura za push |

## 6. Stanja ekrana

- Učitavanje: skeleton kartice.
- Greška: poruka i dugme Pokušaj ponovo.
- Offline: poslednji keširani citat, ako postoji.
- Gost: dostupne javne funkcije.
- Prazno stanje: odgovarajuća poruka ako sadržaj nije dostupan.
