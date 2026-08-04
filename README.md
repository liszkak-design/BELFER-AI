# belfer-ai.pl

Strona docelowa produktu Belfer AI - asystenta nauczyciela opartego na polskiej podstawie programowej.

## Zawartosc repozytorium

| Plik | Opis |
|---|---|
| `index.html` | Cala strona glowna: HTML, CSS i JS w jednym pliku |
| `przyklad-scenariusz-belfer-ai.html` | Przykladowy pakiet dydaktyczny (scenariusz, karta pracy, sprawdzian) |
| `polityka-prywatnosci.html` | Polityka prywatnosci i cookies |
| `robots.txt` | Wersja podgladowa - patrz sekcja o GitHub Pages |
| `robots-produkcja.txt` | Wersja docelowa dla belfer-ai.pl (do podmiany przy publikacji) |
| `sitemap.xml` | Mapa strony dla domeny produkcyjnej |
| `.nojekyll` | Wylacza przetwarzanie Jekyllem na GitHub Pages |
| `TEST-BANERA.html` | Instrukcja testowania banera cookies |
| `COOKIES-INSTRUKCJA.txt` | Jak dodac analityke zgodnie z RODO |
| `WSPOLPRACA.md` | Zasady pracy dwoch osob na tym projekcie |

## Uwaga o strukturze

Strona jest jednym plikiem `index.html` (~122 KB) ze stylami w sekcji `<style>`
i skryptami w `<script>`. To upraszcza wgrywanie na hosting, ale utrudnia prace
dwoch osob jednoczesnie w tym samym pliku. Zasady podzialu pracy opisano
w `WSPOLPRACA.md`.

## Uruchomienie lokalne

Nie trzeba zadnych narzedzi - wystarczy otworzyc `index.html` w przegladarce.

Opcjonalnie lokalny serwer (przydatny do testow banera cookies):

```
python3 -m http.server 8000
```

Nastepnie otworz http://localhost:8000

## Podglad na GitHub Pages

Repozytorium jest przygotowane pod podglad, ktory NIE ma trafic do Google.

Wlaczenie - do wyboru jedna z dwoch drog. Settings -> Pages -> Source:

**A. GitHub Actions** (zalecane, dziala workflow `.github/workflows/pages.yml`)
Kazdy push do `main` automatycznie publikuje strone. Nic wiecej nie trzeba
ustawiac. Przebieg widac w zakladce Actions.

**B. Deploy from a branch**
Branch: `main`, katalog `/ (root)` -> Save. Wtedy plik workflow jest zbedny.

Po ok. 1-2 minutach strona jest pod adresem
`https://liszkak-design.github.io/BELFER-AI/`

### 404 na Pages - co sprawdzic

Najczestsza przyczyna: Source ustawiony na **GitHub Actions**, ale w repo nie
ma zadnego workflow - nie ma wiec czego opublikowac. Objaw: zakladka Actions
jest pusta, a lista deploymentow w srodowisku `github-pages` rowniez.
Rozwiazanie: workflow z tego repo (wariant A) albo przelaczenie na wariant B.

Uwaga: przy repozytorium prywatnym GitHub Pages wymaga planu platnego.
Wszystkie odnosniki w kodzie sa wzgledne, wiec praca w podkatalogu
`/BELFER-AI/` nie psuje nawigacji ani stylow.

### Blokada indeksowania

Podglad jest zabezpieczony na dwa sposoby:

- `<meta name="robots" content="noindex, nofollow, noarchive">` w **kazdym**
  pliku `.html` (`index`, `polityka-prywatnosci`, `przyklad-scenariusz`,
  `TEST-BANERA`)
- `robots.txt` bez wpisu `Sitemap`

W `robots.txt` celowo **nie ma** `Disallow: /`. Zakaz w tym pliku blokuje
pobranie strony, przez co Google nie odczytalby znacznika `noindex`
i moglby mimo wszystko pokazac sam adres w wynikach. Roboty musza wejsc,
przeczytac `noindex` i dopiero wtedy odpuscic.

Znacznik `canonical` nadal wskazuje na `https://belfer-ai.pl/` - to dodatkowy
sygnal, ze wersja z github.io jest tylko kopia robocza.

### Publikacja na belfer-ai.pl (odwrocenie blokady)

- [ ] usun `noindex` ze wszystkich plikow `.html` (szukaj frazy `noindex`)
- [ ] podmien `robots.txt` zawartoscia `robots-produkcja.txt`
- [ ] sprawdz `sitemap.xml` (adresy i daty `lastmod`)
- [ ] jesli domena bedzie inna niz `belfer-ai.pl`, podmien ja w `canonical`,
      `og:url`, `og:image`, `robots-produkcja.txt` i `sitemap.xml`

## Wdrozenie na wlasny hosting

Wgraj zawartosc katalogu przez FTP do `public_html/`. Strona nie wymaga
PHP, bazy danych ani Node. Szczegoly w `INSTRUKCJA-WGRANIA.txt`.

## Do uzupelnienia przed publikacja

- [ ] Dane firmy w `polityka-prywatnosci.html` (pola w nawiasach kwadratowych)
- [ ] Dostawca hostingu i narzedzia analitycznego w tabeli cookies
- [ ] Weryfikacja polityki prywatnosci przez prawnika
- [ ] Decyzja o imiennych opiniach w sekcji rekomendacji
- [ ] Sekcja o przetwarzaniu danych w samej aplikacji (po jej uruchomieniu)
