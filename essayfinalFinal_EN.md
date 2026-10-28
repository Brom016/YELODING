# YELODING: a hybrid PCM and vapor-compression cold-chain box with offline temperature logging that keeps vaccines at 2–8 °C for 24 hours to remote islands

*International Student Essay Challenge, Case Study 5: Smart IoT-Enabled Solar Cold Storage Unit for Medical & Vaccine Supply Chains. Universitas Wahid Hasyim, Universitas Muria Kudus, Cavite State University. Group 5.*

> **Submission note.** This manuscript follows the organizer's format requirements (A4, Times New Roman 12 pt, 1.5 spacing, 2.54 cm margins, APA 7th edition referencing). Every figure carries a placeholder; the source drawings live in `gamtek.html` and the web interface in `wokwi/dashboard.html`. Labels: **[benchmark]** values are supplied with the case benchmarks (Table 1), **[estimate]** marks our calculations with stated assumptions, **[sim]** marks logic verified in the Wokwi simulation, and **[verify]** marks items that still need manufacturer datasheets. The manuscript is a conceptual engineering case study, not a validated medical-device specification.

## Executive summary

Problem. Vaccines, biological reagents, and other temperature-sensitive medical supplies must be transported at 2–8 °C. In remote island and coastal areas, these products are often damaged before they arrive: the grid fails, the box is opened repeatedly, outside temperatures run high, and journeys stretch long. The damage stays invisible. The vaccine looks normal while its protection has declined. The consequences are concrete. Indonesia recorded 63,769 suspected measles cases and 69 deaths in 2025, and in Sumenep 16 of the 17 children who died had never been immunized (Kementerian Kesehatan RI, 2025; WHO Indonesia, 2026).

Solution. We propose YELODING, a 30 L vaccine box [benchmark] built on a hybrid architecture. During transport, phase-change material (PCM) and vacuum insulation hold the temperature for at least 24 hours [benchmark] without any power. At a stationary recharge point, an AC vapor-compression compressor refreezes the PCM in about two hours. Power comes from a 100 Ah LiFePO4 battery through a pure sine inverter, with a 20 W panel on the lid as a supplementary charger. The monitoring layer consists of three temperature probes, an ambient sensor, a pressure sensor, an accelerometer, a lid switch, GNSS, an OLED, three LEDs, and a buzzer that work fully offline. Temperature logs are chained by hash and signed by the device, then synchronized over LTE-M/NB-IoT when a network appears. The device enforces its own governance rule: a cumulative excursion past 15 minutes [benchmark] latches the box into QUARANTINE until a QA officer releases it. The name joins "yelo" (ice, Tagalog) and "dingin" (cold, Indonesian), with "ding!" as the sound of its alarm; it photographs the two partner countries in one word.

Evidence. Design calculations [estimate] give a heat leak of 9 W at 40 °C ambient because of 25 mm vacuum insulation panels, so 7.04 kg of PCM (1,549 kJ) covers the 24-hour budget of 1.16 MJ with a 34% margin. The control logic, alarms, PCM budgeting, hash chain, and quarantine flow have been verified end to end in a Wokwi simulation with eight passing scenarios (Group 5, 2026d).

Conclusion. The approach is workable and honest about its physical limits. The largest constraints are weight, about 48 kg empty, and the dependence on a stationary recharge point. The next steps are a 24-hour cold-life test in a 42 °C chamber with calibrated reference sensors, then a field pilot.

## 1. Introduction and problem definition

A cold chain is like any chain: its strength is set by its weakest link. In cities, that link is a refrigerator on a reliable grid. On remote islands, the weakest link is the last mile: travel by motorcycle, small boat, and foot, under a tropical sun, without dependable power or signal. Vaccination itself is one of the most effective public-health instruments in history, yet its benefit collapses the moment a vial warms or freezes outside its storage range (Montero et al., 2024). Vaccine distribution into such settings is a recognized logistics problem: prioritization, routing, and cold-chain capacity interact, and each failure compounds the others (Shahparvari et al., 2021).

Vaccines and temperature-sensitive biologics lose potency quickly at extreme temperatures, hot or cold, especially during transport and storage; the recommended storage band for most routine vaccines is 2–8 °C (Jiang et al., 2024). This essay covers routine immunization vaccines in that band. Frozen and ultra-cold products are out of scope. We use measles and HPV as examples because they expose two different risks. The measles-rubella vaccine is freeze-dried and sensitive to heat and light, so a temperature spike in transit is its main threat. The HPV vaccine is sensitive to freezing, so temperatures that run too cold near a cooling element are also dangerous. A design that protects both must hold the temperature near the middle of the range, not at either edge.

The stakes are high. Across 2025, Indonesia recorded 63,769 suspected measles cases, 11,094 laboratory-confirmed cases, and 69 deaths, a 147 percent rise in suspected cases over 2024 (Kementerian Kesehatan RI, 2025). Reported first-dose measles-rubella coverage fell from 92 percent in 2024 to 82 percent in 2025 (Media Indonesia, 2025). The worst outbreaks cluster in pockets of low immunization: in Sumenep Regency, 16 of the 17 children who died had never been immunized (WHO Indonesia, 2026). For HPV, WHO records about 36,000 new cervical cancer cases and 21,000 deaths per year in Indonesia, with roughly 70 percent diagnosed at a late stage, against a government target of immunizing 90 percent of 15-year-old girls by 2027 (WHO & UNFPA, 2024).

Heat and freeze damage is dangerous because it is invisible. A vaccine that has been overheated or frozen does not change color and has no smell. A child receives the injection and feels protected, while the protection may have declined. Some observers point to community hesitancy and low coverage as the main drivers of outbreaks. Our argument is narrower: a failing cold chain deepens gaps that already exist, and temperature evidence helps rebuild trust.

