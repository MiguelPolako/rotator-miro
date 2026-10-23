# 🎲 Rotator — dodatek do Miro

Losowo zamienia miejscami zaznaczone karteczki. Przykład: na warsztatach przy każdej osobie leży karteczka z numerem grupy — po kliknięciu „Losuj!” karteczki kilka razy się tasują, zwalniają i zatrzymują na wyniku końcowym. Wszyscy uczestnicy tablicy widzą tasowanie na żywo.

## Funkcjonalność

- **Losuj!** — zaznaczone karteczki zamieniają się pozycjami (x/y). Kolor, treść i rozmiar jadą razem z karteczką.
- **Liczba przetasowań** (1–8, domyślnie 3) — ile razy karteczki przeskoczą, zanim staną na wyniku. Każda kolejna pauza jest dłuższa (efekt zwalniającego koła).
- **Tempo** — długość pierwszej pauzy (200–1500 ms).
- **Pełna losowość** — wynik końcowy to zwykłe losowanie, więc ktoś może dostać tę samą karteczkę lub ten sam numer.
- **Przywróć układ** — cofa ostatnie losowanie.

Działa z karteczkami (sticky notes), kartami, kształtami, tekstami i obrazkami. Ramki i linie są pomijane.

## Ograniczenia

- Wszystkie karteczki muszą leżeć w tej samej ramce (albo wszystkie poza ramkami). Pozycje w ramce Miro liczy względem ramki, więc zamiana między ramkami jest blokowana.
- Miro nie animuje przesuwania — karteczki przeskakują, a efekt „losowania” dają kolejne przetasowania z pauzami.
- Maksymalnie 200 obiektów naraz (limit zapytań Miro Web SDK: 100 000 kredytów/min, każde przesunięcie = 50).
- „Przywróć układ” pamięta tylko ostatnie losowanie i tylko dopóki panel jest otwarty.

## Uruchomienie

Ten sam serwer, co dla Fog of War (z folderu nadrzędnego):

```
cd /Users/michalpolak/miro
python3 -m http.server 3000
```

W Miro utwórz **osobną** aplikację (Ustawienia → Your apps → Create new app → Edit in Manifest), tak jak w `../SETUP.md`, ale z tym manifestem:

```yaml
appName: Rotator
sdkVersion: SDK_V2
sdkUri: http://localhost:3000/rotator/
scopes:
  - boards:read
  - boards:write
```

Potem: Install app → otwórz tablicę → ikona aplikacji na lewym pasku → zaznacz karteczki → **Losuj!**
