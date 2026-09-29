# Tomee Key

Pliki do pobrania dla klucza zabezpieczeń Tomee Key.

## Tomee Manager (Windows)

Aplikacja do zarządzania kluczem: PIN, passkeys, klucze SSH i aktualizacje firmware. Nie wymaga instalacji ani uprawnień administratora — pobierz plik `.exe` i uruchom.

**Najnowsza wersja: [0.2.0](manager/0.2.0/TomeeManager-0.2.0.exe)** (2026-09-29)

Plik nie ma jeszcze cyfrowego podpisu wydawcy, więc Windows SmartScreen może wyświetlić ostrzeżenie („Więcej informacji” → „Uruchom mimo to”). Przed uruchomieniem możesz porównać sumę SHA-256 z tabelą.

| Wersja | Data | SHA-256 | Zmiany |
|---|---|---|---|
| [0.2.0](manager/0.2.0/TomeeManager-0.2.0.exe) | 2026-09-29 | `a6d3da7fd71eddcf…` | Pierwsze wydanie: informacje o kluczu, PIN, passkeys, klucze SSH, aktualizacje firmware z internetu, reset |

## Firmware

Podpisane obrazy firmware. Tomee Manager sam sprawdza nowe wersje i proponuje instalację; plik `.bin` można też wybrać ręcznie w zakładce Firmware. Klucz sprawdza podpis i nie przyjmie pliku z niższą wersją bezpieczeństwa niż zainstalowana.

| Wersja | Wersja bezpieczeństwa | Data | SHA-256 | Zmiany |
|---|---|---|---|---|
| [0.11.0](firmware/0.11.0/tomee-key-0.11.0.bin) | 6 | 2026-09-28 | `63376099bf62a65e…` | FIDO2 / CTAP 2.1: passkeys, PIN, hmac-secret, credProtect, podpisane aktualizacje, interfejs Tomee Management |

Pełne sumy SHA-256 są w pliku `SHA256SUMS` w katalogu każdej wersji.