The main question, stated in the case brief, is this: how can an IoT-enabled, solar-supported cold-chain system keep vaccines and medical supplies within quality limits, keep operating through power and network disruptions, and deliver trustworthy custody records at a cost remote communities can afford? Our thesis follows the structure of our earlier draft: the PCM carries the thermal load, the stationary compressor carries the recharge, small solar carries the data, and evidence carries trust.

## 2. Design requirements and assumptions

### 2.1 Mapping the organizer's benchmarks

Table 1 compares the benchmark dataset supplied with the case against our design. Benchmark values are marked [benchmark]; everything we derived is marked [estimate].

Table 1. Benchmark values and their treatment in the design.

| Parameter | Benchmark [benchmark] | Our design | Status |
|---|---|---|---|
| Storage volume | 30.0 L | 30.0 L net (400 × 250 × 300 mm), three trays | Met |
| Operating temperature | 2.0–8.0 °C | Hysteresis control at 5–7 °C, alarm at 8 °C | Met [sim] |
| Extreme ambient | 38–42 °C | Designed at 40 °C, tested at 42 °C | Met |
| PCM latent heat | > 220 kJ/kg | Salt hydrate at 220 kJ/kg [verify datasheet] | Equal |
| Passive holdover | ≥ 24 h | 24 h at ΔT 35 K, 34% margin | [estimate, test pending] |
| Sampling interval | 30 s | 30 s | Met [sim] |
| Cellular fallback | LTE-M / NB-IoT | SIM7080, both bands, plus 72 h buffer | Met |
| Excursion limit | 15 min | Automatic QUARANTINE latch | Met [sim] |
| GPS accuracy | 2.5 m | 2.5 m target; 3–6 m expected on a side antenna | [estimate] |

### 2.2 Success criteria

Our temperature criterion is tighter than the safe limit: control runs in a 5–7 °C band, leaving room for sensor error and response delay. Alarm criteria: LEDs and the buzzer respond within 30 s locally, telemetry reaches the platform within 2 min when a link exists. Governance criteria: a cumulative excursion past 15 minutes latches QUARANTINE until QA releases the box, and the device cannot forget the event. Cost criterion: about IDR 23.7 million per unit with contingency, calculated in Section 6.

### 2.3 Assumptions and boundaries

The brief prescribes no power consumption, battery capacity, vehicle profile, or PCM mass, and asks for transparent estimates with sensitivity to key assumptions. Six assumptions drive the numbers most: the VIP conductivity of 0.0075 W/m·K in the aged condition; a compressor input of 145 W from a scenario range of 130–180 W; an inverter efficiency of 0.90; an energy price of IDR 1,500 per kWh; grid availability at the recharge point; and at most four lid openings per trip. Section 4.5 shows the effect of each.

Ethical boundaries follow the case rules. The prototype will be tested with calibrated reference sensors and a documented temperature-mapping protocol before it carries real vaccines (WHO, 2011). Cryptography makes the log hard to alter, but it cannot prove that a sensor is accurate or that a handler behaved; calibration and physical seals remain necessary. No patient-identifiable data is stored, in line with Indonesia's Personal Data Protection Law (Republik Indonesia, 2022) and the Philippine Data Privacy Act (Republic of the Philippines, 2012).

## 3. System architecture and technical justification

### 3.1 System flow

The case concept proposes a flow of solar and power input, thermal management, the 2–8 °C storage chamber, then the route and fleet dispatch layer, the IoT sensor array, and a secure telemetry platform. We keep that flow and add a stationary recharge path and an automatic quarantine control.

**[Figure 1 placeholder]**

*Figure 1.* System block diagram of the YELODING box: PV on lid, MPPT A/B, 100 Ah battery, inverter, GQR30TG compressor, condenser, evaporator, PCM, payload chamber, DC rail, sensor set, ESP32 logger, LTE-M link, and hash-chained dashboard.

*Note.* Authors' drawing, after the internal design document (Group 5, 2026a).

### 3.2 Two tiers and external dimensions

The box has two stacked tiers. The upper tier is the cold box, 458 × 334 × 383 mm, holding the payload, PCM, evaporator, and insulation. The lower tier is the machine bay, 490 × 350 × 332 mm, holding the compressor, condenser, battery, inverter, MPPT units, fuse panel, and electronics. A separator of 15 mm PUR plus 2 mm aluminium divides them. The footprint steps outward because the 100 Ah battery sets the width; total height is 742 mm including the PV deck. Empty mass is about 48 kg, about 63 kg loaded with a 15 kg payload (Group 5, 2026b). Section 4.3 states the weight constraint plainly.

The wall builds inward as follows: 13 mm PCM on the two long walls and the floor, a 2 mm food-grade PP liner, 25 mm vacuum insulation panels, and a 2 mm HDPE skin. A 12 mm aluminium evaporator plate sits in the floor under the PCM. The lid measures 415 × 285 mm, is rear-hinged, opens to roughly 120°, and carries a double-lip gasket and a tamper-seal hasp.

**[Figure 2 placeholder]**

*Figure 2.* General arrangement of the YELODING box, isometric projection with principal dimensions in millimetres and the PV cover partly open.

*Note.* Authors' drawing GA-01 (`gamtek.html`).

**[Figure 3 placeholder]**

*Figure 3.* Cold box wall section at large scale: liner 2 mm, PCM 13 mm, VIP 25 mm (aged k = 0.0075 W/m·K), HDPE 2 mm, with the heat-flux calculation.

*Note.* Authors' drawing SEC-01 (`gamtek.html`).

### 3.3 Solar input and the stationary recharge point

