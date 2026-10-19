# 1. Opis projekta

Dnevni citati je aplikacija koja korisnicima svakog dana prikazuje
citat iz izabrane kategorije. Cilj aplikacije je da korisnicima
omogući jednostavan pristup inspirativnim citatima i njihovo
čuvanje, pretraživanje i deljenje.

## 2. Glavne funkcionalnosti

- Prikaz dnevnog citata.
- Izbor kategorije: Vera, Sport, Život i Ljubav.
- Prikaz dodatnih nasumičnih citata.
- Pretraga citata po tekstu i autoru.
- Filtriranje po kategoriji, autoru, dužini i drugim kriterijumima.
- Registracija i prijava korisnika.
- Čuvanje i pregled omiljenih citata.
- Upravljanje profilom i podešavanjima.
- Dnevna push obaveštenja.
- Kopiranje i deljenje citata.

## 3. Predložene tehnologije

- Klijentska aplikacija: React Native ili Flutter.
- Back end: Node.js sa NestJS okvirom.
- Baza podataka: PostgreSQL.
- Keširanje: Redis.
- API: REST API sa JSON formatom.
- Autentikacija: access i refresh tokeni.
- Infrastruktura: Docker i CI/CD.
- Monitoring: Sentry i Prometheus/Grafana.

Konačan izbor tehnologija biće potvrđen tokom planiranja projekta.

## 4. Struktura dokumentacije

- [Arhitektura sistema](docs/arhitektura.md)
- [Model baze podataka](docs/baza-podataka.md)
- [Pregled API-ja](docs/api.md)
- [Home page](docs/ekrani/home.md)
- [Prijava korisnika](docs/ekrani/login.md)
- [Registracija korisnika](docs/ekrani/registracija.md)
- [Profil korisnika](docs/ekrani/profil.md)
- [Pretraga citata](docs/ekrani/pretraga.md)
- [Filteri](docs/ekrani/filteri.md)
- [Odgovornosti tima](docs/tim-i-zadaci.md)
- [Plan razvoja](docs/plan-razvoja.md)

## 5. Korisnički režimi

Aplikacija podržava dva režima:

- Gost: može da pregleda, pretražuje, filtrira i deli citate.
- Prijavljeni korisnik: ima pristup i omiljenim citatima,
  profilu, podešavanjima i personalizovanim obaveštenjima.

## 6. Status projekta

Projekat je u fazi planiranja i definisanja arhitekture.
Tehnologije, funkcionalnosti i detalji implementacije mogu
se menjati nakon pregleda i dogovora tima.

## 7. Autorstvo

Autor dokumentacije: arhitekta projekta.

Verzija dokumentacije: 1.0

Status: za pregled tima.
