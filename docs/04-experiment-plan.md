# Experiment Plan — 8-week pilot (expandable)

Updated 2026-11-05 | status: planned, baseline not started

## Question being tested

Can AI recommendations informed by soil readings, weather trends and standardized photos improve watering decisions and plant outcomes compared with a consistent **safe conventional care protocol**?

**Design limitation:** 6 A plants vs 6 B plants = small feasibility pilot, not sufficient to declare statistically proven superiority.

## Experimental arms and controls

- **A control — 6 pots**: same shared shade as B, water by pre-declared safe conventional inspection rule (manual finger/weight check each morning and afternoon if hot); amounts and timestamps recorded.
- **B AI assisted — 6 pots**: same shared shade as A, AI can propose earlier/later watering based on observations, manual checks and sensor readings; human confirms actions; always record recommendation/action/reason.
- Same seeds, pot size, mix, fertilizer schedule, spacing, pest handling, rain exposure, shade schedule, camera protocol and safe intervention thresholds for both arms.
- Shade cloth is a **shared plot intervention** and MUST be identical for A and B. The AI may suggest a global shade schedule for safety but it is logged separately and cannot be counted as an independent B-only improvement.
- Suggested starting layout A/B is interleaved. After similar-sized seedlings establish, block/randomize labels by location or document deviations. Do not move or swap plants mid-comparison without logging.

## Staged week plan

| Window | Activities | Deliverable | Gate |
|---|---|---|---|
| Pre-week / 2–3 days | Survey weather exposure, rain puddles, Wifi, safe DC power, sun path 08/11/14 | site photos & coordinates | garden position approved |
| Week 1 | Planting/seedling start, IDs A01–B06; water measurement; baseline photos | plant registry | germination documented |
| Week 2 | Install safe shade / data logger dry run, verify sensor calibration and connectivity | baseline data and QA | ≥90% expected logging coverage after acceptance |
| Weeks 3–4 | AI in **shadow mode**: outputs advice but does not influence either group | blinded advice vs human observations | review false alerts / missing data |
| Weeks 5–6 | AI-assisted B watering with human sign-off; A continues fixed conventional safe protocol | daily treatment logs | no unresolved safety concerns |
| Weeks 7–8 | Measure growth, compare treatment outcomes, harvest *if mature* | interim report and retrospective | decide extend, iterate or stop |
| After week 8 if necessary | Continue until meaningful edible leaf harvest / flowering observations | actual leaf mass result | close experiment |

**Important:** greenhouse/temperate harvest estimates do not guarantee leaves ready in 8 weeks. Record first harvest and first buds as observed.

## Measurements and cadence

| Metric | How | Cadence |
|---|---|---|
| Air temperature (°C), RH (%) | shielded SHT31 at canopy | every 5 min |
| Light in/out (lux) | 2× BH1750; flag saturation | every 5 min; compare only within valid range |
| Soil moisture | 4× calibrated probes; raw and calibrated indicator | every 5 min |
| Water added (mL) | graduated jug per pot; after rain note weather | every watering |
| Pot weight (optional, g) | manual kitchen scale for representative pots | 2–3× week |
| Plant height (cm), count of healthy leaves | consistent ruler + observation | 2× week |
| Largest healthy leaf length/width (cm) | ruler | weekly |
| Leaf damage/discoloration/pest signs | photo + human label (unknown permitted) | ≥4× week |
| Stem/flower buds | visual inspection | at least weekly |
| Harvest mass (g) | clean scale per plant | whenever ready |
| Human effort (minutes) | handling, watering, shade changes | every action |
| AI advice | model, prompt version, evidence refs, confidence & outcome | 1× daily |

## Initial shade protocol — both arms

- Full-sun site: start with roof mesh 50% for high-heat interval roughly 10:30–15:30 on sunny days.
- Log every open/close timestamp plus sky/rain state. Modify only if plants experience visible distress; apply equally to A/B.
- Record thermometer and photos; do not assume all afternoon leaf drooping means water deficit — check pot moisture before extra watering.
- For severe weather/high wind, remove shade cloth safely and protect people first, documenting any experiment interruption.

## Soil sensor calibration (required)

1. Take reading for sensor placed in the actual consistent potting mix when relatively dry but still viable.
2. Wet pot thoroughly until drainage, allow free drainage / settle, record saturated-after-drain reading and pot mass.
3. Repeat on each of 4 probes; map raw ADC to a relative moisture score **per sensor**; label it as an estimate not absolute volumetric water content.
4. Verify probes after 48h and weekly; if sensor drift conflicts with manual/weight check, mark reading invalid.
5. Never set universal numeric water/no-water threshold solely from cheap probe output.

## AI advice and human policy

Every recommendation includes: pot_id, timestamp, relevant sensor window, image path/time, observations, suggested action, severity, uncertainty, and manual approval.

- Red flags: suspected disease, pesticide/fungicide recommendation, excess watering, heat stress or missing sensors → ask human to inspect, never auto-act.
- No plant health diagnosis from image alone; treat it as a hypothesis.
- Decision outcome tags: accepted, modified, rejected, not_applicable.
- For A plants, record AI advice only in shadow mode; never secretly apply it to A to avoid treatment crossover.
- Rescue watering allowed for all plants using the same minimum welfare protocol; clearly log it as protocol override.

## Comparison and interpretation

Evaluate per plant and by arm:
- Number surviving; height and healthy leaf count at weeks 2/4/6/8
- Mean leaf length/width and first edible leaf or flower-bud timing
- Total added water in litres **plus rainfall notes** (rain may confound)
- Harvested edible mass if available
- Labor time and number of interventions
- AI alert false positives, actual accepted actions and telemetry availability

Use descriptive tables/photos, not ungrounded claims about statistically significant AI improvement. If either arm gets significantly different shade due to position, flag comparison compromised.

## Daily operator rhythm

08:00 inspect all pots + photo; check soil/manual. 11:00 verify sun/shade action. 16:00 look for signs of stress and evaluate watering. Evening AI summary (time can change). Logged entries are more important than following exact clock times.

## CSV templates in repository

- [Plant registry](../data/templates/plant-registry.csv)
- [Daily observations](../data/templates/daily-observations.csv)
- [Water and decisions](../data/templates/watering-log.csv)