The case concept allows the solar panel to charge a battery or support stationary recharging without being mounted on the box. We take both, with honest proportions. The on-board panel is only 20 W, about 65 Wh per day, because the lid footprint caps its size; its job is to sustain telemetry. Bulk recharging belongs to the stationary point: a 14.6 V / 20 A grid charger, or a 200 W foldable PV for health posts without a grid. Our calculation also strengthens the case for large panels off the box: a large panel on the lid adds solar heat to the very surface we are trying to insulate, so mounting it at the station protects the load.

### 3.4 Thermoelectric or vapor compression: compared, not assumed

The case asks for a comparison of thermoelectric and vapor-compression cooling rather than an assumption that either is always superior. The literature supports both paths for solar-powered vaccine storage: a photovoltaic Peltier unit has been shown to hold 2–8 °C for up to three days with 1 °C control accuracy (Buitendach et al., 2020), and a solar photovoltaic thermoelectric micro cold store met WHO carrier conditions for last-mile delivery (Nadimuthu & Victor, 2021). Peltier systems are simple and vibration-free, but their coefficient of performance falls steeply exactly where our box operates, freezing PCM below its melt point. Table 2 summarizes the comparison under this box's working conditions.

Table 2. Cooling options under YELODING's operating conditions.

| Aspect | Peltier | Vapor compression (GQR30TG via inverter) | Passive PCM |
|---|---|---|---|
| COP while freezing PCM | 0.3–0.6 | about 1.5 [estimate, datasheet [verify]] | not applicable |
| Electrical power | 20 W (trim) | 145 W [estimate; range 130–180 W] | 0 W |
| Role | DC backup if the inverter or compressor fails, about 31 h | refreezing at the station, maintenance in transit | main carrier for 24 h |
| Vibration and noise | low | present, damped by rubber mounts | none |
| Power dependence | direct DC | AC through inverter | none |
| Moving parts | none | present, a mechanical failure point | none |

The conclusion is contextual. Peltier suits a low-power trim on the DC rail, and that is its role here, consistent with the photovoltaic Peltier results in the literature (Buitendach et al., 2020). Vapor compression moves more heat per watt of electricity, so it serves the stationary recharge and maintenance duty. Passive PCM wins when no power exists at all, so it carries the journey. The design uses all three in their proper roles.

**[Figure 4 placeholder]**

*Figure 4.* Refrigerant and airflow schematic: compressor, condenser with two 120 mm fans, capillary, evaporator plate inside the PCM jacket, suction line through the separator, and bay airflow from inlet to exhaust.

*Note.* Authors' drawing REF-01 (`gamtek.html`).

### 3.5 Components that protect quality inside the payload

The PCM melt point is 5–6 °C: above 2 °C so it cannot freeze the vaccine, below 8 °C so it still stores cold. The PCM sits in the walls and floor, never against the vials. Ten-millimetre standoff bosses form air channels, and an 80 mm circulation fan evens out the temperature. The probes sit inside buffer bottles filled with water or glycol that mimic vial thermal mass, so readings approximate the vaccine temperature rather than the air temperature. DS18B20 probes are a proven choice for this class of cold-chain monitor: an IoT cold-chain box built on the same sensor with an ESP8266 reached better than 95 percent accuracy against reference readings (Putra et al., 2025). The evaporator plate runs at −6 to −8 °C while freezing the PCM, but the 5–6 °C PCM layer shields the vials from that surface.

Vibration mitigation follows the design challenge in the case: the compressor sits on four 30-Shore rubber mounts, the fans on grommets, the PCM in foam slots with standoff bosses, the electronics in a foam-potted box, four M6 tie-down eyes secure the box to a vehicle, and the accelerometer converts sustained shaking into a logged event.

For operation at altitude, up to 3,000 m, the wall carries a pressure-equalization valve. Without it, a box sealed warm at sea level and carried to 2,500 m holds about 18 kPa of excess pressure, roughly 2.1 kN of uplift on the lid (Wikipedia contributors, 2026). The valve neutralizes this within seconds.

**[Figure 5 placeholder]**

*Figure 5.* Interior cutaway, isometric section: three trays with probes T1/T2/T3, wall and floor PCM, evaporator plate with copper serpentine, circulation fan, TEC fin block, and the machine tier below with battery, inverter, MPPT A/B, compressor, condenser, fuse panel, and AC outlet.

*Note.* Authors' drawing ISO-01 (`gamtek.html`).

### 3.6 Data integrity, time, and telemetry

A log without trustworthy time is not trustworthy. A DS3231 RTC (±2 ppm) is disciplined by the GNSS pulse-per-second output; every record carries a clock-source flag; position gaps are logged as GPS OUTAGE events and never interpolated. Sampling every 30 s [benchmark] produces about 2,880 readings per sensor per day, a few tens of kilobytes per week, so a 72 h local buffer [benchmark] is cheap.

Each record links to the hash of the previous record, FNV-1a in the simulation and device-signed Ed25519 in the hardware. Editing one old record breaks every link after it (Group 5, 2026d). The log is stored locally in a store-and-forward pattern and synchronized over LTE-M or NB-IoT when a network appears. MQTT is the transport for the same reason it is used in medicine-transport monitoring systems: lightweight publish/subscribe over constrained links, with retained state for late joiners (Bhatti et al., 2024). An IoT framework for vaccine cold chains further argues that authenticated devices are what make surveillance data trustworthy (Jiang et al., 2024), which is why our hash chain and device signature sit under the telemetry rather than on top of it. No patient-identifiable data is stored; position is truncated to four decimals, about 11 m, for non-QA roles, in line with data-protection law in both partner countries (Republik Indonesia, 2022; Republic of the Philippines, 2012).

