Ekran Filteri

## 1. Svrha

Filteri omogućavaju korisniku da suzi rezultate pretrage
prema kategoriji, autoru, dužini citata i drugim kriterijumima.

Filteri se prikazuju u panelu koji izlazi sa dna ekrana
(bottom sheet).

## 2. Elementi interfejsa

1. Naslov Filteri i dugme Zatvori.
2. Izbor kategorija.
3. Polje za izbor autora.
4. Izbor dužine citata.
5. Sortiranje rezultata.
6. Prekidač Samo moji omiljeni.
7. Dugme Resetuj.
8. Dugme Primeni (N rezultata).

## 3. Kategorija

Dostupne kategorije:

- Vera
- Sport
- Život
- Ljubav

Moguć je izbor više kategorija.
Ako nijedna kategorija nije izabrana, pretražuju se sve kategorije.

## 4. Autor

- Korisnik može da pretražuje autore.
- Prikazuju se predlozi do 20 autora.
- Moguće je izabrati više autora.
- Izabrani autori prikazuju se kao čipovi.
- Svaki čip ima opciju uklanjanja.

## 5. Dužina citata

Dostupne su tri opcije:

- Kratki: manje od 100 karaktera.
- Srednji: od 100 do 200 karaktera.
- Dugi: više od 200 karaktera.

Granice treba definisati precizno i primeniti dosledno
u klijentskoj aplikaciji i na serveru.

## 6. Sortiranje

Korisnik može da izabere:

- Relevantnost.
- Najnovije.
- Najpopularnije.
- Autor A–Ž.

Kada postoji tekst pretrage, podrazumevano sortiranje je
po relevantnosti. Kada nema teksta, podrazumevano je
sortiranje po popularnosti.

## 7. Samo moji omiljeni

- Dostupno je samo prijavljenim korisnicima.
- Filtrira rezultate na citate koje je korisnik sačuvao.
- Gost dobija poruku da je potrebna prijava.

## 8. Pravila kombinovanja filtera

Između različitih vrsta filtera primenjuje se logika I.

Primer:

Kategorija Sport I autor određene osobe I kratki citati.

Unutar iste vrste filtera primenjuje se logika ILI.

Primer:

Kategorija Vera ILI Sport.

Ako nije izabrana nijedna vrednost određene vrste,
taj filter se ne primenjuje.

## 9. Primeni i Resetuj

### Primeni

- Prikazuje broj rezultata za trenutno izabrane filtere.
- Zatvara panel i osvežava listu.
- Vraća listu rezultata na vrh.
- Prikazuje aktivne filtere kao čipove.

Ako broj rezultata iznosi nula, dugme može biti onemogućeno
uz jasnu poruku Nema rezultata.

### Resetuj

- Briše sve izabrane filtere.
- Ne menja tekst pretrage.
- Ostaje otvoren panel.
- Dugme je onemogućeno ako nema aktivnih filtera.

### Zatvaranje panela

Zatvaranjem bez primene odbacuju se privremene izmene.

## 10. Tehnička implementacija

Klijent čuva privremeno stanje filtera.
Promene se primenjuju tek nakon pritiska na Primeni.

Broj rezultata osvežava se uz debounce od 300 ms.

API prima sledeće parametre:

- `category`
- `author`
- `length`
- `sort`
- `favorites_only`
- `q`
- `page`
- `limit`

## 11. API

- `GET /api/v1/quotes/search`
- `GET /api/v1/quotes/count`
- `GET /api/v1/authors`

Server validira sve parametre i vraća grešku 400 za
neispravne ili nepodržane vrednosti.

## 12. Odgovornosti tima

| Uloga | Zaduženja |
|---|---|
| DB | Kolone text_length i favorites_count, indeksi i optimizacija upita |
| UX | Logika filtera, broj rezultata, primena i resetovanje |
| UI | Bottom sheet, čipovi, izbor dužine i sortiranje |
| BE | Parametri filtera, endpointi za pretragu i broj rezultata |
| FE | Privremeno stanje, debounce, čipovi i primena filtera |
| DO | Keširanje, monitoring, usklađivanje brojača i k6 testovi |

## 13. Testiranje

Potrebno je proveriti:

- Jedan aktivan filter.
- Više filtera različitih vrsta.
- Više izabranih kategorija ili autora.
- Nula rezultata.
- Resetovanje filtera.
- Zatvaranje bez primene.
- Gosta koji pokušava da koristi filter omiljenih.
- Ispravnost broja rezultata i paginacije.
