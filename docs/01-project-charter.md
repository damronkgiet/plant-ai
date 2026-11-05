# Project Charter — Smart Perilla Farm (Pilot v0.4)

Updated: 2026-11-05 | Status: proposed, not yet constructed

## Why this project

ทดลองใช้ AI + IoT ช่วยปลูกใบงาเกาหลี (Perilla frutescens, Kkaennip) ในพื้นที่กลางแจ้งของบ้านที่แดดเกือบทั้งวัน โดยเน้นความสามารถในการ **วิเคราะห์และเสนอการดูแลที่มีหลักฐาน** มากกว่าความอัตโนมัติทันที

## Decisions already made

| Parameter | v0.4 choice |
|---|---|
| Terrain | สนามหญ้า/พื้นดิน กลางแจ้ง แดดเกือบทั้งวัน |
| Pilot footprint | 3.0 m (X) × 2.0 m (Y), ต้องมีทางเดินภายนอก |
| Plants | 12 กระถาง แบ่ง control A 6 / AI-assisted B 6 |
| Sun management | หลังคาสแลนถอด/ม้วนได้ 50% ทดลองใช้ช่วงแดดจัด; ข้างเปิด |
| Irrigation | มือรดน้ำทั้งหมดใน MVP1 และจดปริมาณน้ำรายกระถาง |
| Data | ESP32, moisture 4 points, air temperature/RH 1 point, lux in/out |
| Vision | มือถือถ่ายจากมุมมาตรฐานก่อนลงทุนกล้อง |
| Server | MQTT → InfluxDB → Grafana + AI report; reuse Home Lab |
| AI | วิเคราะห์ข้อมูล + ภาพ + ประวัติ แต่ไม่สั่งปั๊ม/สแลนอัตโนมัติ |

## Scope

**MVP0 / week 0–2:** สำรวจแสง/ฝน/Wi-Fi/ไฟ, ซื้อของเท่าที่จำเป็น, เพาะเมล็ด, ทำโครงและเริ่ม logging

**MVP1 / week 3–6:** ดูแลจริงและเปรียบเทียบ A (standard care) vs B (AI-recommended watering decisions); ภาพและ sensor anomaly; human approval

**Review / week 7–8:** ประเมินอัตรารอด สุขภาพใบ การเจริญเติบโต การใช้น้ำ การใช้แรง และ readiness ของ AI; ขยายเวลาจนมีผลผลิตหากยังไม่ถึงระยะเก็บใบ

**Out of scope:** ปั๊มน้ำอัตโนมัติ, มอเตอร์สแลน, smart fertigation, automated disease diagnosis, commercial yield claim, controlled environmental chamber, 24/7 on-prem LLM.

## Scientific caveats / hypotheses

- Perilla ปลูกได้แดดเต็มวันหรือร่มบางส่วน ต้องระบายน้ำดี; สแลน 50% เป็น **ค่าเริ่มทดลอง** ไม่ใช่ค่าที่พิสูจน์ว่าดีที่สุด
- พืชตอบสนองต่อช่วงแสงสั้นและอาจเริ่มออกดอกตามฤดูกาล/สายพันธุ์เร็วขึ้น (โดยเฉพาะการเริ่มเดือนพฤศจิกายนในไทย); บันทึกวันที่เห็นตาดอก
- เซนเซอร์ Lux ไม่ใช่ PAR/PPFD และใช้คำนวณ DLI โดยตรงไม่ได้
- การทดลอง 6 ต่อ 6 กระถางมีเป้าหมายเป็น feasibility pilot ไม่ใช่การพิสูจน์ประสิทธิภาพเชิงสถิติ

## Success / exit criteria

1. Survive ≥80% ที่ week 6 เป็นเป้าหมายใช้งาน ไม่ใช่คุณสมบัติที่รับประกันของพืช
2. Sensor data completeness ≥90% ระหว่างช่วงที่ระบบเปิดใช้งานตามแผน
3. ภาพต้นละ ≥4 วัน/สัปดาห์; การรดน้ำมีปริมาณและเวลา
4. มีรายงาน AI อย่างน้อยวันละ 1 รอบในช่วงทดลอง AI พร้อม evidence และ actual action
5. เปรียบเทียบ A/B: survival, leaves, largest leaf dimensions, height, biomass (ถ้าเก็บเกี่ยว), water volume, labor minutes, incidence of stress
6. ไม่มีเหตุการณ์อันตรายจากอุปกรณ์ไฟฟ้าหรือโครงสร้าง

## Risks and countermeasures

| Risk | Countermeasure |
|---|---|
| ฝนหนัก/น้ำขัง/รากเน่า | วางกระถางบนขาตั้ง 10–15 cm, ระบายน้ำรอบแปลง, no solid roof assumption |
| ลมแรงทำให้โครงสแลนล้ม | ค้ำยันและสมอบกตามดินจริง, quick-release fabric, ถอดผ้าก่อนพายุ |
| แดดบ่ายแรง ทำใบเหี่ยว | สแลน 50% ช่วงแดดแรง, วัดแสงใน/นอก + อาการใบ, ไม่ล็อกเวลาโดยไม่ดูสถานการณ์ |
| ทดลอง A/B ถูก confound | ทั้งสองกลุ่มใช้โครงสแลนเดียวกัน, สลับตำแหน่ง, ขนาดกระถาง/ดิน/ปุ๋ยเท่ากัน, เปลี่ยนเฉพาะการตัดสินใจรดน้ำ |
| AI hallucination / vision ambiguity | รายงานระดับความมั่นใจ, อ้างอิง sensor/time/photo, ให้คนอนุมัติทุก action |
| Soil sensor drift | สอบเทียบจาก substrate จริง + ชั่งน้ำหนักกระถาง + ตรวจด้วยมือ, ไม่ใช้ raw ADC เป็น % สากล |
| Crop maturity mismatch | วัดผลที่ 8 สัปดาห์ แต่ harvest endpoint ขยายต่อเมื่อจำเป็น |
| Indoor LLM PC off | batch analysis เมื่อติดเครื่อง, data collector ไม่ต้องพึ่ง AI PC |

## Sources (background, checked 2026-11-05)

- [NC State Extension — Perilla frutescens](https://plants.ces.ncsu.edu/plants/perilla-frutescens/common-name/perilla/) — full sun / partial shade, well-drained soil.
- [PROSEA — Perilla frutescens ecology](https://prosea.prota4u.org/view.aspx?id=586) — short-day flowering and ecology.
- [Chuenwarin et al., 2026](https://doi.org/10.1002/nzc2.70182) — day-extension light and flowering/leaf yield; included for later-phase hypothesis, not pilot lighting spec.

## Next decision gate

ทำ survey หน้างาน 2–3 วัน แล้วบันทึก: ทิศจริง แดด 08/11/14, จุดน้ำขัง, กำลังไฟต่ำแรงดันปลอดภัยจากในบ้าน, 2.4GHz Wi-Fi, และตำแหน่งทางเดิน. **ห้ามซื้อโครงตามแผนโดยไม่วัดพื้นที่/ตรวจจุดยึดจริง.**
