# Model baze podataka

## 1. Pregled

Predložena glavna baza podataka je PostgreSQL.
Model obuhvata korisnike, citate, autore, kategorije,
omiljene citate, podešavanja i pomoćne podatke.

Primarni ključevi, strani ključevi, ograničenja i indeksi
definišu se kroz verzionisane migracije.

## 2. Tabele

### 2.1. users

Čuva podatke o korisnicima.

- id: UUID, primarni ključ
- email: jedinstvena email adresa
- password_hash: heš lozinke, može biti NULL za naloge
  koji koriste isključivo spoljnog provajdera
- display_name: ime za prikaz
- avatar_url: URL slike profila
- auth_provider: email, Google ili Apple
- provider_user_id: identifikator kod spoljnog provajdera
- email_verified: status potvrde emaila
- is_active: status naloga
- terms_accepted_at: vreme prihvatanja uslova
- terms_version: verzija prihvaćenih uslova
- created_at, updated_at, last_login_at
- deleted_at: vreme soft brisanja naloga

### 2.2. categories

Čuva kategorije citata.

- id
- slug: vera, sport, zivot ili ljubav
- name
- icon
- color
- sort_order

### 2.3. authors

Čuva podatke o autorima.

- id
- name
- bio: opciona biografija

### 2.4. quotes

Čuva citate.

- id
- text
- author_id
- category_id
- language
- source
- is_published
- text_length
- favorites_count
- created_at
- updated_at

`author_id` i `category_id` su strani ključevi.
`text_length` predstavlja broj karaktera citata.
`favorites_count` predstavlja broj omiljenih sačuvanih citata.

### 2.5. daily_quotes

Čuva dnevne citate.

- id
- date
- category_id
- quote_id

Kombinacija `date` i `category_id` mora biti jedinstvena,
kako bi za svaki dan i kategoriju postojao jedan dnevni citat.

### 2.6. favorites

Povezuje korisnike i omiljene citate.

- user_id
- quote_id
- created_at

Kombinacija `user_id` i `quote_id` mora biti jedinstvena.

### 2.7. tags

- id
- name

### 2.8. quote_tags

Povezuje citate i oznake.

- quote_id
- tag_id

### 2.9. user_preferences

Čuva korisnička podešavanja.

- user_id
- default_category_id
- notifications_enabled
- notification_time
- theme
- language
- timezone

### 2.10. refresh_tokens

Čuva podatke o sesijama za obnovu prijave.

- id
- user_id
- token_hash
- device_info
- expires_at
- revoked_at

### 2.11. password_resets

Čuva zahteve za resetovanje lozinke.

- id
- user_id
- token_hash
- expires_at
- used_at

### 2.12. email_verifications

Čuva tokene za potvrdu email adrese.

- id
- user_id
- token_hash
- expires_at
- used_at

### 2.13. search_history

Čuva istoriju pretrage prijavljenog korisnika.

- id
- user_id
- query
- created_at

Čuva se najviše 10 najnovijih upita po korisniku.

### 2.14. quote_shares

Beleži deljenje citata.

- id
- quote_id
- user_id: može biti NULL za gosta
- channel
- created_at

### 2.15. devices

Čuva uređaje za push obaveštenja.

- id
- user_id
- push_token
- platform: Android ili iOS

### 2.16. user_activity

Čuva dnevnu aktivnost korisnika.

- user_id
- date

Kombinacija `user_id` i `date` treba da bude jedinstvena.

## 3. Veze između tabela

- Jedan autor može imati više citata.
- Jedna kategorija može sadržati više citata.
- Jedan korisnik može imati više omiljenih citata.
- Jedan citat može biti omiljen kod više korisnika.
- Citat može imati više oznaka.
- Jedan korisnik ima svoja podešavanja.
- Jedan korisnik može imati više uređaja i sesija.
- Dnevni citat povezuje datum, kategoriju i citat.

## 4. Važni indeksi i ograničenja

- Jedinstveni indeks nad normalizovanim emailom.
- GIN indeks nad vektorom za full-text pretragu citata.
- Indeks za pretragu autora.
- Indeks nad `quotes.category_id`.
- Indeks nad `favorites(user_id, created_at DESC)`.
- Jedinstveni indeks nad `favorites(user_id, quote_id)`.
- Jedinstveni indeks nad `daily_quotes(date, category_id)`.
- Indeks nad `quotes(text_length)`, ako ga upiti opravdavaju.
- Indeks nad `quotes(favorites_count)`, ako se koristi za sortiranje.
- Indeks nad `user_activity(user_id, date)`.

Za pretragu bez dijakritika može se koristiti PostgreSQL
ekstenzija `unaccent`, a za toleranciju na greške `pg_trgm`.

## 5. Održavanje podataka

- Sve promene šeme sprovode se migracijama.
- Lozinke i reset tokeni ne čuvaju se u otvorenom tekstu.
- Brojači omiljenih citata moraju ostati usklađeni sa tabelom
  `favorites`.
- Brisanje naloga mora obuhvatiti povezane lične podatke.
- Rezervne kopije moraju se redovno praviti i testirati.
- Pravila čuvanja podataka moraju biti definisana dokumentacijom.

## 6. Napomene

Ovo je logički model baze podataka. Pre implementacije treba
definisati konkretne SQL tipove, pravila brisanja stranih
ključeva, migracije i strategiju održavanja izračunatih kolona.
