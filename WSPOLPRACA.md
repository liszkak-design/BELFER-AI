# Jak pracowac we dwoch na tym projekcie

## Najwazniejsza zasada

Cala strona to jeden plik `index.html`. Jesli obaj bedziecie edytowac go
rownoczesnie, Git zglosi konflikt i ktos bedzie musial recznie skladac zmiany.
Dlatego przed kazda sesja ustalcie, kto co robi.

Najbezpieczniejszy podzial:

| Osoba | Zakres |
|---|---|
| Krzysztof | `index.html` - tresc, sekcje, teksty |
| Kolega | `przyklad-scenariusz-belfer-ai.html`, `polityka-prywatnosci.html`, dokumentacja |

Jesli obaj musicie ruszac `index.html` - pracujcie na osobnych galeziach i nie
edytujcie tych samych sekcji.

## Dodanie kolegi do repozytorium

Settings -> Collaborators -> Add people -> wpisz nazwe uzytkownika lub e-mail
-> wybierz z listy -> Add ... to repository.

Uprawnienie **Write** wystarcza. Nie dawaj Admin. Kolega dostanie e-mail
z zaproszeniem; wygasa ono po 7 dniach.

## Kolega pobiera projekt

```
git clone https://github.com/liszkak-design/BELFER-AI.git
cd BELFER-AI
```

Przy pierwszym wysylaniu zmian GitHub poprosi o haslo - **nie podawaj hasla do
konta**. Trzeba wygenerowac token: Settings -> Developer settings -> Personal
access tokens -> Tokens (classic) -> Generate new token, zakres `repo`.
Token wkleja sie w miejsce hasla.

## Codzienny rytm pracy

Zawsze zacznij od pobrania zmian kolegi:

```
git pull
```

Utworz galez na swoja zmiane:

```
git checkout -b poprawka-cennika
```

Pracuj, a potem:

```
git add .
git commit -m "Cennik: nowe progi dla licencji placowkowych"
git push -u origin poprawka-cennika
```

Na GitHubie pojawi sie przycisk **Compare & pull request**. Kliknij, opisz
zmiane, wyslij. Druga osoba zaglada, komentuje i klika **Merge**. Po scaleniu:

```
git checkout main
git pull
git branch -d poprawka-cennika
```

## Gdy pojawi sie konflikt

Git wstawi w plik znaczniki:

```
<<<<<<< HEAD
twoja wersja
=======
wersja kolegi
>>>>>>> main
```

Otworz plik, zostaw wlasciwa tresc, usun wszystkie trzy linie ze znacznikami,
zapisz i wykonaj:

```
git add index.html
git commit -m "Rozwiazanie konfliktu"
```

Jesli konflikt jest w `index.html` i nie wiesz, co zostawic - otworz plik
w przegladarce po kazdej wersji i sprawdz, ktora dziala.

## Awaryjne cofniecie

Podglad ostatnich zmian:

```
git log --oneline -10
```

Powrot do stanu z konkretnego zapisu (bez kasowania historii):

```
git revert IDENTYFIKATOR
```

Porzucenie niezapisanych zmian w pliku:

```
git checkout -- index.html
```

## Konwencja nazw zapisow

Krotko, po polsku, z obszarem na poczatku:

```
Cennik: korekta progu dla licencji rocznej
Cookies: naprawa przyciskow banera
Scenariusz: dodanie zadania problemowego
Stopka: usuniecie pustej kolumny
```

Unikaj zapisow "poprawki", "zmiany", "update" - po miesiacu nikt nie bedzie
wiedzial, co sie w nich znalazlo.
