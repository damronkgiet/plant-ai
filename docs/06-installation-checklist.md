# Work Plan and Installation Checklist

Updated: 2026-11-05 | Status: TODO | Track completion by editing [ ] → [x] with date/evidence

## Gate 0 — site survey (before buying frame)

- [ ] Record GPS **not necessary**; sketch garden orientation N/E/S/W and measure unobstructed 3×2 m footprint
- [ ] Confirm available access/walkways (ideally 0.6 m outside frame)
- [ ] Photograph shadows at 08:00, 11:00, 14:00 on 2–3 days
- [ ] Identify lowest wet area after rain; do not place pots in standing runoff
- [ ] Verify phone + ESP32 2.4GHz Wi-Fi at planned enclosure
- [ ] Identify safe power strategy: protected indoor supply / outdoor low-voltage cable
- [ ] Check strong wind exposure, children/pets, access, soil condition for anchors
- [ ] Finalize north arrow / rotate SVG and update coordinates if real plot differs

**Done when:** site dimensions and risks documented with photos; BOM budget approved.

## Gate 1 — crop & frame

- [ ] Source verified Korean perilla edible seed and test germination with spare seeds
- [ ] Label all 12 equal pots and verify drainage
- [ ] Mix common substrate, record initial volume and inputs, assign seedlings fairly
- [ ] Prepare 12 stable stands 10–15cm above grass
- [ ] Install 6-post frame with diagonal bracing, verified anchors and user-safe access
- [ ] Attach removable 50% shade mesh; test removal/open/close without snagging
- [ ] Keep sides open, confirm roof does not trap people/wires
- [ ] Inspect during dry gusts; **do not leave cloth on if a storm is forecast**

**Done when:** frame and supports are stable, all pots accessible, drainage clear.

## Gate 2 — electronics bench test

- [ ] ESP32 Wi-Fi connected and MQTT publishing at 5-minute intervals
- [ ] SHT31 in radiation shield with ventilation
- [ ] Inside and outside light sensors with correct rain-protection, not saturated in comparison window
- [ ] Four soil probes read consistently, each with its own calibration record
- [ ] Validate 3.3V ADC input levels, cable length/noise and no exposed conductors
- [ ] Record test data in InfluxDB and create basic Grafana panel
- [ ] Test Wi-Fi disconnection/restart: log and alert without losing control safety
- [ ] Place powered box above splash level, route low voltage only in secure weather-resistant way

**Done when:** 24h bench + 24h in-place telemetry sample, data completeness ≥90%, no unsafe power setup.

## Gate 3 — planting baseline

- [ ] Fill plant-registry.csv for all pots (seed batch, sowing, transplant date)
- [ ] Take first photo per pot with ID/ruler and fixed viewpoint
- [ ] Calibrate irrigation measuring jug and log mL per pot
- [ ] Agree rescue watering rule and which decisions differ across A/B
- [ ] Freeze shared shade schedule for comparison, change for safety only and log it

**Done when:** 12 IDs tracked, consistent care protocol established.

## Gate 4 — pilot & review

- [ ] Daily sensor summary checks and inspect all 12 pots
- [ ] Weeks 3–4 AI shadow report reviewed for quality
- [ ] Weeks 5–6 B AI recommendations approved/rejected with reason
- [ ] Every watering and shade action recorded including weather/rain
- [ ] Weekly progress report and photos, watch for flower buds
- [ ] Week 8 compare per-pot outcomes and decide extend / redesign / finish

## Delivery / definition of done

- [ ] Plot usable and safe after rain/wind check
- [ ] Device-to-Grafana telemetry working with validated units
- [ ] AI daily report includes evidence and uncertainty
- [ ] A/B results summarized without overstating significance
- [ ] Final retrospective lists issues and proposed MVP2 requirements

## Change log

- 2026-11-05: First version, 12-pot full-sun outdoor pilot and shared shade fairness documented.
