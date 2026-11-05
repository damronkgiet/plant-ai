# BOM — Smart Perilla Farm outdoor pilot

Updated: 2026-11-05 | THB indicative planning ranges, **not quotations or guaranteed stock**

Assumption: no existing spare pots, no spare metal frame; existing Home Lab/InfluxDB/Grafana and smartphone reused. **No mains power wiring on an exposed lawn.** Obtain local quotes and measure mounting dimensions before procurement.

## A. Plants and pots — essential

| Code | Item | Qty | Planned total (THB) | Notes |
|---|---|---:|---:|---|
| P01 | Pot 10–12 inch, drain holes | 12 | 480–960 | same batch/model all 12 |
| P02 | Consistent potting mix | ~90–120 L | 350–750 | same mix and mass/volume per pot |
| P03 | Verified edible green Korean perilla (kkaennip) seeds | 1 packet (+spare) | 80–180 | verify true seed type and provenance; do not substitute sesame |
| P04 | Stable risers/blocks | 12 sets | 240–600 | elevate 10–15cm, do not obstruct holes |
| P05 | Labels, mulch, watering measure | 1 set | 200–450 | ID tag + graduated measuring jug |
| | **Subtotal A** | | **1,350–2,940** | |

## B. Shade structure — essential for full-sun site

| Code | Item | Qty | Planned total (THB) | Notes |
|---|---|---:|---:|---|
| F01 | Galvanized steel poles/crossbars for 3×2m, ~2m tall | 6 posts + crossbars | 1,500–3,000 | cut list after site survey; avoid unbraced PVC |
| F02 | Ground anchors, braces, connectors | 1 set | 350–800 | type depends on soil, high wind risk |
| F03 | 50% shade mesh ~2m wide × 3–4m long | 1 | 200–450 | account for overlap/rolling, verify exact net dimensions |
| F04 | Clips, straps, ties, quick-release rope | 1 set | 150–350 | fabric must be removable quickly |
| | **Subtotal B** | | **2,200–4,600** | |
| F05 | Optional west-facing roll-up curtain | 1 | +200–500 | buy only if side sun still a problem |

## C. Sensor and electronics — essential for telemetry MVP

| Code | Item | Qty | Planned total (THB) | Notes |
|---|---|---:|---:|---|
| E01 | ESP32 DevKit (2.4GHz Wi-Fi) | 1 | 180–350 | reuse spare if available |
| E02 | SHT31 with radiation shield/weather arrangement | 1 | 250–600 | keep measuring element ventilated |
| E03 | BH1750 / suitable Lux sensor weather-housed | 2 | 160–360 | shaded vs unshaded; Lux ≠ PAR; check saturation |
| E04 | Capacitive soil probes for continuous outdoor operation | 4 | 520–1,400 | prefer sealed probes; cheap bare PCB probes are not truly rainproof |
| E05 | IP65 enclosure + mounting | 1 | 180–450 | mount at south central frame post |
| E06 | Cable glands, short shielded signal wires, mounting hardware | 1 set | 250–600 | ADC cable noise check required |
| E07 | Safe 5V DC supply and outdoor-rated low-voltage routing | 1 set | 300–900 | power supply positioned protected, residual-current-protected circuit if mains involved |
| | **Subtotal C** | | **1,840–4,660** | |

## Summary

| Bundle | THB |
|---|---:|
| Plants + pots | 1,350–2,940 |
| Shade structure | 2,200–4,600 |
| Electronics | 1,840–4,660 |
| **Essential total (A+B+C)** | **5,390–12,200** |
| West curtain optional | +200–500 |
| Later irrigation pump/valves and camera | **excluded** |

Amounts depend heavily on durability of outdoor sensor probes, metalwork and already-owned components. Delivery, contractor labor, replacements, and electrical professional fees excluded. The earlier lighter budget excluded part of robust outdoor anchoring and durable electronics; this is a fuller outdoor estimate.

## Practical procurement stages

**Buy first:** seeds, 12 pots, potting mix, labels, measuring jug; simulate field in phone spreadsheet before full sensors.

**After site survey:** metal frame, ground anchors and shade mesh. Check soil firmness / wind / water access.

**After dry-run on bench:** ESP32 + SHT31 + 2 lux + 4 soil probes + box, verify range/noise and MQTT; install outdoors only after safe wiring check.

**Do not buy yet:** irrigation pump, automated shade motor, fixed IP camera, expensive PAR sensor, heater/chiller, fertilizer injector.

## Example Thai retail price evidence (not endorsements; verify current price/stock)

- [ArtronShop Farm1 component listing](https://www.artronshop.co.th/product/tag/Farm1): commodity capacitive sensor ~118 THB; weather-ready versions often cost more.
- [ArtronShop humidity sensor listing](https://www.artronshop.co.th/category/57/โมดูลเซ็นเซอร์วัดอุณหภูมิและความชื้น): SHT30 commodity module ~161 THB (not equivalent to shielded outdoor assembly).
- [Thai Electronic and Sensor Technology](https://thaielecsensor.com/shop): industrial versions often materially costlier.
- Specific price rows above are planning allocations, **not copied vendor offers**; obtain 2 quotes for frame/anchors and confirm sensor packaging specifications before order.

## Supplier acceptance requirements

- Seed packet explicitly says Korean edible perilla / kkaennip / Perilla frutescens, with seller and lot/date.
- All pots same volume, draining freely.
- Structural frame has safe anchor/tie-down plan and rapid cloth release.
- Electronics 5V/3.3V-compatible with documented interfaces; ESP32 ADC inputs must never receive >3.3V.
- Outdoor electronics withstand splash; **IP65 box does not make exposed sensor boards waterproof**.
