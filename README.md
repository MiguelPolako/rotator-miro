# 🎲 Rotator — losowanie karteczek na tablicy Miro

Dodatek do Miro, który losowo zamienia miejscami wybrane karteczki.

**Przykład:** na warsztatach przy każdym uczestniku leży karteczka z numerem grupy. Klikasz **Losuj!** — karteczki kilka razy przeskakują między osobami, coraz wolniej, aż zatrzymują się na końcowym wyniku. Wszyscy na tablicy oglądają to na żywo, a każdy ma przy sobie wylosowany numer grupy.

```
Przed:                         Po losowaniu:
Ania    [Grupa 1]              Ania    [Grupa 2]
Bartek  [Grupa 1]     🎲 →     Bartek  [Grupa 1]
Celina  [Grupa 2]              Celina  [Grupa 2]
Darek   [Grupa 2]              Darek   [Grupa 1]
```

---

## Jak korzystać

> Ta część zakłada, że dodatek jest już zainstalowany. Jeśli nie — zobacz [Instalacja](#instalacja) niżej.

**Otwórz dodatek:** na tablicy Miro, na pasku po lewej stronie kliknij **⋯** (więcej aplikacji) i wybierz **Rotator**. Po prawej otworzy się panel.

**Losowanie:**
1. Zaznacz karteczki, które mają się wymieszać. Najprościej: przytrzymaj `Shift` i klikaj kolejne albo zaznacz je myszką jak prostokątem. Panel pokaże, ile karteczek wybrałeś (muszą być co najmniej 2).
2. Kliknij **🎲 Losuj!**
3. Poczekaj kilka sekund, aż karteczki się zatrzymają. Panel napisze **Gotowe!**

**Ustawienia w panelu:**
- **Liczba przetasowań** — ile razy karteczki przeskoczą, zanim staną na wyniku (od 1 do 8). Więcej = dłuższe napięcie.
- **Tempo** — jak długo karteczki stoją między przeskokami. Każda kolejna przerwa jest trochę dłuższa, jak w zwalniającym kole fortuny.

**Cofnięcie:** **↩️ Przywróć układ sprzed losowania** ustawia karteczki tak, jak stały przed ostatnim losowaniem. Działa tylko dla ostatniego losowania i tylko dopóki panel jest otwarty.

**Pytania i odpowiedzi**

- **Czy ktoś może dostać tę samą karteczkę co wcześniej?** Tak — losowanie jest w pełni losowe, więc czasem ktoś zostanie przy swoim numerze.
- **Co się przesuwa razem z karteczką?** Wszystko: tekst, kolor i rozmiar. Zmienia się tylko miejsce.
- **Co mogę losować?** Karteczki (sticky notes), karty, kształty, teksty i obrazki. Ramki i linie są pomijane.
- **Panel pisze, że karteczki muszą być w tej samej ramce.** Wszystkie wybrane karteczki muszą leżeć w jednej ramce (frame) albo wszystkie poza ramkami. Przenieś je i spróbuj ponownie.
- **Ile karteczek naraz?** Do 200.
- **Karteczki przeskakują, a nie przesuwają się płynnie.** Tak działa Miro — efekt losowania dają kolejne przetasowania.

---

## Instalacja

Robisz to raz. Zajmie około 15 minut i nie wymaga znajomości programowania.

**Będzie potrzebne:** konto w Miro i przeglądarka Chrome (w Safari dodatek może nie działać).

### Krok 1. Pobierz pliki

1. Na górze tej strony na GitHubie kliknij zielony przycisk **Code**, a potem **Download ZIP**.
2. Otwórz pobrany plik ZIP. Powstanie folder **rotator-miro-main** — zapamiętaj, gdzie jest (zwykle w Pobranych).

### Krok 2. Udostępnij pliki dla Miro

Miro musi mieć skąd wczytać dodatek. Wybierz **jeden** sposób:

**Sposób A — w internecie, przez Netlify (zalecany).** Działa zawsze, także gdy Twój komputer jest wyłączony, na Macu i na Windowsie.

1. Wejdź na **https://app.netlify.com/drop** i załóż darmowe konto (bez konta strona po pewnym czasie zniknie).
2. Przeciągnij folder **rotator-miro-main** na stronę, w zaznaczone miejsce.
3. Po kilkunastu sekundach dostaniesz adres, np. `https://zielona-kostka-123.netlify.app`. **Skopiuj go** — przyda się w kroku 4.

**Sposób B — na własnym komputerze (tylko Mac).** Nic nie trafia do internetu, ale dodatek działa tylko wtedy, gdy masz otwarte okno Terminala.

1. Otwórz Terminal: `⌘ + Spacja`, wpisz „Terminal”, naciśnij Enter.
2. Wpisz `cd ` (z odstępem na końcu), przeciągnij folder **rotator-miro-main** do okna Terminala i naciśnij Enter.
3. Wpisz `python3 -m http.server 3001` i naciśnij Enter. Jeśli Mac zaproponuje instalację „narzędzi dla programistów” — zgódź się, poczekaj do końca i wpisz to polecenie jeszcze raz.
4. **Nie zamykaj okna Terminala.** Twój adres to `http://localhost:3001`.

Żeby później wyłączyć: w oknie Terminala naciśnij `Ctrl + C`. Przed kolejnym użyciem powtórz punkty 1–3.

> Używasz też dodatku Fog of War? Rotator celowo działa na numerze **3001**, a Fog of War na **3000**, żeby oba mogły działać jednocześnie (każdy w swoim oknie Terminala).

### Krok 3. Utwórz „Developer team” w Miro

Miro pozwala dodawać własne dodatki tylko w specjalnym zespole testowym (Developer team). Bez niego nie zobaczysz przycisku do tworzenia aplikacji.

1. Zaloguj się do Miro i wejdź na **https://miro.com/app/dashboard/?createDevTeam=1**
2. Zaznacz zgodę na regulamin i kliknij **Create team**.
3. Od razu pojawi się okno **Create new app** — wpisz nazwę **Rotator** i kliknij **Create app**.

> Masz już Developer team? Kliknij swoje zdjęcie w prawym górnym rogu → **Settings** → zakładka **Your apps** → **+ Create new app**.
>
> Konto firmowe (plan Enterprise)? Tam Developer team musi włączyć administrator firmy. Najprościej założyć darmowe prywatne konto Miro i zainstalować dodatek tam.

### Krok 4. Wklej ustawienia dodatku

1. Na stronie nowej aplikacji kliknij **Edit in Manifest**.
2. Usuń cały tekst z okienka i wklej ten poniżej. W wierszu z `sdkUri` wpisz **swój adres** z kroku 2:

```yaml
appName: Rotator
sdkVersion: SDK_V2
sdkUri: http://localhost:3001
scopes:
  - boards:read
  - boards:write
```

Jeśli wybrałeś sposób A, zamiast `http://localhost:3001` wpisz adres z Netlify, np. `sdkUri: https://zielona-kostka-123.netlify.app`.

> ⚠️ **Uwaga na odstępy.** Wiersze `appName`, `sdkVersion`, `sdkUri` i `scopes` muszą zaczynać się przy samej lewej krawędzi, bez spacji przed nimi. Wcięte są tylko dwa wiersze z myślnikiem. Jeśli Miro pokaże błąd `bad indentation`, usuń spacje na początku tych wierszy.

3. Kliknij **Save**.

### Krok 5. Dodaj ikonę (opcjonalnie)

Bez tego dodatek też działa, tylko ma ogólną ikonę.

Na stronie aplikacji znajdź pola **Outline icon** i **Color icon**. Z folderu **rotator-miro-main/icons** przeciągnij:
- `outline.svg` → na **Outline icon**
- `color.svg` → na **Color icon**

### Krok 6. Zainstaluj

1. Na dole strony aplikacji kliknij **Install app and get OAuth token**.
2. Wybierz zespół (jeśli widzisz tylko Developer team — wybierz go i korzystaj z dodatku na tablicach w tym zespole), kliknij **Install & authorize**, potem **Close**.
3. Otwórz tablicę w tym zespole i odśwież stronę. Dodatek znajdziesz pod **⋯** na pasku po lewej.

Gotowe — wróć do części [Jak korzystać](#jak-korzystać).

---

## Coś nie działa?

| Co widzisz | Co zrobić |
|---|---|
| Panel dodatku jest pusty albo pokazuje błąd | Sposób B: sprawdź, czy okno Terminala jest otwarte i czy adres `http://localhost:3001` otwiera się w przeglądarce. Sposób A: sprawdź, czy adres w `sdkUri` jest dokładnie taki jak z Netlify. |
| Nie ma przycisku **Create new app** | Zrób krok 3 (Developer team). |
| Błąd `bad indentation` przy zapisie | Usuń spacje na początku wierszy — patrz uwaga w kroku 4. |
| Nie widać dodatku na tablicy | Odśwież tablicę. Upewnij się, że tablica jest w tym samym zespole, w którym zainstalowałeś dodatek. |
| Panel pisze „Zaznacz co najmniej 2 karteczki” | Zaznacz karteczki na tablicy, zanim klikniesz **Losuj!** |
| W Safari nic się nie dzieje | Użyj Chrome. |

---

## Dla zainteresowanych: jak to działa

- `index.html` — wczytywany przez Miro w tle, otwiera panel po kliknięciu ikony.
- `app.html` — panel z przyciskami i cała logika.
- Dodatek zapamiętuje miejsca wybranych karteczek, losowo przydziela je od nowa i przesuwa karteczki przez Miro Web SDK v2. Robi to kilka razy z rosnącymi przerwami, a ostatnie losowanie jest wynikiem.
