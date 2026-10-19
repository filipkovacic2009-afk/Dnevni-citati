Ekran Profil

## 1. Svrha

Omogućava korisniku da pregleda i menja svoje podatke,
podešavanja, omiljene citate i bezbednosne opcije naloga.

Gostu se prikazuje poziv da se prijavi ili registruje.

## 2. Elementi interfejsa

1. Avatar, ime i email.
2. Dugme Uredi profil.
3. Statistika omiljenih citata i niza dana.
4. Prečica ka omiljenim citatima.
5. Podešavanja kategorije, obaveštenja, teme i jezika.
6. Promena lozinke, odjava i brisanje naloga.
7. Uslovi korišćenja, privatnost, kontakt i verzija aplikacije.

## 3. Funkcionalnosti

### 3.1. Avatar

- Korisnik može da izabere sliku iz galerije ili kamerom.
- Slika se smanjuje na maksimalno 512 × 512 piksela.
- Maksimalna veličina datoteke je 2 MB.
- Podržani formati: JPG, PNG i WebP.
- Server proverava format i uklanja EXIF metapodatke.
- U bazi se čuva URL slike, a datoteka u objektnoj memoriji.

### 3.2. Izmena profila

- Korisnik menja ime.
- Email se menja posebnim postupkom uz potvrdu nove adrese.
- Dugme Sačuvaj aktivno je samo kada postoje izmene.
- Pri izlasku sa nesačuvanim izmenama prikazuje se upozorenje.

### 3.3. Statistika

Prikazuje se broj omiljenih citata i niz dana aktivnosti.

- Broj omiljenih citata dobija se iz baze.
- Aktivnost se računa prema vremenskoj zoni korisnika.
- Potrebno je definisati pravilo za računanje niza dana.

### 3.4. Omiljeni citati

- Lista se sortira od najnovije sačuvanih ka starijim.
- Prikazuju se tekst, autor i kategorija.
- Korisnik može ukloniti citat.
- Lista podržava paginaciju ili beskonačno učitavanje.
- Prazno stanje nudi opciju Istraži citate.

### 3.5. Podrazumevana kategorija

Korisnik bira kategoriju koja se prva prikazuje na Home ekranu.
Izbor se čuva na serveru i lokalno stanje se ažurira.

### 3.6. Obaveštenja

- Korisnik uključuje ili isključuje dnevni podsetnik.
- Može izabrati vreme slanja.
- Potrebna je dozvola operativnog sistema.
- Server čuva push token uređaja.
- Vreme slanja tumači se prema vremenskoj zoni korisnika.

### 3.7. Tema i jezik

- Tema: svetla, tamna ili sistemska.
- Jezik se čuva u korisničkim podešavanjima.
- Promena teme primenjuje se bez ponovnog pokretanja.

### 3.8. Promena lozinke

- Zahteva se trenutna lozinka.
- Nova lozinka mora zadovoljiti bezbednosna pravila.
- Potvrda nove lozinke mora se podudarati.
- Ostale aktivne sesije mogu se opozvati nakon promene.

### 3.9. Odjava

- Prikazuje se dijalog za potvrdu.
- Refresh token se opoziva na serveru.
- Lokalni tokeni se uklanjaju.
- Korisnik se vraća u režim gosta.

### 3.10. Brisanje naloga

- Prikazuje se jasno upozorenje.
- Zahteva se ponovna potvrda identiteta.
- Nalog može biti privremeno deaktiviran pre trajnog brisanja.
- Povezani lični podaci brišu se ili anonimizuju prema politici
  čuvanja i važećim propisima.

Period od 14 dana iz početnog predloga treba potvrditi kao
konačnu poslovnu odluku i jasno objaviti korisniku.

## 4. API

- `GET /api/v1/me`
- `PATCH /api/v1/me`
- `GET /api/v1/me/preferences`
- `PATCH /api/v1/me/preferences`
- `GET /api/v1/me/stats`
- `POST /api/v1/me/avatar`
- `DELETE /api/v1/me/avatar`
- `POST /api/v1/me/devices`
- `POST /api/v1/me/change-password`
- `POST /api/v1/me/change-email`
- `POST /api/v1/auth/logout`
- `DELETE /api/v1/me`

## 5. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Podešavanja, aktivnost, uređaji i podaci profila |
| UX | Tok izmena, odjave i brisanja |
| UI | Avatar, statistika i komponente podešavanja |
| BE | Profil, preference, slike, statistika i nalog |
| FE | Ekran profila, forme i lokalna podešavanja |
| DO | Objektna memorija, push servis i monitoring |
