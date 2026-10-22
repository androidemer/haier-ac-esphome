# Schemat podłączenia

## Złącze w klimatyzacji

Zdejmij przedni panel. Znajdź moduł KZW-W002 podłączony do złącza USB-A.

> Złącze wygląda jak USB, ale elektrycznie to UART!

## Pinout USB-A

| Pin | USB nazwa | Funkcja |
|-----|-----------|---------|
| 1 | VCC | 5V zasilanie |
| 2 | D- | TX lub RX |
| 3 | D+ | RX lub TX |
| 4 | GND | Masa |

## Podłączenie do ESP32-C3

| Klima | ESP32-C3 |
|-------|----------|
| Pin 1 (5V) | 5V (VIN) |
| Pin 2 | GPIO5 |
| Pin 3 | GPIO4 |
| Pin 4 (GND) | GND |

> Jeśli nie działa — zamień piny 2 i 3 miejscami.

## Uwagi

- Nie montuj ESP32 w metalowej obudowie
- Nie używaj GPIO01/GPIO03 (kolidują z USB)
- Zasilanie 5V z klimy podłącz do pinu VIN (nie 3.3V!)
