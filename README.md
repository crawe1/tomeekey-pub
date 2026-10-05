# Tomee Key

Pliki do pobrania dla klucza zabezpieczeń Tomee Key.

**Jak zacząć i jak używać klucza: [INSTRUKCJA.md](INSTRUKCJA.md)** · [wersja PDF do wydruku](INSTRUKCJA.pdf)

Parametry, standardy i architektura bezpieczeństwa: [SPECYFIKACJA.md](SPECYFIKACJA.md) · [wersja PDF](SPECYFIKACJA.pdf)

## Tomee Manager (Windows)

Aplikacja do zarządzania kluczem: PIN, passkeys, klucze SSH i aktualizacje firmware. Nie wymaga instalacji ani uprawnień administratora — pobierz plik `.exe` i uruchom.

**Najnowsza wersja: [0.4.0](manager/0.4.0/TomeeManager-0.4.0.exe)** (2026-10-05)

Plik nie ma jeszcze cyfrowego podpisu wydawcy, więc Windows SmartScreen może wyświetlić ostrzeżenie („Więcej informacji” → „Uruchom mimo to”). Przed uruchomieniem możesz porównać sumę SHA-256 z tabelą.

| Wersja | Data | SHA-256 | Zmiany |
|---|---|---|---|
| [0.4.0](manager/0.4.0/TomeeManager-0.4.0.exe) | 2026-10-05 | `9af60a55e0bc68c2…` | Obsługa kluczy z izolacją TrustZone (firmware 0.15.0): Manager rozpoznaje rodzaj klucza, proponuje właściwe aktualizacje (aplikacja i usługi bezpieczne) i pokazuje wersję usług bezpiecznych; klucze bez TrustZone nadal dostają firmware 0.14.x |
| [0.3.0](manager/0.3.0/TomeeManager-0.3.0.exe) | 2026-09-30 | `07438617857d7b7a…` | Kody TOTP (zakładka Kody), wpisywanie kodów gestami dotyku, praca w tle przy zegarze i autostart z Windows, automatyczne ustawianie czasu na kluczu, aktualizacje aplikacji |
| [0.2.0](manager/0.2.0/TomeeManager-0.2.0.exe) | 2026-09-29 | `a6d3da7fd71eddcf…` | Pierwsze wydanie: informacje o kluczu, PIN, passkeys, klucze SSH, aktualizacje firmware z internetu, reset |

## Firmware

Podpisane obrazy firmware. Tomee Manager sam sprawdza nowe wersje i proponuje instalację; plik `.bin` można też wybrać ręcznie w zakładce Firmware. Klucz sprawdza podpis i nie przyjmie pliku z niższą wersją bezpieczeństwa niż zainstalowana.

| Wersja | Wersja bezpieczeństwa | Data | SHA-256 | Zmiany |
|---|---|---|---|---|
| [0.14.4](firmware/0.14.4/tomee-key-0.14.4.bin) | 6 | 2026-10-02 | `2acc6a435f3024e7…` | Stabilność: poprawne opóźnienia odczytu pamięci Flash przy zegarze 16 MHz (zgodnie ze specyfikacją producenta układu); bootloader nowych kluczy dwukrotnie sprawdza podpis firmware (odporność na zakłócenia) i uruchamia się szybciej |
| [0.14.3](firmware/0.14.3/tomee-key-0.14.3.bin) | 6 | 2026-10-02 | `e8d517f65b73b8ec…` | Niezawodność zapisu: kod HOTP nie może zostać wydany dwa razy, a passkey nie zostaje zdublowany po wyjęciu klucza w trakcie zapisu; zapis do obszaru bootloadera i firmware zablokowany w aplikacji; kontrola zakresu każdego zapisu do pamięci Flash |
| [0.14.1](firmware/0.14.1/tomee-key-0.14.1.bin) | 6 | 2026-09-30 | `b912945991ea0ee2…` | Bezpieczniejszy dotyk: przytrzymanie wpisuje kod dopiero po puszczeniu palca (1,5–5 s, zielona dioda szybko miga), przedmiot lub kropla wody na polu dotykowym jest po 10 s ignorowana, lepsze wykrywanie szybkich stuknięć; ochrona zapisu przy spadku napięcia zasilania |
| [0.13.0](firmware/0.13.0/tomee-key-0.13.0.bin) | 6 | 2026-09-29 | `f95e605de743ccf2…` | Wpisywanie kodów dotykiem: 1, 2, 3 dotknięcia lub przytrzymanie wpisują kod przypisanego konta, 4 dotknięcia powtarzają ostatni kod (przypisanie w Tomee Manager, zakładka Kody) |
| [0.12.0](firmware/0.12.0/tomee-key-0.12.0.bin) | 6 | 2026-09-29 | `a3e58f19199e59bb…` | Kody TOTP/HOTP (do 56 kont, SHA1/SHA256, opcjonalny dotyk); wymaga Tomee Manager z zakładką Kody |
| [0.11.0](firmware/0.11.0/tomee-key-0.11.0.bin) | 6 | 2026-09-28 | `63376099bf62a65e…` | FIDO2 / CTAP 2.1: passkeys, PIN, hmac-secret, credProtect, podpisane aktualizacje, interfejs Tomee Management |

## Firmware z izolacją TrustZone (od 0.15.0)

Klucze z izolacją TrustZone (od wersji 0.15.0) mają dwa osobno aktualizowane obrazy: aplikację i usługi bezpieczne, każdy z własną wersją bezpieczeństwa. Tomee Manager od wersji 0.4.0 rozpoznaje rodzaj klucza i proponuje właściwe pliki. Klucz bez TrustZone nie przyjmie tych obrazów, a klucz z TrustZone — obrazów z tabeli powyżej. Przejście istniejącego klucza na TrustZone wykonuje Tomee (dane zostają).

| Wersja | Obraz | Wersja bezpieczeństwa | Data | SHA-256 | Zmiany |
|---|---|---|---|---|---|
| [0.15.0](firmware/0.15.0/tomee-key-services-0.15.0.bin) | usługi bezpieczne | 1 | 2026-10-05 | `b009d0c24fb00b7f…` | Izolacja TrustZone: klucz urządzenia, klucze kont, podpisy, PIN, hmac-secret i sekrety kodów jednorazowych działają w strefie bezpiecznej mikrokontrolera, a część startowa jest chroniona przed zapisem i ukrywana po uruchomieniu; usługi bezpieczne aktualizowane osobno; dla kluczy z TrustZone (wymaga Tomee Manager 0.4.0) |
| [0.15.0](firmware/0.15.0/tomee-key-0.15.0.bin) | aplikacja | 6 | 2026-10-05 | `a25e379549b165db…` | Izolacja TrustZone: klucz urządzenia, klucze kont, podpisy, PIN, hmac-secret i sekrety kodów jednorazowych działają w strefie bezpiecznej mikrokontrolera, a część startowa jest chroniona przed zapisem i ukrywana po uruchomieniu; usługi bezpieczne aktualizowane osobno; dla kluczy z TrustZone (wymaga Tomee Manager 0.4.0) |

Pełne sumy SHA-256 są w pliku `SHA256SUMS` w katalogu każdej wersji.