The monitoring dashboard shows the temperature trace against the 2–8 °C limits, the state badge, the PCM reserve, the event log, the hash chain, and the route map. It is gated to sender-only access because the public demo broker is world-readable; a real deployment uses an authenticated broker over TLS with per-device keys. Remote commands are recorded in the hash chain as REMOTE CMD entries, so remote control is fully auditable.

**[Figure 6 placeholder]**

*Figure 6.* Web dashboard, sender view: connection bar, temperature chart against the 2–8 °C limits, state badge, PCM reserve meter, event log, hash chain list, and route map with the simulated Semarang to Kudus track.

*Note.* Screenshot of `wokwi/dashboard.html` (Group 5, 2026d).

**[Figure 7 placeholder]**

*Figure 7.* Dashboard authentication gate: sender access code prompt that gates every monitoring and control function.

*Note.* Screenshot of `wokwi/dashboard.html` (Group 5, 2026d).

### 3.7 Health worker workflow

The health worker receives a filled box: PCM cold, battery full, seal intact. She loads the vaccines and presses the handover button. During the trip she reads the lamp colors; the sender watches the map and temperatures on the dashboard. At the destination, the receiver verifies the hash receipt, breaks the seal, and the status page shows the peak temperature and the time outside the range. If the box has latched QUARANTINE, the batch is not used until a QA decision follows the product label and WHO or national guidance. The system presents evidence; the human decision stays with humans and guidelines.

## 4. Key calculations and benchmark comparison

### 4.1 The dominant heat load and the choices that reduce it

The brief asks which heat load dominates under the specified ambient and which design choices reduce it most. The calculation follows.

Assumptions [estimate]: cold box 458 × 334 × 383 mm, mean wall area 0.77 m2, VIP 25 mm at an aged conductivity of 0.0075 W/m·K so R = 3.33 m2K/W, design ambient 40 °C, target 5 °C.

```
Q = ΔT × A / R = 35 × 0.77 / 3.33 = 8.1 W
plus 15% thermal bridging  = 9 W
at 42 °C (ΔT 37 K)         = about 10 W
```

Conduction through the walls is the dominant load, about 85 percent of the 24-hour budget. The design choice that reduces it most is the vacuum insulation. Our earlier draft used 50 mm polyurethane foam, a 19 W load, and needed 11 to 12 kg of PCM. The 25 mm VIP cuts the load to 9 or 10 W and the PCM to 7.04 kg. The full 24-hour budget is: conduction 778 kJ, lid openings 4 × 30 kJ, fan and sensors 86 kJ, solar gain on the dark skin 173 kJ, total about 1.16 MJ.

### 4.2 PCM mass and the right margin

The brief asks how much PCM is needed for the 24-hour target and what margin is appropriate.

```
m = Q / λ = 1,160,000 / 220,000 = 5.3 kg   theoretical minimum
installed = 7.04 kg × 220 kJ/kg = 1,549 kJ
margin    = (1,549 - 1,160) / 1,160 = 34%
```

The 34% margin covers PCM ageing, 42 °C days, extra lid openings, and operators who follow the procedure less strictly than the SOP. A larger margin adds weight without a demonstrated need; a smaller one removes the room for error. The installed plates sit inside the wall zone, so the payload stays at 30.0 L [benchmark].

### 4.3 Weight, stated plainly

The empty box weighs about 48 kg, about 63 kg loaded. That is not as light as a food-delivery carrier, and we will not claim it is. We define portable honestly: a two-person lift, a mandatory trolley, four M6 tie-down eyes for strapping to a motorcycle or boat, and a low center of gravity because the battery sits on the tier floor. Our first draft targeted 18 to 20 kg; we dropped that target because it forced compromises we were not willing to hide.

### 4.4 Energy budget and autonomy

Table 3. Electrical loads.

| Load | Power | Rail |
|---|---|---|
| Electronics, sensors, GNSS, LTE, OLED | 5 W | 5 V DC |
| Circulation fan + two condenser fans | about 6 W | 12 V DC |
| Compressor through inverter | 161 W DC-side while running | 145 W divided by 0.90 |
| Inverter standby (eco) | 2 W | [verify] |

A normal operating day needs about 810 Wh: PCM recharge for 2.1 h at 338 Wh, transit at a 5% duty for 177 Wh, standby for 44 Wh, and DC loads for 264 Wh. An extreme 42 °C day needs about 900 Wh. Autonomy from 1,024 Wh usable (80% DoD) is 94 h for passive holding plus telemetry, about 30 h of active operation, and 31 h on the TEC alone if the inverter fails.

Table 4. Sensitivity to the compressor input assumption, as the brief requests.

| Scenario | Input | COP | Daily energy | Active autonomy |
|---|---|---|---|---|
| Optimistic | 130 W | 1.69 | 756 Wh | 32 h |
| Baseline | 145 W | 1.52 | 810 Wh | 30 h |
| Pessimistic | 180 W | 1.22 | 928 Wh | 27 h |

The on-board 20 W panel contributes about 65 Wh per day. That sustains telemetry and stretches passive autonomy to about five days. It never covers cooling; bulk recharging belongs to the stationary point. Through a cloudy spell, the battery bridges about 3.8 days without sun.

### 4.5 Operation at altitude

The design envelope extends to 3,000 m. Two risks are addressed. First, pressure: the equalization valve neutralizes the 18 kPa differential at 2,500 m. Second, thin air: cooling capacity falls 10 to 20 percent at 2,000 m, a rule of thumb of 5 to 10 percent per 1,000 m, but the colder ambient keeps the condensing temperature near 34 °C, better than 50 °C at the coast. The BMP390 logs altitude with every record and raises an ALTITUDE HIGH event above a 2,000 m threshold. The compressor's altitude rating is a mandatory datasheet item (Embraco, 2019; Schneider Electric, 2011).

### 4.6 Benchmark comparison summary

