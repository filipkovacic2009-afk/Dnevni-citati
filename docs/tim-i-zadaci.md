Odgovornosti članova tima

## 1. Uloge

| Skraćenica | Uloga |
|---|---|
| DB | Dizajner/administrator baze podataka |
| UX | UX dizajner |
| UI | UI dizajner |
| BE | Back end developer |
| FE | Front end / mobilni developer |
| DO | DevOps inženjer |

Ako ista osoba obavlja UX i UI poslove, te odgovornosti
mogu se spojiti.

## 2. DB — baza podataka

- Projektuje šemu baze podataka.
- Definiše primarne i strane ključeve.
- Priprema migracije.
- Projektuje indekse za pretragu i filtriranje.
- Održava podatke o omiljenim citatima.
- Definiše transakcije za registraciju.
- Planira rezervne kopije i testove vraćanja podataka.
- Učestvuje u definisanju pravila brisanja i čuvanja podataka.

## 3. UX — korisničko iskustvo

- Definiše tokove gosta i prijavljenog korisnika.
- Organizuje navigaciju između ekrana.
- Definiše ponašanje dugmadi i formi.
- Priprema poruke grešaka i praznih stanja.
- Definiše pravila validacije i povratne informacije.
- Proverava pristupačnost i jednostavnost korišćenja.
- Testira da li korisnik može da završi zadatke bez zabune.

## 4. UI — korisnički interfejs

- Priprema dizajn sistem.
- Definiše boje kategorija i tipografiju.
- Dizajnira kartice citata, dugmad, polja i navigaciju.
- Priprema svetlu i tamnu temu.
- Definiše stanja komponenti.
- Priprema ikone, animacije i prilagodljive rasporede.
- Vodi računa o kontrastu i veličini dodirnih površina.

## 5. BE — back end

- Implementira REST API.
- Implementira registraciju i prijavu.
- Proverava i izdaje tokene.
- Implementira pretragu i filtere.
- Implementira upravljanje omiljenim citatima.
- Implementira profil i korisnička podešavanja.
- Implementira resetovanje lozinke i potvrdu emaila.
- Implementira zakazane poslove i push obaveštenja.
- Obezbeđuje validaciju, autorizaciju i obradu grešaka.

## 6. FE — mobilna aplikacija

- Implementira navigaciju i ekrane.
- Povezuje aplikaciju sa API-jem.
- Implementira validaciju formi.
- Održava stanje prijave i korisničkih podešavanja.
- Implementira čuvanje omiljenih citata.
- Implementira pretragu i filtere.
- Implementira kopiranje i deljenje citata.
- Implementira offline prikaz dostupnih keširanih podataka.
- Implementira push dozvole i upravljanje temom.

## 7. DO — infrastruktura

- Podešava development, staging i production okruženja.
- Priprema Docker konfiguraciju.
- Podešava CI/CD.
- Upravlja tajnama i pristupnim ključevima.
- Podešava HTTPS, logovanje i monitoring.
- Podešava rezervne kopije i proceduru oporavka.
- Obezbeđuje skaliranje i stabilnost servisa.
- Podešava keširanje, alarme i testiranje opterećenja.

## 8. Odgovornosti po ekranima

| Ekran | Glavne odgovornosti |
|---|---|
| Home | DB: citati; UX/UI: kartica i tok; BE: dnevni citat; FE: prikaz i akcije; DO: keš |
| Log in | DB: korisnici i tokeni; UX/UI: forma; BE: autentikacija; FE: prijava; DO: bezbednost |
| Sign up | DB: korisnik i preference; UX/UI: registracija; BE: kreiranje naloga; FE: validacija; DO: email servis |
| Profil | DB: preference i aktivnost; UX/UI: podešavanja; BE: profil; FE: forme; DO: storage i push |
| Pretraga | DB: indeksi; UX/UI: rezultati; BE: upiti; FE: lista i debounce; DO: monitoring |
| Filteri | DB: indeksi i brojači; UX/UI: logika i panel; BE: filteri; FE: primena; DO: keš i testovi |

## 9. Saradnja i kontrola kvaliteta

- Zajedničke odluke o API-ju dokumentuju se pre implementacije.
- Promene baze rade se preko migracija.
- Promene koda proveravaju se kroz pull request.
- Svaka funkcionalnost mora imati definisane kriterijume
  prihvatanja i odgovarajuće testove.
- Greške se evidentiraju i rešavaju prema prioritetu.Odgovornosti članova tima

