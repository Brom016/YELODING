# Case Study 5 — Solution Analysis
## Smart IoT-Enabled Solar Cold Storage Unit for Medical & Vaccine Supply Chains

> Working analysis for the International Student Essay Challenge (Unwahas / UMK / CvSU).
> All values labeled **[benchmark]** come from the brief; all values labeled **[estimate]** are our own transparent calculations with stated assumptions, as the brief requires.

---

## 1. What the Case Is Actually Testing

The brief explicitly says "the challenge is not simply to build a cooler." Reading the "Questions to Consider" as an implied scoring rubric, judges will reward:

1. **Quantitative reasoning** — real heat-load and PCM-mass calculations, not adjectives.
2. **Honest trade-off analysis** — TEC vs. vapor-compression compared, not one declared "best."
3. **Failure-first thinking** — behavior during power loss, no signal, sensor fault, door open, delay.
4. **Data credibility without hype** — tamper-evidence that acknowledges cryptography can't fix bad sensors or lying handlers (the brief warns about this explicitly).
5. **Testable pilot plan** — calibration, temperature mapping, holdover demonstration under a stated profile.
6. **Whole-life cost** — batteries, calibration, connectivity, training, not just unit price.
7. **Baseline methodology for the 25% spoilage figure** — how a real project would measure it.

---

## 2. Design Requirements (Consolidated)

| Requirement | Value | Source |
|---|---|---|
| Usable chamber volume | 30 L | **[benchmark]** |
| Operating band | 2–8 °C (we target 3–7 °C control band for margin) | **[benchmark + design choice]** |
| Extreme ambient baseline | 38–42 °C (test to 43 °C, WHO PQS hot climate) | **[benchmark + standard]** |
| PCM latent heat | > 220 kJ/kg | **[benchmark]** |
| Passive holdover | ≥ 24 h, no external power | **[benchmark]** |
| Sensor sampling | 30 s | **[benchmark]** |
| Max allowed excursion | 15 min (scenario benchmark) | **[benchmark]** |
| GPS accuracy target | 2.5 m under suitable conditions | **[benchmark]** |
| Cellular fallback | LTE-M / NB-IoT | **[benchmark]** |

**Intended product class (stated boundary):** routine EPI vaccines and biological reagents stored at 2–8 °C. Not blood products, not frozen products, not frozen IPPV (which needs −20 °C). All excursion decisions deferred to product labels and national immunization programme rules.

---

## 3. Thermal Engineering — The Core Calculations

### 3.1 Chamber geometry [estimate]

The payload chamber is fixed at 40 × 25 × 30 cm = **30.0 L** exactly [benchmark]. The compact revision (full working in `detail.md`) builds the walls as: liner 2 mm + VIP 25 mm + HDPE skin 2 mm, with 13 mm PCM plates inside the liner on the two long walls and the floor, and a 12 mm evaporator plate under the floor PCM.

- Cold box external: 0.458 × 0.334 × 0.383 m (**58.6 L**)
- A_in (inside the liner) = 0.644 m², A_out = 0.913 m², mean A ≈ **0.77 m²**
- Wall insulation: VIP with aged k ≈ 0.0075 W/m·K → R = 0.025/0.0075 = **3.33 m²·K/W** (a 60 mm PUR wall is R = 2.61 on the same geometry)

### 3.2 Steady-state conduction heat load [estimate]

Q = ΔT × A / R

Worst case: ambient 40 °C, setpoint 5 °C, ΔT = 35 K:

> Q = 35 × 0.77 / 3.33 ≈ 8.1 W, +15% for hinges and fasteners ≈ **9 W**

The same geometry in 60 mm PUR would leak about 12 W. VIP buys compactness: equal or better insulation at 2.5 cm instead of 6 cm.

### 3.3 Full 24-hour holdover heat budget [estimate]