Sensitivity to the three largest assumptions reads as follows. The 9 W heat leak depends on the VIP; if the vacuum fails and conductivity drifts toward 0.02 W/m·K, the load triples and the 24-hour promise dies, which is why compressor duty cycle is monitored as an early detector. The 145 W compressor input spans 130 to 180 W and moves active autonomy between 30 and 27 h; recharging remains possible in every scenario. The energy price of IDR 1,500 per kWh touches only the monthly operating cost of about IDR 36,000 and does not change the architecture.

## 5. Operational plan, risk analysis, and validation strategy

### 5.1 Response to failures

The brief asks how the system responds to a sensor fault, a door left open, a depleted battery, a lost cellular signal, and a route delay. Table 5 answers each; rows marked sim have been executed in the simulation.

Table 5. Failure-response matrix.

| Failure | Detection | Automatic response | Human procedure |
|---|---|---|---|
| Sensor fault or drift | cross-probe voting, rate-of-change check | channel flagged, control moves to the median | fit a calibrated spare probe |
| Lid left open | reed switch + temperature rate | buzzer within 30 s, PCM drain 1.3x, logged | closure SOP, note in log [sim] |
| Battery depletion | voltage divider | yellow at 11.0 V, compressor shed at 10.5 V, logging prioritized | return to station [sim] |
| Cellular loss | heartbeat timeout | store-and-forward, sync on reconnect | no action needed, audit trail intact |
| Route delay | GPS + holdover estimate | alert with remaining safe hours | divert to the nearest handover point |
| Compressor failure | zero tach, temperature trend | TEC 20 W holds about 31 h | holdover clock runs, recovery dispatch |
| Excursion > 15 min | 30 s sampling | QUARANTINE latch, evidence export | QA decision [sim] |
| VIP vacuum loss | rising duty-cycle trend | early warning before the 24 h promise is at risk | panel inspection at the base stop |

### 5.2 Evidence for a batch decision after an excursion

When the QUARANTINE latch sets, the box exports an evidence bundle: the complete temperature curve, the magnitude and duration of the excursion, which sensors read what, lid events, the GPS track, and the time source. The decision follows the product label and national or WHO guidance; a vaccine vial monitor is checked where present. If the evidence is insufficient, the default disposition is do not use. Discarding one batch is cheaper than risking one child.

### 5.3 Verification in the Wokwi simulation

Before a single physical component is purchased, the control logic runs in a Wokwi simulation: an ESP32, two DS18B20 probes, a DHT22, an OLED, a buzzer, three LEDs, three buttons, a power slide switch, and a battery potentiometer, connected to a public MQTT broker and a web dashboard (Group 5, 2026d). Eight test scenarios all pass.

**[Figure 10 placeholder]**

*Figure 10.* Photograph or screenshot of the Wokwi simulation: circuit view and serial monitor showing hash-chained records.

*Note.* From `wokwi/sketch.ino` (Group 5, 2026d).

Table 6. Wokwi test scenarios.

| # | Scenario | Pass criteria | Status |
|---|---|---|---|
| S1 | Normal operation | OLED OK, PCM 100%, chain grows, no alarms | Pass [sim] |
| S2 | Hysteresis | compressor on at 7 °C, off only below 5 °C | Pass [sim] |
| S3 | Power loss | PASSIVE-HOLD, PCM drains with delta T | Pass [sim] |
| S4 | Lid open | DOOR OPEN event, 1.3x PCM drain | Pass [sim] |
| S5 | Excursion quarantine | 15 story-minutes, QUARANTINE latch | Pass [sim] |
| S6 | Low battery | yellow at 11.0 V, compressor shed at 10.5 V | Pass [sim] |
| S7 | Handover | hash receipt printed for the receiver | Pass [sim] |
| S8 | Tamper test | editing one record breaks the chain | Pass [sim] |

The simulation firmware and the real device share the same control structure. Only the peripherals change: three probes instead of two, real LTE-M, real GNSS.

### 5.4 Physical validation

The test plan answers the brief's questions on sensor calibration, alarm latency, temperature uniformity, holdover time, and data integrity (WHO, 2011). Table 7 lists the tests.

Table 7. Validation plan.

| Test | Method | Pass criteria |
|---|---|---|
| 24 h cold life | 42 °C chamber, calibrated reference sensors | 2–8 °C held for 24 h [benchmark] |
| Temperature mapping | nine points per WHO (2011) | coldest-to-warmest spread inside the band |
| Sensor calibration | comparison at 0 °C and 5 °C against an ISO/IEC 17025 reference | deviation <= 0.5 °C |
| Alarm latency | injected excursion | local 30 s, remote 2 min |
| Holdover | full PCM, no power, 42 °C | >= 24 h [benchmark] |
| Data integrity | tamper test, RTC swap, network cut | chain break detected, gaps logged [sim] |
| Compressor start | measured LRA vs inverter surge | 10 starts without trip [verify] |
| Vibration and drop | shaker profile + 200 km mixed road | no plate chafing, chain intact |
| Water and corrosion | salt spray, simulated rain | IPX4 upright |
| GNSS accuracy | P50 and P95 on real routes | reported as a distribution, not a best case |

### 5.5 Baseline spoilage data

The 25 percent spoilage figure sometimes quoted is hypothetical, not a finding. The pilot will attach loggers to existing delivery routes for several weeks, then compute the percentage of trips that leave 2–8 °C and the durations involved. That number becomes the baseline for judging the box's benefit. We state this method up front so the essay does not lean on an invented figure.

## 6. Economic, environmental, and social impact

### 6.1 Budget per unit (lowest-price scenario)

The brief asks for full life-cycle costs, including battery replacement, calibration, connectivity, maintenance, and training. Table 8 uses the lowest price found for each component as a budget floor, at IDR 18,000 per USD (Group 5, 2026c).

