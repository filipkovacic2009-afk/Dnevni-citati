Ekran Pretraga

## 1. Svrha

Omogućava pronalaženje citata prema tekstu, autoru i kategoriji.
Rezultati se mogu dodatno suziti pomoću filtera.

## 2. Elementi interfejsa

1. Polje za pretragu.
2. Dugme za brisanje teksta.
3. Dugme Otkaži ili Nazad.
4. Dugme Filteri sa brojem aktivnih filtera.
5. Čipovi aktivnih filtera.
6. Nedavne pretrage.
7. Predlozi dok korisnik kuca.
8. Lista rezultata.
9. Prazno stanje Nema rezultata.

## 3. Pretraga

- Pretraga se pokreće nakon najmanje dva karaktera.
- Automatski fokus se postavlja pri otvaranju ekrana.
- Debounce za glavno polje iznosi 400 ms.
- Prethodni zahtev se otkazuje kada je to moguće.
- Stariji odgovor ne sme prepisati novije rezultate.
- Podržava se pretraga po tekstu citata i imenu autora.
- Pretraga treba da podrži reči sa i bez dijakritika.

Primer: upiti „zivot“ i „život“ treba da daju
odgovarajuće ekvivalentne rezultate.

## 4. Brisanje i otkazivanje

- Dugme X briše tekst i vraća nedavne pretrage.
- Aktivni filteri ostaju sačuvani.
- Dugme Otkaži zatvara ekran i vraća prethodnu stranicu.

## 5. Nedavne pretrage

- Prikazuje se do deset poslednjih upita.
- Dodir na upit ponavlja pretragu.
- Korisnik može obrisati pojedinačan upit ili celu istoriju.
- Gosti imaju lokalnu istoriju.
- Prijavljeni korisnici mogu sinhronizovati istoriju sa serverom.
- Istorija se čuva samo u obimu koji je potreban za funkciju.

## 6. Predlozi

- Predlozi se pojavljuju nakon dva karaktera.
- Prikazuje se najviše pet predloga.
- Predlozi obuhvataju autore i popularne fraze.
- Debounce za predloge iznosi 250 ms.
- Predlozi se prikazuju dok je polje fokusirano.

## 7. Rezultati pretrage

Svaka kartica sadrži:

- Tekst citata.
- Autora.
- Kategoriju.
- Dugme Sačuvaj.
- Dugme Podeli.

Dodir na autora pokreće pretragu tog autora.
Lista koristi virtuelizaciju i paginaciju radi performansi.

## 8. Prazno stanje

Ako nema rezultata, prikazuje se poruka:

„Nema rezultata za ovaj upit.“

Korisniku se predlaže da promeni reči ili ukloni filtere.

Dostupno je dugme Ukloni filtere.

## 9. API

- `GET /api/v1/quotes/search`
- `GET /api/v1/search/suggestions`
- `GET /api/v1/me/search-history`
- `POST /api/v1/me/search-history`
- `DELETE /api/v1/me/search-history/{id}`
- `DELETE /api/v1/me/search-history`

Pretraga citata dostupna je gostima. Istorija na serveru
zahteva autentikaciju.

## 10. Performanse

- PostgreSQL full-text pretraga.
- `unaccent` za rad sa dijakriticima.
- `pg_trgm` za toleranciju na greške u kucanju.
- Redis keš za česte upite kada je opravdano.
- Monitoring sporih upita i optimizacija indeksa.

## 11. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Full-text indeksi i istorija pretrage |
| UX | Tok pretrage, predlozi i prazna stanja |
| UI | Polje, filteri i kartice rezultata |
| BE | Pretraga, predlozi, istorija i paginacija |
| FE | Debounce, lista i korisničke interakcije |
| DO | Keširanje, monitoring i testovi performansi |
