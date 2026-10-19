# Arhitektura aplikacije Dnevni citati

- Autor: arhitekta projekta
- Verzija: 1.0
- Status: za pregled tima

## 1. Pregled sistema

Aplikacija Dnevni citati korisnicima omogućava prikaz jednog
dnevnog citata iz izabrane kategorije. Korisnici mogu da
pregledaju dodatne citate, pretražuju sadržaj, koriste filtere,
čuvaju omiljene citate i upravljaju svojim profilom.

Kategorije citata su:

- Vera
- Sport
- Život
- Ljubav

Aplikacija podržava goste i registrovane korisnike.

## 2. Glavni moduli

### 2.1. Korisnička aplikacija

Obuhvata ekrane, navigaciju, prikaz citata, pretragu, filtere,
upravljanje profilom i lokalno čuvanje određenih podataka.

### 2.2. Back end

Obrađuje API zahteve, autentikaciju, poslovnu logiku,
pretragu, omiljene citate, profil i slanje obaveštenja.

### 2.3. Baza podataka

Čuva korisnike, citate, autore, kategorije, omiljene citate,
podešavanja, istoriju pretrage i podatke potrebne za autentikaciju.

### 2.4. Infrastruktura

Obuhvata pokretanje aplikacije, okruženja, automatizovano
testiranje i objavljivanje, keširanje, monitoring i rezervne kopije.

## 3. Predložena tehnologija

| Deo sistema | Predlog |
|---|---|
| Mobilna aplikacija | React Native ili Flutter |
| Back end | Node.js i NestJS |
| API | REST, JSON |
| Glavna baza | PostgreSQL |
| Keš | Redis |
| Autentikacija | JWT access i refresh tokeni |
| Kontejnerizacija | Docker |
| CI/CD | GitHub Actions ili GitLab CI |
| Monitoring grešaka | Sentry |
| Monitoring infrastrukture | Prometheus i Grafana |
| Push obaveštenja | Firebase Cloud Messaging i APNs |

Ovo je predložena tehnologija, a ne konačna odluka.
Izbor zavisi od potreba projekta i znanja tima.

## 4. Arhitektura komunikacije

1. Korisnik pokreće akciju u aplikaciji.
2. Klijentska aplikacija šalje HTTP zahtev ka API-ju.
3. Back end proverava zahtev, prava pristupa i podatke.
4. Po potrebi se izvršava upit nad bazom ili kešom.
5. Back end vraća JSON odgovor.
6. Aplikacija prikazuje rezultat korisniku.

Javni endpointi omogućavaju pristup sadržaju bez prijave.
Endpointi za profil i omiljene citate zahtevaju autentikaciju.

## 5. Standardi API-ja

- Osnovna putanja: `/api/v1`.
- Format podataka: JSON.
- Predloženi format odgovora: `data`, `error` i `meta`.
- Validacija ulaznih podataka obavlja se i na serveru.
- Endpointi se štite odgovarajućim ograničenjem broja zahteva.
- Zaštićeni endpointi proveravaju identitet i prava korisnika.
- Greške se vraćaju u doslednom formatu.

## 6. Globalni UX/UI standardi

- Dosledan dizajn svih ekrana.
- Mreža razmaka zasnovana na 8 px.
- Minimalna dodirna površina dugmadi od 44 × 44 px.
- Podrška za svetlu i tamnu temu.
- Kontrast u skladu sa WCAG AA smernicama.
- Jasna stanja učitavanja, greške i praznog sadržaja.
- Poruka za slučaj gubitka internet veze.
- Vidljive povratne informacije nakon korisničkih akcija.

## 7. Stanja aplikacije

Svaki ekran treba da definiše sledeća stanja:

- Učitavanje: prikaz skeleton elemenata ili indikatora.
- Uspeh: prikaz traženih podataka.
- Prazno stanje: poruka i predlog sledeće akcije.
- Greška: objašnjenje i opcija za ponovni pokušaj.
- Offline: prikaz lokalno sačuvanih podataka kada su dostupni.
- Gost: ograničenja funkcija koje zahtevaju korisnički nalog.

## 8. Bezbednost

- Komunikacija sa serverom koristi HTTPS.
- Lozinke se nikada ne čuvaju u otvorenom tekstu.
- Za heširanje lozinki koristi se Argon2id ili odgovarajuća
  bezbedna konfiguracija bcrypt algoritma.
- Refresh tokeni se čuvaju u obliku heša na serveru.
- Mobilna aplikacija čuva tokene u sigurnom skladištu.
- Tajne i pristupni ključevi ne smeju biti u repozitorijumu.
- Osetljivi podaci ne smeju se upisivati u logove.
- Potrebni su rate limiting, validacija i kontrola pristupa.

## 9. Okruženja i održavanje

Predviđena su tri okruženja:

- Development
- Staging
- Production

Migracije baze moraju biti verzionisane.
Produkcija zahteva rezervne kopije, proveru mogućnosti vraćanja
podataka, monitoring i proceduru za oporavak od greške.

## 10. Otvorene arhitektonske odluke

- Da li aplikacija podržava samo srpski ili više jezika?
- Odakle dolaze citati i ko odobrava sadržaj?
- Da li će postojati web verzija?
- Da li je potreban administratorski panel?
- Da li je dnevni citat isti za sve korisnike?
- Koje tehnologije će tim konačno izabrati?