Table 8. Cost breakdown per unit.

| Block | Cost (IDR) | Approx. USD |
|---|---|---|
| Cold box: shell, VIP, liner, PCM 7.04 kg, evaporator, gasket, latches, pressure valve, PV cover, trays | 6,955,000 | 386 |
| Machine tier: GQR30TG compressor, condenser, 100 Ah battery, 1,000 W inverter, dual MPPT, 20 W panel, grid charger, TEC, fuses, shell | 9,270,000 | 515 |
| Electronics and telemetry: ESP32, 3x DS18B20, DHT22, BMP390, MPU-6050, OLED, SIM7080, GNSS, RTC, RCD, enclosure | 1,895,000 | 105 |
| **Total BOM** | **18,120,000** | **1,005** |
| Assembly, refrigerant brazing, initial calibration, commissioning, staff training | + 2,500,000 | + 139 |
| **Total, ready to operate** | **about 20,620,000** | **about 1,145** |
| 15% contingency for battery, inverter, VIP, and compressor price volatility | + 3,090,000 | + 172 |
| **Proposed budget per unit** | **about 23,700,000** | **about 1,320** |

The optional 200 W deployable PV (IDR 2.4 million) is excluded because the health post is assumed to have a grid connection.

### 6.2 Life-cycle cost

Annual operating cost is about IDR 1.1 million: station electricity of IDR 36,000 per month (810 Wh per day), data connectivity of IDR 300,000 per year, silica gel replacement, calibration, and light servicing. Battery replacement adds IDR 2.6 million in year six or seven. Five-year total cost of ownership is about IDR 26.2 million, roughly IDR 435,000 per month. Training is covered in the assembly line: half a day for operators, one day for the facility technician, one day for QA. The comparison is simple: a single spoiled vaccine shipment is worth millions to tens of millions of rupiah, plus the trust that is lost with it.

### 6.3 Environment

No fuel and no generator means a low operational carbon footprint. The compressor runs about 2.1 h per recharge cycle and about 5 percent during transit. Solar-powered micro cold storage in the same class has been shown to mitigate around 700 kg of annual carbon emissions (Nadimuthu & Victor, 2021), and our box stays in that family. The LiFePO4 battery lasts beyond 2,000 cycles and is safer than other chemistries, passing the UN 38.3 low-pressure test (United Nations, 2019). The PCM is reused indefinitely, the refrigerant charge stays below 110 g under regulation, and battery and PCM recycling are part of the maintenance procedure.

### 6.4 Privacy, roles, and audit

No patient-identifiable data exists on the box or in the log. Shipment identifiers are pseudonymous. Position is truncated to four decimals for regular roles and five decimals for QA only. Access is role-based: couriers see their own shipments, QA sees excursion reviews, auditors get read-only, and every human override is logged. The design follows Indonesia's Personal Data Protection Law (Republik Indonesia, 2022) and the Philippine Data Privacy Act (Republic of the Philippines, 2012), answering the brief's requirement for privacy-preserving design with authorized audits.

### 6.5 Social and health impact

One YELODING carries vaccines for many children at once, including school immunization drives. Every safe trip means a group of children who are actually protected. Temperature evidence helps health workers answer parental hesitancy: parents can see for themselves that the vaccine reaching their child never left the range. Two centuries of vaccination show that coverage, not only efficacy, decides outcomes (Montero et al., 2024); a trusted cold chain is part of that coverage story. Doses per box depend on the vaccine type and presentation; the pilot determines the exact figure.

## 7. Limitations and recommendations

The limitations, stated by us: this is a conceptual design, not a validated medical device. The 48 kg weight requires two people and a trolley, and remains difficult on narrow footpaths. The system depends on a stationary recharge point; without one, active control is lost and the box reverts to 24-hour passive holdover. The GQR30TG data is still a scenario until the full datasheet arrives, above all the LRA against the inverter surge. Cryptography protects the record, not the reality: a sensor can be inaccurate and a handler can be careless, so calibration and physical seals stay mandatory.

We do not use blockchain for most cases. A hash-chained log with device signatures is enough to detect tampering, and the simulation demonstrates it. Blockchain becomes relevant when an audit involves many parties who do not trust each other, and even then it cannot prove that a sensor was accurate.

Recommendations: build the prototype, run the 24-hour test at 42 °C with calibrated reference sensors, verify the compressor LRA against the inverter surge, then run a field pilot in one island regency. Government and partners can help with stationary recharge points at health posts, integration of the log into immunization reporting systems, and support for calibration and training.

## 8. Conclusion

The answer to the main question is yes. Vaccines at 2–8 °C can be kept for at least 24 hours to remote islands without a reliable grid and without internet, provided the thermal load is carried by PCM and vacuum insulation, the recharge is carried by a compressor at a stationary point, the electronics only observe and prove, and the 15-minute rule is enforced by the device itself.

Three findings matter most. The 25 mm VIP cuts the heat load from 19 W to 9 or 10 W, so 7.04 kg of PCM suffices with a 34% margin, and the physical price is a weight of about 48 kg that we acknowledge. The panel on the lid only covers the electronics, so bulk recharging belongs to the stationary point, and an inexpensive AC compressor through an inverter is the most realistic way to refreeze the PCM in about two hours. The system's largest value is not its cooler but its tamper-resistant temperature evidence, its local alarms that work without a network, and its quarantine latch that enforces the 15-minute rule automatically, all verified in the Wokwi simulation before a single physical component was purchased.

On islands where the power is out and the signal is gone, vaccines cannot wait and health workers must not guess. YELODING is designed to work exactly when everything else is absent, and to give the health worker proof, rather than hope, that the vaccine in the syringe is still safe. When the buzzer sounds its "ding!", something needs attention; when it stays silent, the cold chain is intact.

