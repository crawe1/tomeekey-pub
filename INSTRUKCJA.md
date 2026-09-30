# Tomee Key — instrukcja

Tomee Key to sprzętowy klucz bezpieczeństwa USB. Zastępuje hasła i kody SMS:
logujesz się dotykiem klucza, a do serwisów, które wymagają kodów jednorazowych,
klucz sam wpisuje kod.

> **Pilot:** to wersja testowa. Dodawaj Tomee Key w serwisach jako **dodatkowy**
> sposób logowania i zachowaj dotychczasowy (telefon, kody zapasowe). Problemy zgłaszaj
> na biuro@tomee.pl.

## Spis treści

1. [Pierwsze uruchomienie](#1-pierwsze-uruchomienie)
2. [Logowanie kluczem w serwisach (passkeys)](#2-logowanie-kluczem-w-serwisach-passkeys)
3. [Kody jednorazowe (TOTP)](#3-kody-jednorazowe-totp)
4. [Klucze SSH](#4-klucze-ssh-dla-programistów)
5. [Aktualizacje](#5-aktualizacje)
6. [Co oznaczają diody](#6-co-oznaczają-diody)
7. [Gdy coś nie działa](#7-gdy-coś-nie-działa)

---

## 1. Pierwsze uruchomienie

1. Pobierz **Tomee Manager** (plik `.exe`, sekcja „Tomee Manager” w [README](README.md)) i uruchom go.
   Windows może pokazać „System Windows ochronił Twój komputer” — kliknij **Więcej informacji → Uruchom mimo to**.
   Program nie wymaga instalacji ani uprawnień administratora.
2. Podłącz klucz. Po kilku sekundach w oknie pojawi się jego numer i wersja.
3. Zakładka **PIN** → ustaw PIN (co najmniej 4 znaki). PIN chroni klucz, gdyby ktoś go znalazł.
   Zapamiętaj go — po 8 błędnych próbach klucz trzeba wyczyścić.
4. Tomee Manager zostaje w tle (ikona **T** przy zegarze) i uruchamia się razem z Windows.
   Zamknięcie okna nie wyłącza programu; całkiem wyłączysz go prawym klikiem na ikonie → **Zakończ**.

## 2. Logowanie kluczem w serwisach (passkeys)

Większość dużych serwisów (Google, Microsoft, GitHub, Apple, Allegro i inne) pozwala dodać klucz bezpieczeństwa:

1. W serwisie wejdź w ustawienia bezpieczeństwa i wybierz **dodaj klucz dostępu (passkey)** albo **klucz bezpieczeństwa**.
2. Gdy Windows zapyta, gdzie zapisać klucz, wybierz **klucz bezpieczeństwa / inne urządzenie**.
3. Podaj **PIN** klucza i **dotknij klucza**, gdy zamiga zielona dioda.

Od teraz przy logowaniu wybierasz klucz bezpieczeństwa, podajesz PIN i dotykasz klucza.
Listę zapisanych kont zobaczysz w Tomee Managerze w zakładce **Passkeys** (po podaniu PIN-u).

## 3. Kody jednorazowe (TOTP)

Klucz może zastąpić aplikację z kodami w telefonie (Google Authenticator itp.).

**Dodanie konta**

1. W serwisie włącz uwierzytelnianie **aplikacją**. Pojawi się kod QR — kliknij „nie możesz zeskanować?”, aby zobaczyć **klucz tekstowy**.
2. Tomee Manager → zakładka **Kody** → **Dodaj konto…** → wpisz nazwę (np. `GitHub:jan`) i wklej klucz tekstowy → **OK** → PIN.
3. Kod pojawi się na liście. Wpisz go w serwisie, żeby potwierdzić. **Zapisz kody zapasowe**, które serwis pokaże na koniec.

Wskazówka: zeskanuj ten sam kod QR także telefonem, zanim go potwierdzisz — telefon i klucz będą podawać te same kody (kopia zapasowa).

**Wpisywanie kodu dotykiem**

1. Tomee Manager → **Kody** → zaznacz konto → **Gest…** → wybierz np. **1 dotknięcie** (opcjonalnie „Naciśnij Enter po kodzie”).
2. Na stronie logowania kliknij w pole kodu i **dotknij klucza**. Kod wpisze się sam.

| Gest | Działanie |
|---|---|
| 1, 2 lub 3 dotknięcia | kod konta przypisanego do tego gestu |
| przytrzymanie ok. 2 s | kod konta przypisanego do przytrzymania |
| 4 dotknięcia | ten sam kod jeszcze raz (np. gdy wpisał się w złe pole) |

Do tego Tomee Manager musi działać (wystarczy ikona przy zegarze) — podaje kluczowi aktualny czas.
Kody możesz też skopiować z listy dwuklikiem.

## 4. Klucze SSH (dla programistów)

Tomee Manager → zakładka **SSH** → **Utwórz klucz SSH** → Windows poprosi o PIN i dotyk.
Klucz publiczny trafi do schowka — dodaj go na serwerze (`~/.ssh/authorized_keys`) albo w GitHub/GitLab → SSH keys.
Przy logowaniu przez `ssh` wystarczy dotknąć klucza. Na nowym komputerze użyj **Wczytaj z Tomee Key → Zapisz plik klucza**.

## 5. Aktualizacje

Tomee Manager sam sprawdza nowe wersje:

- **Nowy firmware klucza** — żółty przycisk „Dostępna aktualizacja” → **Pobierz i zainstaluj** → dotknij klucza. Klucz zrestartuje się (do ok. 15 s — nie odłączaj go). Konta, PIN i kody zostają.
- **Nowa wersja aplikacji** — przycisk „Nowa wersja aplikacji” → **Tak**. Program sam się podmieni.

## 6. Co oznaczają diody

| Dioda | Znaczenie |
|---|---|
| czerwona miga szybko przez ok. 3 s po podłączeniu | klucz się uruchamia — nie dotykaj go |
| zielona świeci | dotykasz klucza |
| zielona miga | klucz czeka na dotknięcie (logowanie, rejestracja, aktualizacja) |
| 2 zielone mrugnięcia | kod został wpisany |
| 3 czerwone mrugnięcia | kod nie został wpisany: gest nie ma przypisanego konta albo Tomee Manager nie działa |
| czerwona i zielona na zmianę | „Zidentyfikuj klucz” w aplikacji albo instalacja aktualizacji |
| czerwona świeci stale | błąd klucza — odłącz i podłącz; jeśli wraca, zgłoś problem |
| czerwona miga wolno bez końca | brak poprawnego firmware (np. przerwana aktualizacja) — zgłoś problem, klucz trzeba wgrać ponownie |

## 7. Gdy coś nie działa

| Problem | Rozwiązanie |
|---|---|
| Tomee Manager nie widzi klucza | podłącz klucz ponownie, najlepiej bezpośrednio do komputera (bez rozgałęźnika) |
| „Zbyt wiele błędnych prób z rzędu” | odłącz i podłącz klucz, spróbuj ponownie |
| Zapomniany PIN albo „PIN zablokowany” | jedyne wyjście to **Reset** w Tomee Managerze — kasuje wszystkie konta, kody i klucze SSH; potem zaloguj się do serwisów innym sposobem i dodaj klucz od nowa |
| Kod TOTP nie jest przyjmowany | sprawdź zegar Windows: Ustawienia → Czas i język → **Synchronizuj teraz** |
| Dotyk nie wpisuje kodu (3 czerwone mrugnięcia) | sprawdź, czy ikona **T** jest przy zegarze i czy konto ma przypisany gest |
| Zgubiony klucz | zaloguj się do serwisów innym sposobem (telefon, kody zapasowe) i usuń Tomee Key z ustawień bezpieczeństwa; zgłoś zgubienie |
