# IoT Platform Research — Plant AI

> Updated: 2026-11-17 | Status: research / hypotheses, not validated by hands-on testing.

## Purpose
Use Smart Perilla Farm as a research POC for ESP32 sensor monitoring, compare existing IoT platforms with a self-built dashboard, and identify possible hardware + cloud service opportunities. **Do not commit to a SaaS architecture or paid product yet.**

## Platform comparison

| Platform | Main strengths | Research questions |
|---|---|---|
| Arduino Cloud | Device/Thing setup, web/mobile dashboards, cloud variables, historical data, triggers and integrations | ESP32 board support, retention by plan, API limits, notification options, OTA support for selected boards, commercial licensing |
| Blynk | Mobile-oriented dashboards, device templates, provisioning and commercial IoT product features | Branding/white-label costs, fleet limits, data ownership, subscriptions |
| ThingsBoard | Telemetry, dashboards, device management, rule engine; Community Edition can be self-hosted | Multi-tenancy boundaries in CE vs paid editions, deployment/maintenance cost, end-user UX |
| Home Assistant | Local-first integrations, automations and dashboards | Suitability for single household vs multi-customer cloud service |

**Caution:** Capabilities, plans, prices and license terms change. Verify against vendor documentation before choosing a platform or quoting commercial pricing. Features may depend on hardware, plan or edition.

## Official references
- Arduino Cloud: https://docs.arduino.cc/arduino-cloud/
- Arduino Cloud plans: https://cloud.arduino.cc/plans/
- Arduino Cloud API: https://docs.arduino.cc/cloud-api/
- Blynk documentation: https://docs.blynk.io/
- ThingsBoard documentation: https://thingsboard.io/docs/
- Home Assistant documentation: https://www.home-assistant.io/docs/

## Research POC: 4-week outline
1. **Week 1:** Connect ESP32 + soil moisture + air temperature/humidity sensors to Arduino Cloud. Test setup, dashboard, alert, and data export/API.
2. **Week 2:** Mirror the same readings into local storage (Home Lab). Measure data gaps, connectivity recovery, and retention.
3. **Week 3:** Build a minimal self-hosted mobile-friendly dashboard. Compare setup effort, usability, maintenance, and costs.
4. **Week 4:** Add plant-specific threshold rules and a small AI-assisted interpretation experiment. Record failures and product hypotheses.

## Product ideas to validate (not confirmed demand)
- Per-plant and per-pot views rather than generic device dashboards.
- Care recommendations using plant species, age and growth stage.
- Join sensor readings with timestamped plant photographs and manual notes.
- Explainable alerts with suggested actions, not only numeric thresholds.
- Simple Wi-Fi onboarding and device-to-account pairing for nontechnical buyers.
- Hardware-only tier with essential functionality; optional paid history, alerts, or analysis.

## Evaluation checklist
- [ ] ESP32 connects and reports reliably
- [ ] Recovery after Wi-Fi/power outage
- [ ] Historical storage and export tested
- [ ] Dashboard usability on phone
- [ ] Notifications and API behavior verified
- [ ] Privacy/security and customer data separation evaluated
- [ ] Cloud costs estimated at 10 / 100 / 1,000 devices
- [ ] Vendor licensing and commercial use confirmed
- [ ] Customer willingness to pay tested independently of technical feasibility

## Decision record
- **Now:** Research first; experiment beyond immediate farm requirements to learn feasibility.
- **Preference:** Eventually design/build our own system if it offers meaningful advantages.
- **Not yet decided:** Platform, final architecture, target customers, subscription model, or product price.
