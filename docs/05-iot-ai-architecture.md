# IoT + AI System Architecture (MVP1)

Updated: 2026-11-05 | Design target: Home Lab existing stack, not always-on AI PC

## Topology

~~~text
12 pots / 3×2m shared shade
   ├─ 4× capacitive moisture probes
   ├─ 1× SHT31 (shielded ambient air)
   └─ 2× BH1750 (under / outside shade; lux only)
                 │ 3.3V GPIO/ADC; weather-protected cables
                 ▼
             ESP32 2.4GHz Wi-Fi
                 │ MQTT over LAN (retry / no movement commands)
                 ▼
          Home Lab MQTT broker
                 │ Telegraf / small collector
                 ▼
          InfluxDB ───────► Grafana charts + alert checks
                 │
                 ├──── daily structured observation summary
Phone photos ────┤
                 ▼
          AI analyzer (on-demand when AI PC available)
                 │
                 ▼
        Recommendations stored + human approval log
                 └──── daily summary / optional message alert
~~~

## Split responsibilities

| Component | Always on? | Function |
|---|---|---|
| ESP32 | yes if powered | read probes, buffer small outages, publish |
| Home Lab broker/collector | yes | telemetry ingestion, validation, persistence |
| InfluxDB/Grafana | yes | trends, gaps, anomalies, dashboards |
| Phone photo workflow | operator | repeatable evidence photos, filenames |
| Local vision model / LLM | **no** | batch assessment, photo comparison and recommendations |
| Human | on inspection | watering, shade, pest care, safety overrides |

## MVP telemetry envelope / contract v0.1

MQTT topic: plant-ai/v1/site/home/telemetry (device identifier in payload).
Timestamp: ISO-8601 **UTC** from synchronized clock; dashboard display Asia/Bangkok.

~~~json
{
  "schema_version": "1.0",
  "ts": "2026-11-05T03:00:00Z",
  "device_id": "esp32-plot-01",
  "air_temp_c": 31.2,
  "air_rh_pct": 69.0,
  "lux_inside": 24100,
  "lux_outside": 53200,
  "soil": {
    "A02": {"adc_raw": 1876, "relative_moisture_pct": 43.0, "valid": true},
    "B02": {"adc_raw": 1771, "relative_moisture_pct": 50.0, "valid": true},
    "A05": {"adc_raw": 2056, "relative_moisture_pct": 35.0, "valid": true},
    "B05": {"adc_raw": 1920, "relative_moisture_pct": 40.0, "valid": true}
  },
  "shade_state": "deployed",
  "sample_quality": ["demo_sample_not_actual_data"]
}
~~~

Numbers above are **illustrative**, not measured. Report both raw ADC and per-probe calibrated indicator; keep valid flag. Do not mislabel relative percent as measured volumetric water content.

## Suggested InfluxDB measurements

- plant_air: tags site_id, sensor_id; fields temp_c, rh_pct, valid
- plant_light: tags site_id, sensor_id (inside/outside); fields lux, saturated, valid
- plant_soil: tags pot_id, sensor_id, treatment_arm; fields raw_adc, relative_pct, valid
- plant_event: tags event_type, pot_id, arm; fields water_ml, duration_min (as applicable)
- plant_ai_report: store rich text + references in files/SQLite/Postgres, not inflated InfluxDB tags

**No cardinality explosion:** avoid attaching photo IDs, unique alert IDs or raw text as InfluxDB series tags. Persist high-cardinality events in relational/file storage.

## QA and alerts

- 5-minute sampling, timestamp UTC, fields may be null if measurement failed.
- Flag missing measurement and improbable jumps instead of silently interpolating.
- 10-minute no-data alert; repeated probe flatline and strong sensor disagreement flagged for manual inspection.
- Under-vs-outside shade lux ratio requires both sensors valid and **not saturated**.
- Initial temperature, soil and light alert thresholds should be **observational**, tuned after first 7–14 days, not hard-coded irrigation triggers.

## Vision protocol

- Filename: YYYY-MM-DD_HHMM_<pot_id>_<view>.jpg; photo local storage, no private household details in frame.
- Minimum top + side images per pot when feasible with scale label, consistent background/angle and time.
- AI output JSON should include: observation, evidence_photo, evidence_sensor_window, concern, uncertainty, suggested_manual_action, rationale, version, reviewed_by_human.
- Avoid claim that an LLM provides certified plant disease identification.

## Security, power, and reliability

- MQTT authentication; local Wi-Fi/IoT network only; no direct internet exposed.
- Keep credentials in local configuration, never committed.
- Place mains power supply in a suitable weather-protected location, route **low-voltage** cable to the plot; use properly protected circuits and qualified installer for new outdoor AC work.
- Drip loops and weatherproof cable glands for box; no exposed joints / open USB power bricks on wet lawn.
- ESP32 analog inputs are **3.3V maximum**. Confirm sensor voltage and voltage-divider needs before wiring.
- Brownout/restart should resume logging only; no uncontrolled actuators (MVP has none).
- If AI PC offline, data collection and Grafana continue unaffected.

## Deferred for MVP2

Automatic irrigation: dedicated pump + flow sensor + dry-run/failsafe + manual override + weather protection. Requires separate design and human confirmation after MVP1 validates advice.