## References

Bhatti, D. S., Hussain, M. M., Suh, B., Ali, Z., Akobir, I., & Kim, K. (2024). IoT-enhanced transport and monitoring of medicine using sensors, MQTT, and secure short message service. *IEEE Access, 12*. https://doi.org/10.1109/ACCESS.2024.3382508

Buitendach, H., Jiya, I. N., & Gouws, R. (2020). Solar powered peltier cooling storage for vaccines in rural areas. *Indonesian Journal of Electrical Engineering and Computer Science, 17*(1), 36–46. https://doi.org/10.11591/ijeecs.v17.i1.pp36-46

detikJateng. (2025, August 26). *Sumenep KLB campak, 17 meninggal, mayoritas belum pernah imunisasi* [Sumenep measles outbreak, 17 dead, majority never immunized]. https://www.detik.com

Embraco. (2019). *High altitude effects on refrigeration systems* [Technical bulletin]. Nidec Global Appliance. https://www.embraco.com

GS1. (2022). *GS1 EPCIS 2.0 standard*. https://www.gs1.org/standards/epcis

Group 5. (2026a). *Detail.md: Dimensions and calculations of the cold-chain box* [Unpublished project document].

Group 5. (2026b). *Dimension.md: Dimension sheets of the cold-chain box* [Unpublished project document].

Group 5. (2026c). *Price.md: Component cost breakdown* [Unpublished project document].

Group 5. (2026d). *Wokwi: ESP32 simulation of the cold-chain box, sketch.ino and dashboard.html* [Internal project code].

International Electrotechnical Commission. (2007). *IEC 60664-1: Insulation coordination for equipment within low-voltage systems, Part 1*. https://webstore.iec.ch

Jiang, S., Jia, S., & Guo, H. (2024). Internet of Things (IoT)-enabled framework for a sustainable vaccine cold chain management system. *Heliyon, 10*, e28910. https://doi.org/10.1016/j.heliyon.2024.e28910

Kementerian Kesehatan RI. (2025). *Kemenkes waspadai dinamika campak nasional dan global* [Ministry of Health monitors national and global measles dynamics]. https://kemkes.go.id

Kementerian Kesehatan RI. (2026). *Sehat negeriku: Bahan imunisasi HPV dan kanker serviks* [Immunization materials on HPV and cervical cancer]. https://sehatnegeriku.kemkes.go.id

Media Indonesia. (2025, August 27). *KLB campak, IDAI: Imunisasi harus diperkuat* [Measles outbreak, IDAI: Immunization must be strengthened]. https://mediaindonesia.com

Montero, D. A., Vidal, R. M., Velasco, J., Carreño, L. J., Torres, J. P., Benachi, O. M. A., Tovar-Rosero, Y.-Y., Oñate, A. A., & O'Ryan, M. (2024). Two centuries of vaccination: Historical and conceptual approach and future perspectives. *Frontiers in Public Health, 11*, 1326154. https://doi.org/10.3389/fpubh.2023.1326154

Nadimuthu, L. P. R., & Victor, K. (2021). Environmental friendly micro cold storage for last-mile Covid-19 vaccine logistics. *Environmental Science and Pollution Research*. https://doi.org/10.1007/s11356-021-17584-2

