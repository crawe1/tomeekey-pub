# Tomee Key — firmware

Podpisane obrazy firmware klucza Tomee Key. Instalacja: Tomee Manager → zakładka Firmware → wybierz plik `.bin`.
Klucz sprawdza podpis i nie przyjmie pliku z niższą wersją bezpieczeństwa niż zainstalowana.
Pełne sumy SHA-256: `SHA256SUMS` w katalogu wersji.

| Wersja | Wersja bezpieczeństwa | Data | SHA-256 | Zmiany |
|---|---|---|---|---|
| [0.11.0](firmware/0.11.0/tomee-key-0.11.0.bin) | 6 | 2026-09-28 | `63376099bf62a65e…` | FIDO2 / CTAP 2.1: passkeys, PIN, hmac-secret, credProtect, podpisane aktualizacje, interfejs Tomee Management |
