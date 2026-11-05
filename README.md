# Plant AI — Smart Perilla Farm

โครงการทดลองปลูก **ใบงาเกาหลี (Korean perilla / Kkaennip)** ด้วย AI + IoT ในสวนบ้าน

## Pilot v0.4 — assumptions (2026-11-05)

- สถานที่: สนามหญ้า/พื้นดินกลางแจ้ง ได้รับแดดเกือบทั้งวัน
- พื้นที่ทดลอง: 3.0 × 2.0 เมตร (โครงสแลนชั่วคราว); เผื่อทางเดินรอบนอก
- พืช: 12 กระถาง ขนาด 10–12 นิ้ว ยกพ้นพื้น 10–15 ซม.
- แสง: สแลน 50% หลังคาถอด/ม้วนได้ ข้างเปิด; ม่านฝั่งแดดบ่ายเป็น option
- A/B: 6 กระถางดูแลมาตรฐาน และ 6 กระถางรับคำแนะนำ AI; ทั้งคู่ใช้สแลนเดียวกัน
- ระยะ: 8 สัปดาห์สำหรับ pilot; อาจขยายจนเก็บเกี่ยวได้จริง
- สถานะ: **Planning / Not installed** — ขนาดและทิศจริงต้องวัดหน้างานก่อนซื้อโครง

## Documents

1. [Project charter and scope](docs/01-project-charter.md)
2. [Detailed plot layout and sensor placement](docs/02-site-layout.md)
3. [Bill of materials (BOM)](docs/03-bom.md)
4. [Experiment and measurement plan](docs/04-experiment-plan.md)
5. [IoT/AI architecture and data contract](docs/05-iot-ai-architecture.md)
6. [Installation and acceptance checklist](docs/06-installation-checklist.md)
7. [Scalable plot drawing (SVG)](docs/site-layout.svg)

## Guiding principles

- Plant safety first: water/drainage decisions stay under human control in MVP1.
- MQTT/InfluxDB/Grafana on the existing Home Lab; camera uses phone at first.
- Record raw data and manual interventions; AI advice is always auditable.
- Do not change the shared shade roof differently for A and B during the comparison.
- No purchase commitments until surveying sun path, drainage, power and Wi-Fi.

## First milestone

Survey 08:00 / 11:00 / 14:00 for 2–3 days; confirm physical dimensions and direction; then approve BOM and build.