Popmama. (2025). *Kasus campak di Indonesia tertinggi kedua di dunia* [Indonesia's measles cases second highest in the world]. (Media summary of Ministry of Health data; verify against the primary source before quoting.)

Putra, A. D., Defit, S., & Nurcahyo, G. (2025). Penerapan IoT pada alat temperature monitoring system cold chain box vaccine menggunakan sensor DS18B20 [IoT application for a cold chain box vaccine temperature monitoring system using the DS18B20 sensor]. *Jurnal KomtekInfo, 12*(1), 1–11. https://doi.org/10.35134/komtekinfo.v12i1.589

Republic of the Philippines. (2012). *Data Privacy Act of 2012 (Republic Act No. 10173)*. https://www.officialgazette.gov.ph

Republik Indonesia. (2022). *Undang-Undang Nomor 27 Tahun 2022 tentang Pelindungan Data Pribadi* [Law No. 27 of 2022 on Personal Data Protection]. https://peraturan.bpk.go.id

Schneider Electric. (2011, March 22). *Altitude derating* [Technical FAQ]. https://www.se.com

Shahparvari, S., Hassanizadeh, B., Mohammadi, A., Kiani, B., Lau, K. H., Chhetri, P., & Abbasi, B. (2021). A decision support system for prioritised COVID-19 two-dosage vaccination allocation and distribution. *Transportation Research Part E: Logistics and Transportation Review, 153*, 102438. https://doi.org/10.1016/j.tre.2021.102438

United Nations. (2019). *Manual of tests and criteria* (7th rev.). https://unece.org

Wikipedia contributors. (2026). *Atmospheric pressure*. Wikipedia. https://en.wikipedia.org/wiki/Atmospheric_pressure

World Health Organization. (2011). *Annex 9: Temperature mapping of storage areas* (WHO Technical Report Series No. 961). https://www.who.int

World Health Organization. (2015). *Immunization in practice: A practical guide for health staff*. https://www.who.int

World Health Organization. (2024). *WHO PQS catalogue: Performance, quality and safety*. https://www.who.int

World Health Organization Indonesia. (2026, February 9). *Sumenep successfully ended measles outbreak*. https://www.who.int/indonesia

World Health Organization & United Nations Population Fund. (2024, November 15). *WHO, UNFPA commend Indonesia's efforts to eliminate cervical cancer*. https://www.who.int/indonesia

## Appendix A. Dimension summary

Table A1. Principal dimensions.

| Parameter | Value |
|---|---|
| Payload chamber internal | 400 × 250 × 300 mm, 30.0 L net [benchmark] |
| Trays | 3 trays, each <= 90 mm |
| Lid opening | 415 × 285 mm, rear hinge, double-lip gasket |
| Cold box external | 458 × 334 × 383 mm |
| Machine tier external | 490 × 350 × 332 mm |
| Separator | 15 mm PUR + 2 mm aluminium |
| Overall assembly | 490 × 350 × 742 mm |
| Weight empty / loaded | about 48 kg / about 63 kg with 15 kg payload |
| PCM | plate A 2 pcs (400 × 313 × 13) + plate B 1 pc (400 × 276 × 13), 7.04 kg total |
| Evaporator | Al 6063 400 × 250 × 12 mm, copper serpentine, 80 mm fan |
| Compressor | GQR30TG, Ø130 × 165 mm, 245 W cooling [verify] |
| Battery | LiFePO4 12.8 V 100 Ah, 329 × 172 × 214 mm [verify] |
| Inverter | pure sine 1,000 W, 300 × 160 × 85 mm [verify] |
| Solar panel | 20 W semi-flexible 440 × 320 × 3 mm on the lid, hinged protective cover |
| Vents | exhaust 320 × 160 mm, inlet 200 × 60 mm |
| Front control panel | OLED 128×64 + 3 LEDs + buzzer, 90 × 50 mm |
| Protection | IPX4 upright, pressure-equalization valve for 3,000 m operation |

## Appendix B. Electrical system and protection

Table B1. Electrical system.

| Item | Specification |
|---|---|
| Standing DC load | 5 W electronics + 6 W fans = 11 W, 264 Wh per day |
| Compressor AC path | 145 W through the inverter, 161 W DC-side while running |
| Battery | LiFePO4 12.8 V 100 Ah, 1,280 Wh, 1,024 Wh usable at 80% DoD |
| Inverter | pure sine 1,000 W, surge >= 1,500 VA, efficiency 0.90 |
| MPPT | A 10 A for the on-board PV, B 20 A for the station PV |
| Fuses | 40 A battery main, 30 A inverter (10 mm2 cable, max 0.5 m), 30 A MPPT-B, 15 A PV, 15 A DC distribution |
| AC protection | 30 mA RCD, AC compartment separated from the DC rail, 230 V warning labels |
| DC protection | TVS on the 12 V rail, blocking diode on the PV input, LVD at 11.0 V and 10.5 V |
| Recharging | 14.6 V / 20 A grid charger at the station; 20 W on-board PV as a supplement; transfer switch to run the compressor directly from the grid |
| PCM recharge time | 1,549 kJ at 210 W net, about 2.1 h |

**[Figure 6 placeholder]**

*Figure 6.* Electrical single-line diagram: sources, fuses, battery bus, inverter branch with RCD, and the DC distribution rail.

*Note.* Authors' drawing EL-01 (`gamtek.html`).

**[Figure 7 placeholder]**

*Figure 7.* Control-panel schematic: ESP32 pin map, I2C devices (OLED, BMP390, MPU-6050, DS3231), OneWire probes, buzzer and LED outputs, inverter relay, TEC driver, GNSS with PPS, and the 5 V / 3.3 V supply chain.

*Note.* Authors' drawing EL-02 (`gamtek.html`).

## Appendix C. Benchmark mapping to the Wokwi implementation

Table C1. Benchmarks and their simulation evidence.

| Brief benchmark | Implementation in the simulation | Evidence |
|---|---|---|
| 30 s sampling | record interval of 2 s at SIM_SCALE 60, equal to 30 s of story time | serial log [sim] |
| 24 h holdover | PCM_FULL_STORY_H = 24, drain follows delta T | S3 pass [sim] |
| 15 min excursion | cumulative counter, QUARANTINE latch | S5 pass [sim] |
| Cellular fallback | MQTT to a public broker, store-and-forward buffer | S8 pass [sim] |
| Verifiable custody | FNV-1a hash chain per record, handover receipt | S7 and S8 pass [sim] |
| Local alarms | OLED + 3 LEDs + buzzer without a network | S2, S4, S6 pass [sim] |

On the real device, the FNV-1a hash is replaced by signed Ed25519, two probes become three, and MQTT over WiFi becomes LTE-M. The control structure does not change.

## Appendix D. Figure list and sources

| Figure | Content | Source |
|---|---|---|
| 1 | System block diagram | Authors, after Group 5 (2026a) |
| 2 | General arrangement | Drawing GA-01, `gamtek.html` |
| 3 | Wall section | Drawing SEC-01, `gamtek.html` |
| 4 | Refrigerant and airflow schematic | Drawing REF-01, `gamtek.html` |
| 5 | Interior cutaway | Drawing ISO-01, `gamtek.html` |
| 6 | Electrical single-line diagram | Drawing EL-01, `gamtek.html` |
| 7 | Control-panel schematic | Drawing EL-02, `gamtek.html` |
| 8 | Wokwi simulation setup | Screenshot, `wokwi/sketch.ino` (Group 5, 2026d) |
| 9 | Dashboard, sender view | Screenshot, `wokwi/dashboard.html` (Group 5, 2026d) |
| 10 | Dashboard authentication gate | Screenshot, `wokwi/dashboard.html` (Group 5, 2026d) |

*Academic integrity disclosure. This analysis is the team's own work, prepared with AI assistance for document drafting as permitted and disclosed under the organizer's rules. All technical figures are labelled benchmark, estimate, sim, or verify; simulation results are logic verification, not measurements of a physical device. Benchmark values are quoted from the case benchmarks in Table 1; no benchmark is presented as our own estimate.*
