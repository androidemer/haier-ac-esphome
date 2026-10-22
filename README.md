# Haier AC — integracja z Home Assistant przez ESP32

Lokalna integracja klimatyzatorów Haier z Home Assistant, z pominięciem chmury Haier/hOn. Działa całkowicie offline — bez internetu, bez chmury, bez rejestracji.

## Testowane modele

| Model | Moduł WiFi | Protokół | Status |
|-------|-----------|----------|--------|
| Haier AS50TDDHRA-CL | KZW-W002 - zmieniony na ESP | hOn (UART 9600) | ✅ Działa |

## Czego potrzebujesz

- **Home Assistant** z dodatkiem ESPHome
- **ESP32-C3 Super Mini** (~15-25 zł na Allegro/AliExpress)
- odcięty kabelek z końcówką USB A
- Lutownica (opcjonalnie, ale zalecane)

## Szybka instalacja

### 1. Podłącz ESP32 do klimatyzacji

Zdejmij przedni panel klimatyzacji. Znajdź złącze USB-A (to UART, nie USB!).

Klima USB-A ESP32-C3 Super Mini
## Pin 1 (5V) - 5V (VIN)
## Pin 2 (TX) - GPIO5
## Pin 3 (RX) - GPIO4
## Pin 4 (GND) - GND

>  Nie montuj ESP32 w metalowej obudowie — blokuje WiFi!

### 2. Wgraj firmware

1. Otwórz **ESPHome** w Home Assistant
2. **New Device** → nazwa: `haier-klima` → wybierz **ESP32-C3**
3. Zamień zawartość pliku YAML na zawartość z [`esphome/haier-ac.yaml`](esphome/haier-ac.yaml)
4. Edytuj sekcję `substitutions` — wpisz swoją sieć WiFi
5. Kliknij **Install** → **Plug into computer** (przez USB za pierwszym razem)

### 3. Dodaj do Home Assistant

Po wgraniu ESP32 powinien pojawić się automatycznie w:
**Ustawienia → Urządzenia i usługi → ESPHome**

### 4. Dodaj dashboard

Skopiuj zawartość z [`dashboard/haier-card.yaml`](dashboard/haier-card.yaml) do swojego dashboardu.

## Parametry techniczne

| Parametr | Wartość |
|----------|---------|
| Protokół | hOn (UART) |
| Prędkość | 9600 baud |
| TX ESP32 | GPIO4 |
| RX ESP32 | GPIO5 |
| Złącze klimy | USB-A (elektrycznie UART) |
| Zasilanie | 5V z klimy → VIN ESP32 |

## FAQ

**Q: Mogę używać innego ESP32?**
A: Tak. Zmień `board:` w konfiguracji (np. `esp32dev` dla ESP32-WROOM).

**Q: Co jeśli moja klima używa smartAir2?**
A: Zmień `protocol: hOn` na `protocol: smartAir2` i spróbuj `baud_rate: 2400`.

**Q: Czy mogę jednocześnie używać aplikacji hOn?**
A: Nie. Po wymianie modułu klima jest w 100% lokalna.

**Q: Czy ikona WiFi pojawi się na wyświetlaczu klimy?**
A: Tak, dzięki opcji `wifi_signal: true`.

## Licencja

MIT License — rób z tym co chcesz.
