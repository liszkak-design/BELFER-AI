# belfer-ai.pl

Strona docelowa produktu Belfer AI - asystenta nauczyciela opartego na polskiej podstawie programowej.

## Zawartosc repozytorium

| Plik | Opis |
|---|---|
| `index.html` | Cala strona glowna: HTML, CSS i JS w jednym pliku |
| `przyklad-scenariusz-belfer-ai.html` | Przykladowy pakiet dydaktyczny (scenariusz, karta pracy, sprawdzian) |
| `polityka-prywatnosci.html` | Polityka prywatnosci i cookies |
| `robots.txt`, `sitemap.xml` | Pliki dla wyszukiwarek |
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

## Wdrozenie

Wgraj zawartosc katalogu na hosting przez FTP albo wlacz GitHub Pages:
Settings -> Pages -> Deploy from a branch -> main -> / (root).

Uwaga: przy repozytorium prywatnym GitHub Pages wymaga planu platnego.

## Do uzupelnienia przed publikacja

- [ ] Dane firmy w `polityka-prywatnosci.html` (pola w nawiasach kwadratowych)
- [ ] Dostawca hostingu i narzedzia analitycznego w tabeli cookies
- [ ] Weryfikacja polityki prywatnosci przez prawnika
- [ ] Decyzja o imiennych opiniach w sekcji rekomendacji
- [ ] Sekcja o przetwarzaniu danych w samej aplikacji (po jej uruchomieniu)