| Load | Basis | Energy over 24 h |
|---|---|---|
| Conduction (ΔT=35 K, VIP 25 mm, aged) | 9 W × 86,400 s | 778 kJ |
| Door/lid openings | 4 openings × ~30 kJ allowance (air exchange is small; this covers exposed-surface and payload handling warming) | 120 kJ |
| Internal fan + sensor self-heating | ~1 W × 24 h | 86 kJ |
| Solar gain on box skin | assume vehicle-transported/shaded, ~2 W avg | 173 kJ |
| Payload | pre-conditioned to 4 °C at dispatch | 0 |
| **Total holdover thermal demand** | | **≈ 1.16 MJ ≈ 322 Wh thermal** |

### 3.4 PCM mass required [estimate]

m = Q_total / λ, with λ = 220 kJ/kg [benchmark], melt point 5–6 °C:

> m = 1.16 × 10⁶ J / 220,000 J/kg ≈ **5.3 kg** minimum

Plates (salt hydrate, ρ ≈ 1,500 kg/m³): two long-wall plates 40 × 31.3 × 1.3 cm (2.44 kg each) plus one floor plate 40 × 27.6 × 1.3 cm (2.15 kg):

> **7.0 kg of PCM, 4.7 L of panel volume, capacity 1.55 MJ → 34% margin**

The plates sit inside the wall zone, so the payload stays 30.0 L. Recharge: 1.55 MJ at 80 W of cooling = 5.4 h, overnight at the station.

Engineering cautions to state (shows depth):
- Salt-hydrate PCMs risk phase separation and loss of latent heat over cycles → specify stabilized/formulated PCM, macro-encapsulated panels, and periodic requalification.
- Paraffin PCMs (~180–200 kJ/kg, ρ ≈ 800) would need 11–13 L — too bulky. This is *why* the >220 kJ/kg benchmark matters.

### 3.5 Insulation choice [estimate]

| Wall build-up | R (m²·K/W) | Conduction @ ΔT 35 K | Cold box external | PCM |
|---|---|---|---|---|
| PUR 60 mm (previous revision) | 2.61 | ~12 W | 52.8 × 40.4 × 45.3 cm | ~9 kg |
| **VIP 25 mm (chosen)** | **3.33 (aged)** | **9 W** | **45.8 × 33.4 × 38.3 cm** | **7.0 kg** |
| PUR 40 mm (cost fallback) | 1.74 | ~18 W | 48.8 × 36.4 × 41.3 cm | ~12 kg |

VIP costs more per panel and hates punctures; the essay should state both, with the mitigations in `detail.md` §9 (skins, corner guards, compressor duty-cycle monitoring). The PUR 40 mm fallback keeps every other calculation intact with recalculated numbers if VIP is unaffordable.

### 3.6 Sensitivity analysis (what the brief demands)

- ±5 K ambient error → ±12% PCM mass.
- PCM latent heat degradation 220 → 190 kJ/kg → +16% mass → hence the 25% margin.
- One extra 5-minute door opening at 40 °C ≈ +40 kJ ≈ +2% margin consumed.
- Doubling internal fan power to 2 W → +86 kJ → +5%.
- Conclusion: **the design margin should be ≥25%, and door discipline + fan power are the second-order terms worth stating.**

---

## 4. Cooling Technology — TEC vs. Vapor Compression (Argue, Don't Assume)

### 4.1 The recharge problem defines the choice

The PCM must be re-frozen between trips. Re-freezing 7.0 kg (1.55 MJ) in 6.5 to 8 hours needs ≈ **55–65 W of continuous cooling**.

| Criterion | Thermoelectric (Peltier) | Vapor-compression (DC compressor) |
|---|---|---|
| COP @ ΔT ≈ 30–35 K | 0.3–0.6 | 1.5–3.0 |
| Electrical power to deliver 65 W cooling | **110–130 W** | 25–35 W |
| On a 216 Wh battery (20 Ah × 12 V × 90%) | lasts **< 2 h** | lasts **~8 h** |
| Moving parts / vibration | none | compressor (mitigate with rubber mounts) |
| Refrigerant | none | R600a/R290 or R134a (small charge) |
| Precise ±0.1 °C control | excellent | good |
| Maintenance | near-zero | periodic, standard refrigeration skills |
| Cost (small DC unit) | low–mid | mid |
| Suitability | **trim/maintainer, small loads** | **primary cooling + PCM freeze** |

### 4.2 Recommendation [design decision]

**DC vapor-compression as primary cooling**, for three reasons: (1) realistic PCM recharge time on solar power, (2) 3–5× better COP at tropical ΔT, (3) standard, locally serviceable refrigeration technology in both Indonesia and the Philippines.

**Thermoelectric as an auxiliary trim stage** (10–20 W): fine-tunes chamber temperature around the PCM's passive regulation, provides redundancy if the compressor circuit fails, and is used in the "quiet mode" for last-mile hand-carry where vibration-free, silent operation matters.

This hybrid answers the brief's requirement to "compare rather than assume."

---

## 5. Power System [estimate]

### 5.1 Electrical loads

| Load | Power | Energy/day |
|---|---|---|
| Compressor (PCM recharge cycle) | ~28 W electrical | ~215 Wh |
| Electronics + telemetry | ~5 W | ~120 Wh |
| **Total design electrical demand** | | **~385 Wh/day** |

### 5.2 Solar + storage

- **PV (stationary charging station, per the brief's allowance):** 385 Wh/day ÷ (4.5 peak-sun-hours × 0.8 derate) ≈ 107 W → **150 W panel** (200 W for more cloudy-day margin). Indonesia/Philippines insolation ≈ 4–5 kWh/m²/day supports this year-round.
- **Battery:** the transit maintain load is 11.5 W (9 W leak ÷ COP 2, plus fan and electronics) → **12 V 20 Ah LiFePO₄ (240 Wh, 216 usable)** covers about 18 h of maintaining. The 24 h passive promise rests on the PCM, which is what lets the battery be this small. LiFePO₄ chosen for thermal stability, 2,000+ cycles, no thermal-runaway class risk — a safety argument worth stating explicitly in a *medical* context.
- Box can accept vehicle 12 V while driving; PV station recharges battery + PCM overnight at the health-facility hub.

---

## 6. IoT Telemetry & Trust Architecture

### 6.1 Sensor array

- **3× calibrated temperature probes** (PT1000 Class A, ±0.16 °C @ 5 °C) placed at geometric positions identified by temperature mapping; sensor voting (median) for control, min/max for excursion logic.
- Door/lid reed switch, accelerometer/vibration logger (brief requires vibration mitigation — mounts + logging), GPS (2.5 m target with SBAS/dual-band under open sky), battery/charge state, humidity and barometric pressure (SHT4x + BMP390 class) so excursions can be correlated with weather.
- Sampling **30 s [benchmark]**; local ring buffer in flash ≥ 72 h (~0.5 MB for a week — trivial, so buffer generously). Fallback ladder: LTE-M first, NB-IoT second on the same module, then the 72 h buffer, sync on reconnect.

### 6.2 Failure-response matrix (this is where essays win or lose)

| Failure | Detection | Automatic response | Human protocol |
|---|---|---|---|
| Sensor fault (stuck/drift/out-of-family) | cross-sensor voting + rate-of-change checks | mark channel suspect, control on median, flag log | swap to pre-calibrated spare probe |
| Door left open | reed switch + temperature rate-of-change | local buzzer ≤ 30 s, push alert | closure SOP, note in custody log |
| Battery low | coulomb counting | priority power to logging/GPS, shed comms | scheduled return / PV recharge |
| Cellular lost | heartbeat timeout | **store-and-forward**, sync on reconnect | no action needed; audit trail intact |
| Route delay | GPS + ETA model vs. holdover runway | predictive alert: "hours of holdover remaining" | divert to nearest handover point |
| Compressor failure | current signature + temp trend | TEC trim holds band briefly; PCM takes over | holdover clock starts — 24 h runway, dispatch recovery |
| Excursion > 8 °C | 30 s sampling → detect ≤ 30 s | alarm immediately; at 15 min cumulative → auto-quarantine flag on shipment record | QA decision workflow (§7) |

**Alarm latency commitment:** detect ≤ 30 s (sampling interval), local alert ≤ 30 s, remote alert ≤ 2 min when connected. Testable, defensible.

### 6.3 Trustworthy records (and honest limits)

- **Hash-chained, signed event log** (Ed25519): each 30 s record links to the previous hash; daily root hash optionally anchored to a permissioned ledger / GS1 EPCIS event stream. Handover = dual signed QR receipts (dispatcher ↔ receiver).
- **State plainly (the brief demands it):** cryptography proves records weren't altered *after* the fact; it cannot prove the sensor was accurate or the handler honest. Therefore pair it with:
  - calibration certificates traceable to national standards (ISO/IEC 17025 labs),
  - periodic ice-point field verification (0 °C check, monthly),
  - plausibility analytics (sensor voting, impossible-rate detection),
  - role-based access + audit logging of every human override.
- **Privacy:** no patient data on the box or in the log — shipment IDs are pseudonymous; location data truncated for non-authorized roles; access by role (courier: own shipments; QA: excursion reviews; auditor: read-only). Align with Indonesia's PDP Law and the Philippine Data Privacy Act. Data minimization is the cheapest privacy control.

---

## 7. Excursion Decision Workflow

When > 8 °C for > 15 min cumulative [benchmark triggers, decisions follow product rules]:

1. Shipment auto-flagged **QUARANTINE** — receiver cannot close custody without a QA disposition.
2. Evidence bundle exported automatically: full temperature curve, excursion duration/magnitude, which sensors, door events, GPS timeline.
3. Decision authority: national immunization programme / product stability data (some products tolerate brief excursions; none may be assumed to). VVM (vaccine vial monitor) status is checked for vaccines that carry one.
4. Default disposition when evidence is insufficient: **do not use.** "When in doubt, throw it out" — cheaper than a harmed patient.

---

## 8. Validation & Pilot Plan (Realistic, Testable)

### 8.1 Laboratory qualification (before any real product)

| Test | Protocol sketch | Pass criterion |
|---|---|---|
| Calibration | 3-point (0/5/10 °C) against ISO 17025-traceable reference | within ±0.2 °C |
| Temperature mapping | 9-point grid (3×3), empty + loaded, 43 °C ambient | every point within 2–8 °C, spread ≤ 2 K |
| **Holdover demonstration** | pre-cool to 4 °C, 20 L water-equivalent payload, 43 °C chamber, power off, log until warmest probe crosses 8 °C | **≥ 24 h [benchmark]**; report the margin |
| Door-opening cycle | 4 × 60 s openings at 40 °C ambient | no excursion > 15 min |
| Pull-down | from 35 °C payload to 5 °C | ≤ 4 h |
| Alarm latency | scripted excursions, measure detect→notify | local ≤ 60 s, remote ≤ 2 min |
| Vibration | road/vehicle shaker profile | no PCM panel damage, no sensor shift, log intact |
| Water spray | IPX4 spray on all faces, 5 min each, vents closed as shipped | no ingress at seams; vents and bay floor dry |
| Data integrity | attempt record edit/insertion after the fact | hash chain verification fails loudly |
| GPS accuracy | against surveyed points, open sky + urban | ≤ 2.5 m typical, characterize worst case |

### 8.2 Baseline spoilage & excursion study (the brief's explicit question)

Before claiming impact, run a **6-month observational baseline** on target routes:

- retrofit existing transport with loggers only (no intervention),
- measure: % shipments with any excursion, % with > 15 min excursions, mean excursion duration, seasonal split (dry/rainy),
- link to QA discard/spoilage records to establish the **route-specific** baseline that replaces the hypothetical "up to 25%" figure,
- then run the pilot arm on the same routes and compare — this turns a hypothetical number into local evidence, which is exactly what Section 1 of the brief asks for.

### 8.3 Pilot design

- 10 units, 2 routes (one island/coastal in the Philippines, one rural Central Java), 3 months.
- Primary endpoints: excursion-free shipment rate, holdover compliance, alarm latency in the field, data completeness (sync success rate).
- Human factors: health-worker task time, training duration, error rates — because "how a health worker can trust it" is the brief's final message.

---

## 9. Cost Analysis [estimates — label as such]

**Unit CAPEX (target: affordable for remote communities):**

| Item | Est. cost (USD) |
|---|---|
| Insulated box + VIP panels + PCM plates (7 kg) | 380–560 |
| DC compressor cooling unit | 150–300 |
| TEC trim module + heatsinks | 30–60 |
| LiFePO₄ 12 V 20 Ah battery (flat) | 90–140 |
| 150 W PV + charge controller (shared charging station) | 90–150 |
| Electronics (MCU, LTE-M, GPS, 3× PT1000, enclosure) | 100–180 |
| Assembly, calibration, certification | 100–200 |
| **Total per unit** | **≈ 940–1,790** |

**5-year TCO per unit:** + 1 battery replacement (~120), annual calibration (~50/yr), LTE-M/NB-IoT plan (~$3–6/month), maintenance spares (~50/yr), training amortized → **≈ $1,700–2,800 over 5 years**, i.e. **$28–47/month**. Compare against the cost of a single wasted vaccine shipment and the baseline spoilage rate measured in §8.2 — that comparison *is* the economic argument.

**Environmental & social:** solar-primary energy, R600a/R290 low-GWP refrigerant option, PCM recyclability; local assembly and technician training in Kudus/Semarang and Cavite as the community-capacity argument.

---

## 10. Limitations to State Proactively (scores honesty points)

1. This is a conceptual design; not a validated medical device (brief's own scope note).
2. All thermal numbers assume stated material properties; prototype testing will revise them.
3. Cryptography secures records, not reality — calibration and human protocol carry that burden.
4. The 15-min excursion benchmark is scenario-specific; product labels govern real decisions.
5. The 25% spoilage figure is a prompt; §8.2 is how we'd replace it with local data.
6. LTE-M/NB-IoT availability is operator-dependent; the 72 h store-and-forward buffer is the mitigation, not an assumption of coverage.

---

## 11. Essay Outline (mapped to the required structure, §7 of brief)

1. **Title + Executive summary** — the 5-line pitch: 30 L box in a 46 × 33.5 × 57.5 cm body, 2–8 °C, 24 h+ holdover on ~7 kg PCM, VC primary + TEC trim, solar charging station, signed hash-chain custody, ~$1–1.8 k CAPEX.
2. **Introduction & problem** — island/rural cold chain, outage + transit + monitoring gaps; cite WHO cold-chain guidance.
3. **Requirements & assumptions** — table from §2, every number tagged benchmark vs. estimate.
4. **Architecture & justification** — §3–6; include the system diagram (redraw the brief's flow with our hybrid choice).
5. **Key calculations** — §3 heat budget + PCM mass + sensitivity table; §4 TEC/VC comparison table.
6. **Operations, risk, validation** — failure matrix (§6.2), excursion workflow (§7), test plan + pilot (§8).
7. **Economic/environmental/social** — §9 TCO + local capacity.
8. **Limitations & recommendations** — §10.
9. **Conclusion** — return to the brief's final message: design for reliability when conditions are not ideal.
10. **References (APA 7)** — WHO PQS (E004/E03 cold-chain equipment specs), WHO Immunization in Practice, GS1 EPCIS 2.0, PT1000/IEC 60751, ISO/IEC 17025, Indonesia PDP Law, Philippine DPA (RA 10173), PCM literature for salt-hydrate stabilization.

**Formatting reminders:** A4, Times New Roman 12 pt, 1.5 spacing, 2.54 cm margins, PDF; label every figure/table; distinguish benchmark values from estimates everywhere.

---

## 12. Academic Integrity Note

The brief (§9) requires participant's-own analysis and **disclosure of permitted AI-tool use per organizer rules**. Use this document as your engineering scaffold and verify every number yourself — recalculate, don't copy-paste. Disclose AI assistance if the organizers' rules require it.
