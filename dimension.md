# dimension.md — Dimension sheets (compact revision · AC power update)

> Companion to `detail.md`. Numbers only, no derivations. All values are [estimate] unless marked [benchmark] or [verify]. Payload core is fixed at 40 × 25 × 30 cm = 30.0 L.
> Final assembly: **49 × 35 × 74.2 cm (incl. on-board PV cover), ≈ 48 kg empty, ≈ 63 kg loaded (+15 kg payload).**
> Power baseline: GQR30TG AC compressor (245 W cooling) · LiFePO₄ 12.8 V 100 Ah · inverter 1,000 W PSW · on-board PV 20 W under a protective cover · station charging (grid charger baseline / deployable PV option).

## 1. Payload chamber (core, mandatory)

| Parameter | Value |
|---|---|
| Internal dimensions | 400 × 250 × 300 mm |
| Net volume | 30.0 L [benchmark] |
| Usable after racks | 3 trays, each ≤ 90 mm tall |
| Lid opening | 415 × 285 mm, rear hinge, double-lip gasket, tamper seal lug |
| Lid operation | opens rearward (hinges on the long rear edge); swings up and rests open at ~120° — no prop rod at this mass |
| Lid interior face | food-grade PP liner 2 mm + VIP 25 mm |
| Silica gel sachet | 20 g, clipped to lid interior corner; replaced annually |

## 2. Wall build-up (inside → out) — unchanged

| Layer | Thickness | Added per axis |
|---|---|---|
| PCM plates, 2 long walls + floor | 13 mm | +2.6 cm (Y), +1.3 cm (Z) |
| Liner, food-grade PP | 2 mm per face | +0.4 cm (X, Y, Z) |
| Evaporator plate, aluminium + 80 mm fan | 12 mm | +1.2 cm (Z only) |
| VIP panels, 6 faces | 25 mm | +5.0 cm (X, Y, Z) |
| HDPE skin | 2 mm per face | +0.4 cm (X, Y, Z) |

Stack check, axis by axis:

| Axis | Sum | Result |
|---|---|---|
| X: 0.2+2.5+0.2+40+0.2+2.5+0.2 | 45.8 cm | no PCM on short walls |
| Y: 0.2+2.5+0.2+1.3+25+1.3+0.2+2.5+0.2 | 33.4 cm | PCM walls included |
| Z: 0.2+2.5+0.2+1.2+1.3+30+0.2+2.5+0.2 | 38.3 cm | evaporator under floor PCM |

## 3. PCM plates (salt hydrate, melt 5–6 °C, ρ 1.5 kg/L) — unchanged

| Plate | Dimensions (mm) | Volume | Mass |
|---|---|---|---|
| A, long wall (×2) | 400 × 313 × 13 | 1.63 L each | 2.44 kg each |
| B, floor (×1) | 400 × 276 × 13 | 1.44 L | 2.15 kg |
| Total | | 4.70 L | **7.04 kg** |
| Latent capacity | 7.04 × 220 kJ/kg | 1,549 kJ | margin 34% over 1.16 MJ demand |
| Passive holdover | 24 h at 38–42 °C ambient | [estimate — test profile required] |

## 4. Cold box (tier 2) — unchanged

| Parameter | Value |
|---|---|
| External | **458 × 334 × 383 mm** (58.6 L) |
| Outer skin colour | **dark charcoal grey**, RAL 7021, UV-stabilised HDPE |
| Accent stripe | **Sunlight Yellow**, RAL 1023, 5 mm band on the top perimeter |
| Interior liner colour | off-white / food-grade natural PP |
| Lid stack (top → bottom) | skin 2 / VIP 25 / liner 2 |
| Floor stack (bottom → top) | skin 2 / VIP 25 / liner 2 / evaporator 12 / PCM 13 |
| Corner guards | 4 pcs, 30 × 30 × 20 mm, black rubber |
| Tie-down eyes | 4 pcs, M6, at base corners, yellow powder-coated |
| Handles | 2 side recessed, 160 × 60 mm grip |
| Latches | 2 front, cam-action, brushed stainless; released simultaneously |
| Hasp | 1 centre-front, accepts wire tamper seal or padlock; broken seal flags a custody event |
| Hinges | 2 rear, brushed stainless, 60 mm; M5 × 16 SS bolts into HDPE backing plate |
| Pressure-equalization valve | 1 × membrane/duckbill vent Ø10–15 mm, upper side wall; IPX4, self-sealing; equalizes altitude ΔP (see §12.5) |

## 4a. On-board PV deck and protective cover (NEW)

| Parameter | Value |
|---|---|
| Panel | 20 W semi-flexible mono, ≈ **440 × 320 × 3 mm**, ≈ 0.7 kg [verify] |
| Mounting | bonded to the lid top with structural adhesive over a flat adapter plate; no through-lid fasteners |
| Permanent fit | the panel and cover are part of the lid: they swing with it when it opens and travel with the box — no install/remove cycle, ever |
| Lid motion | co-axial hinge line: the payload lid opens its full ~120° with panel + cover attached; a cable loop on the hinge side is sized for the full travel |
| Cover SOP | open during operation and charging (panel harvests); closed only for storage, stacking, heavy rain, or high-theft parking |
| Deck footprint | 440 × 320 mm, centred on the lid, ≥ 9 mm margin to every edge |
| Theoretical cap | 458 × 334 mm footprint → ≈ 25 W max; 20 W keeps margin and sourcing flexibility |
| Cover | hinged HDPE flat lid **≈ 460 × 336 × 2 mm + 15 mm frame**, rear-hinged (co-axial with the payload-lid hinge line), opens ~100° |
| Cover hardware | 2 quarter-turn latches + padlock eye; **lockable** (anti-theft) |
| Cover sensing | reed switch on the cover frame — **PV COVER OPEN is a logged custody event** |
| Stacking | cover closed = flat 460 × 336 deck; strap load rides on the cover frame, not the panel |
| Wiring | panel leads through a sealed gland at the lid rear edge, down the hinge side into the machine tier; IP67 gland |
| Height added | ≈ 10 mm (panel 3 + air gap + cover 2 + frame) |
| Thermal | panel heat sits above the VIP lid; no measurable payload effect — the VIP is the barrier |
| Energy | ≈ 65 Wh/day to the battery (4.5 PSH × 0.8 × 0.9); range extender only — see `detail.md` §6.7 |

### Cold box interior — detailed contents

| Item | Detail |
|---|---|
| Vaccine trays | 3 × removable PP tray, ≤ 90 mm tall, 395 × 245 mm footprint |
| PCM plate A (×2) | 400 × 313 × 13 mm slabs, two long interior walls; 10 mm standoff bosses for air circulation |
| PCM plate B (×1) | 400 × 276 × 13 mm slab on the floor, above the evaporator |
| Evaporator plate | Al 6063, 400 × 250 × 4 mm, Cu serpentine bonded; −6 to −8 °C while charging |
| Circulation fan | 80 × 80 × 15 mm axial, floor short edge; 1 W, 2 000 RPM |
| Temperature probes | 3 × DS18B20: T1 top-centre, T2 bottom-centre, T3 mid wall |
| Lid reed switch | magnetic reed, lid-frame mount |
| TEC cold-side fin block | 40 × 40 × 25 mm, floor corner; DC fallback |
| Silica gel sachet | 20 g, lid interior, replaced annually |

## 5. Machine tier (tier 1) — REVISED

| Parameter | Value |
|---|---|
| External | **490 × 350 × 332 mm** (57 L) |
| Internal | **480 × 340 × 320 mm** (52.2 L) |
| Separator to cold box | PUR 15 mm + aluminium 2 mm (17 mm total) |
| Shell | 2.5 mm plastic; **exhaust 320 × 160 mm** on the Y+ wall behind the condenser (2 × 120 mm fans, finger guard, mesh); **inlet louvre 200 × 60 mm** on the X− end wall, upper section, 45° |
| Control panel (front face) | 90 × 50 mm panel, left side; black anodised bezel; sealed OLED window + LED gaskets |
| Power input port (front face) | 12 V DC barrel jack, right side; yellow embossed label; black rubber hinged cover |
| AC outlet | 230 V AC Schuko/universal outlet + RCD 30 mA, on the front face far right (covered flap); for compressor-side service and station tools |
| AC/DC separation | AC compartment (inverter, RCD, outlet, compressor leads) shielded from the DC rail and cable channels; screw-locked fuse panel lid |

### Internal layout (verified fit)

| Item | Dimensions (mm) | Position (X, Y, Z from tier origin) |
|---|---|---|
| Battery LiFePO₄ 12.8 V 100 Ah, flat | 329 × 172 × 214 | 0–329, 0–172, 0–214 |
| Inverter 1,000 W PSW | 300 × 160 × 85 | 10–310, 10–170, 224–309 (on battery, 10 mm rubber standoffs) |
| MPPT-A 10 A (on-board PV) | 168 × 100 × 30 | 10–178, 180–280, 0–30 |
| MPPT-B 20 A (station PV input) | 123 × 90 × 35 | 10–133, 180–270, 40–75 (stacked above MPPT-A) |
| Electronics box | 130 × 80 × 60 | 195–325, 180–260, 0–60 |
| Compressor GQR30TG (Ø130, vertical) | 140 × 140 × 170 envelope | 335–475, 5–145, 0–170 |
| Condenser + 2 × 120 mm fans | 280 × 150 face, 80 deep | 100–380, 260–340, 30–180 (Y+ wall) |
| Fuse panel + main fuse + DC distro | 140 × 100 × 100 | 340–480, 150–250, 0–100 |
| MPPT-A branch fuse | 5 A | PV-A side; MPPT-B branch 20 A |
| AC outlet + RCD module | 90 × 70 × 60 | 390–470, 260–330, 0–60 |
| PV input connector (station kit) | Solar-style plug, bulkhead IP67 | rear face, right of the antennas |
| Wiring channel | leftover strips | X 380–480, Y 260–340, Z 180–320; X 310–480, Y 0–150, Z 170–220 |
| TEC hot-side heatsink | 60 × 60 × 20 | through the separator, floor corner X 5–65, Y 190–250, Z 170–190 |
| GNSS + LTE antennas | patch 25 × 25 mm, external bulkhead | rear face, diagonal corners, ≥ 250 mm apart |

Fit checks:
- Battery ↔ inverter: 10 mm standoff above the battery top; inverter terminals face the front service edge.
- Battery ↔ compressor: X-separated (329 vs 335).
- Inverter ↔ condenser: Y-separated (≤ 170 vs ≥ 260).
- MPPT / electronics ↔ condenser: Y ≤ 301 / ≤ 260 with condenser starting at 260 and Z ≥ 30 → electronics limited to Y ≤ 260.
- Fuse panel ↔ compressor: Y-separated (≥ 150 vs ≤ 145).
- AC outlet ↔ condenser: X-separated (≥ 390 vs ≤ 380).
- Battery mass (10.5 kg) sits on the tier floor → low centre of gravity.

### Control panel detail (front face, left side)

| Part | Spec | Position on panel |
|---|---|---|
| OLED display | SSD1306 128 × 64 px, I2C 0x3C; sealed acrylic window | upper-left |
| LED — green | 5 mm, compressor running | right column, top |
| LED — red | 5 mm, excursion / quarantine | right column, mid |
| LED — yellow | 5 mm, battery low | right column, bottom |
| Buzzer grille | active buzzer 5 V, 3 × Ø2 mm holes | lower-left |
| OLED content | state · T1/T2 °C · PCM % / HOLD h · BAT V / CMP · INV on/off | — |

### Power input port detail (front face, right side)

| Parameter | Value |
|---|---|
| Connector | 5.5 × 2.1 mm barrel jack, centre positive |
| Voltage | 12 V DC nominal (10.5–14.6 V) |
| Max current | 10 A (fused); **electronics and DC loads only** — the AC compressor never runs from this port |
| Cover | spring-loaded hinged rubber flap, IP54 when closed |
| Dual-use | vehicle socket for DC loads / slow top-up via optional DC-DC charger; PV station cable at the charging point |

## 6. Electronics (controller board)

| Part | Value / spec | Count |
|---|---|---|
| MCU board | ESP32-WROOM-32 | 1 |
| Temperature probes | DS18B20 waterproof, 1.5 m cable | 3 |
| Pull-up resistors | 4.7 kΩ, 1/4 W | 1 per bus |
| Ambient sensor | DHT22 (or SHT4x) | 1 |
| Barometric + humidity (doubles as altitude log) | BMP390 (or BME280), I2C | 1 |
| Accelerometer | MPU-6050, I2C | 1 |
| Display | OLED SSD1306 128×64, I2C 0x3C | 1 |
| Cellular | SIM7080 LTE-M / NB-IoT | 1 |
| GNSS receiver | u-blox NEO-M8N / MAX-M10S class, UART + PPS | 1 |
| RTC | DS3231, ±2 ppm | 1 |
| GNSS backup | CR1220 coin cell on V_BCKP | 1 |
| GNSS antenna | 25 × 25 mm active patch, IP67, bulkhead SMA | 1 |
| Buzzer | Active, 5 V | 1 |
| Fan tach inputs | RPM monitoring, stall alarm | 3 (2 condenser + 1 circulation) |
| Indicator LEDs | 5 mm, green / red / yellow | 3 |
| LED series resistors | 220 Ω, 1/4 W | 3 |
| Decoupling capacitors | 100 nF ceramic, per IC | 4+ |
| Bulk capacitor | 470 µF electrolytic, 16 V, on 12 V rail | 1 |
| TVS diode | SMBJ15A on 12 V input | 1 |
| Battery sense divider | 10 kΩ + 3.3 kΩ, 1% | 1 pair |
| Buck converter | LM2596 module, 12 V → 5 V, 3 A | 1 |
| LDO | AMS1117-3.3 | 1 |
| Compressor control | inverter remote-enable relay (DC coil, 12 V) + flyback diode | 1 |
| Main fuses | Blade/ANL: 40 A battery main, 30 A inverter, 30 A MPPT, 15 A PV, 15 A DC distro | 5 |
| Blocking diode | Schottky, PV input | 1 |
| RCD / GFCI | 30 mA, on the 230 V AC outlet | 1 |

## 7. Power system

| Item | Dimensions (mm) | Mass | Notes |
|---|---|---|---|
| Battery LiFePO₄ 12.8 V 100 Ah | 329 × 172 × 214 | 10.5 kg [verify] | integrated BMS, ≥ 100 A continuous |
| Inverter pure sine 1,000 W | 300 × 160 × 85 | 2.2 kg [verify] | 12 V DC → 230 V AC, surge ≥ 1,500–2,000 VA, eco ≤ 2 W |
| MPPT-A 10 A (on-board PV) | 168 × 100 × 30 | 0.3 kg [verify] | 20 W panel input |
| MPPT-B 20 A (station PV) | 123 × 90 × 35 | 0.5 kg [verify] | deployable PV input, rear bulkhead connector |
| On-board PV 20 W semi-flexible | ≈ 440 × 320 × 3 | 0.7 kg [verify] | bonded to lid top, under cover |
| PV protective cover | 460 × 336 × 2 + frame | 0.9 kg | hinged, lockable, reed-switch monitored |
| AC compressor GQR30TG | Ø130 × 165 h | 8.0 kg [verify] | 220–240 V, 245 W cooling, 1/10 HP RSIR, PTC start |
| Condenser wire-tube + 2 × 120 mm fans | 280 × 150 face, 80 deep | 1.9 kg | 365 W rejection, ≈ 64 CFM through core |
| Evaporator plate (coil-bonded) | 400 × 250 × 12 | 2.0 kg | Cu serpentine + 80 mm fan |
| Station grid charger (baseline) | 14.6 V / 20 A | 1.2 kg | stays at the charging station |
| Deployable PV 200 W foldable (option) | ≈ 600 × 430 × 50 folded | ≈ 8 kg [verify] | stays at the station; feeds MPPT-B via the rear connector |
| Optional DC-DC charger | 12 V / 20 A | 0.8 kg | alternator charging while driving |

### Protection setpoints

| Item | Value |
|---|---|
| Battery main fuse | 40 A |
| Inverter branch | 30 A, 10 mm² cable, ≤ 0.5 m |
| MPPT / PV | 30 A branch, 15 A PV-side fuse |
| DC distribution | 15 A |
| AC output | RCD 30 mA |
| Battery LVD (BMS + firmware) | load shed below 11.0 V, hard cut 10.5 V |

## 8. Final assembly

| Parameter | Value |
|---|---|
| Overall (L × W × H) | **490 × 350 × 742 mm** incl. PV cover, stepped footprint |
| Cold box | 458 × 334 × 383 mm |
| PV deck + cover (on lid) | ≈ 460 × 336 × 10 mm |
| Machine tier | 490 × 350 × 332 mm |
| Total external volume | ≈ 119 L |
| Payload volume | 30.0 L net [benchmark] |
| Weight, empty | **≈ 48 kg** |
| Battery mass | 10.5 kg [verify] |
| Weight, +15 kg payload | **≈ 63 kg** |
| On-board PV energy | ≈ 65 Wh/day — range extender only |
| Station charging kit | grid charger 1.2 kg (baseline) or deployable PV ≈ 8 kg (option) |
| Centre of gravity | low — battery on the tier floor |
| Carrying | **2-person lift + trolley mandatory**; 4 × M6 tie-down eyes |
| Trolley base | +40 mm, +4 kg |

## 9. Comparison with the previous revision

| Parameter | 20 Ah / DC (old) | **100 Ah / AC (current)** |
|---|---|---|
| Overall | 460 × 335 × 575 mm | **490 × 350 × 732 mm** |
| External volume | 89 L | **118 L** |
| Payload | 30.0 L | 30.0 L |
| Heat leak | 9 W | 9 W (10 W at 42 °C) |
| PCM mass | 7.0 kg | 7.0 kg |
| Compressor | DC BD35F, 115 W cooling | **AC GQR30TG, 245 W cooling** |
| Cooling input power | 88 W DC | **145 W AC / 161 W DC-side [estimate]** |
| Battery | 240 Wh (216 usable) | **1,280 Wh (1,024 usable)** |
| PV | 200 W separate | **20 W on-board under cover + station kit** |
| Inverter | none | **1,000 W PSW** |
| Daily energy | ≈ 385 Wh | **≈ 810 Wh** |
| Active autonomy | ≈ 15 h | **≈ 30 h** |
| Passive + telemetry | ≈ 18 h | **≈ 94 h** |
| Empty weight | ≈ 28.5 kg | **≈ 46.5 kg** |

### Battery capacity comparison (for the essay's sizing argument)

| Capacity | Usable @ 80% DoD | Active ops | Passive + telemetry | Verdict |
|---|---|---|---|---|
| 20 Ah (240 Wh) | 192 Wh | ≈ 6 h | ≈ 19 h | insufficient for the AC load |
| 50 Ah (640 Wh) | 512 Wh | ≈ 15 h | ≈ 46 h | absolute minimum |
| 80 Ah (1,024 Wh) | 819 Wh | ≈ 24 h | ≈ 74 h | minimum for a 24 h full-active day |
| **100 Ah (1,280 Wh)** | **1,024 Wh** | **≈ 30 h** | **≈ 94 h** | **chosen — healthy margin** |
| 150 Ah (1,920 Wh) | 1,536 Wh | ≈ 45 h | ≈ 140 h | overkill for this duty; +5 kg, +8 L |

## 10. Cooling loop — REVISED

### 10.1 Cycle design points

| Parameter | Value | Note |
|---|---|---|
| Evaporating temperature | −8 °C | plate must sit below the 5–6 °C PCM freeze point |
| Condensing temperature | 50–55 °C | 40 °C ambient, machine bay up to 50 °C |
| Cooling capacity | 245 W rated → ≈ 220 W at design [estimate] | [verify] rating conditions |
| Electrical input | 145 W baseline (130–180 W scenarios) | [verify] |
| COP | ≈ 1.5 at design | 1.2–1.7 across scenarios |
| Heat rejection | **≈ 365 W** | capacity + input |
| Refrigerant | R134a or R600a, charge to be confirmed | [verify] — R600a is flammable, bay stays vented |
| Expansion | capillary, fixed orifice | [verify] length/ID from compressor kit |
| Full PCM recharge | 1,549 kJ at 210 W net = **2.1 h** | faster than the old DC design |

### 10.2 Evaporator (cold plate) — unchanged

| Part | Spec |
|---|---|
| Base plate | aluminium 6063, 400 × 250 × 4 mm, anodized |
| Coil | copper Ø8 × 0.5 mm wall, 6-pass serpentine, 2.8 m, thermal epoxy in milled grooves |
| Clamp | 400 × 30 × 4 mm bar, 6 × M5 bolts |
| Surface temp while charging | −6 to −8 °C |
| Mass | 2.0 kg incl. 80 mm fan |
| Frost | negligible in 2–8 °C chamber; 20 g silica gel in the payload |

### 10.3 Circulation fan — unchanged

| Spec | Value |
|---|---|
| Size | 80 × 80 × 15 mm axial |
| Power | 12 V, 0.08 A, ≈ 1 W |
| Airflow | 30 CFM free air |
| Speed / noise | 2 000 RPM, ≤ 24 dBA |
| Duty | continuous, clipped to the floor plate short edge |

### 10.4 Condenser — REVISED

| Spec | Value |
|---|---|
| Type | wire-tube, copper Ø6 with steel wires, 3 rows |
| Face | **280 × 150 mm**, flush on the Y+ wall |
| Wire surface | ≈ 0.62 m², UA ≈ 35 W/K |
| Duty | **365 W rejection** at air ΔT ≈ 10 K |
| Airflow needed | ≈ 64 CFM through the core |

### 10.5 Condenser fans — REVISED (2 units)

| Spec | Value |
|---|---|
| Size / count | 120 × 120 × 25 mm axial, **2 pcs** |
| Power | 12 V, 0.20 A each (4.8 W total) |
| Airflow | 65 CFM free air each, ≈ 90 CFM free combined |
| Speed / noise | 1 900 RPM each, ≈ 30 dBA combined |
| Bearing + feedback | dual ball, tach wire per fan |
| Interlock | firmware will not start the compressor when either tach reads zero |
| Mount | rubber grommets, pulls bay air through the condenser and out |

### 10.6 Vents and airflow — REVISED

| Opening | Size | Position |
|---|---|---|
| Exhaust | **320 × 160 mm** | Y+ side wall behind the condenser, finger guard + insect mesh |
| Inlet | **200 × 60 mm** | X− end wall, upper section, louvred 45°, mesh |
| Path | inlet → across the bay past the DC electronics → compressor → fans → condenser → exhaust |
| Drain | Ø8 mm | bay floor, lowest corner |

### 10.7 Refrigerant lines

| Line | Spec |
|---|---|
| Discharge | copper Ø6, 150 mm, compressor to condenser |
| Capillary | fixed orifice, coiled at condenser outlet |
| Suction | copper Ø8, 250 mm, 10 mm foam insulation, sealed grommet through the separator |
| Joints | brazed; Schrader port optional |

### 10.8 TEC trim module — unchanged (DC fallback)

| Part | Spec |
|---|---|
| Module | 40 × 40 mm Peltier, 60 W max, run at 20 W |
| Cold side | 40 × 40 × 25 mm fin block, cold box floor corner |
| Hot side | 60 × 60 × 20 mm heatsink in the machine tier |
| Role | holds the 10 W leak for ≈ 31 h on battery alone (COP 0.45 → 22 W + 11 W DC loads) if the compressor or inverter fails |

## 11. GNSS receiver, antenna and time — unchanged

| Item | Spec |
|---|---|
| Module | u-blox NEO-M8N or MAX-M10S class, multi-GNSS |
| Interface | UART2, GPIO16 RX / GPIO17 TX, NMEA 9600 baud |
| PPS output | GPIO35, disciplines the system clock |
| Supply | 3.3 V, ≈ 0.15 W |
| Accuracy | 2.5 m CEP open sky [benchmark]; 3–6 m on a side-facing patch |
| Antenna | 25 × 25 mm active patch, IP67 bulkhead, rear face upper corner; LTE antenna diagonal corner ≥ 250 mm apart |
| Ground plane | copper foil 100 × 100 mm |
| Clock | GNSS PPS sets the clock; DS3231 holds time during outages; clock-source flag per record |
| Privacy | 4 decimals (≈ 11 m) in telemetry; 5 decimals for QA role only |

## 12. Telemetry matrix, rain, vibration, AC safety

### 12.1 Telemetry matrix

| Parameter | Sensor | Interval | When the link drops |
|---|---|---|---|
| Payload temperature, 3 points | DS18B20 | 30 s [benchmark] | 72 h buffer, sync on reconnect |
| Ambient temp + humidity | DHT22 / SHT4x | every record | same |
| Barometric pressure | BMP390 | every record | same |
| Position, speed, HDOP, satellites | GNSS, 1 Hz internal | every record | same; gaps logged, never interpolated |
| Battery voltage | divider on ADC | every record | same |
| Lid state | reed switch | event + every record | same |
| Vibration RMS | accelerometer | every record + threshold event | same |
| Compressor duty + inverter state | runtime counter + relay feedback | every record | same |
| Clock source | GNSS PPS / RTC | per record | drift flagged |

Fallback ladder: LTE-M first, NB-IoT second, then the 72 h store-and-forward buffer. The local buzzer and OLED never depend on the link.

### 12.2 Rain and water ingress

| Path | Protection |
|---|---|
| Lid | double-lip gasket + tamper-seal hasp |
| Probe and antenna cables | sealed glands; antenna bulkhead IP67 |
| Vents | 45° louvres + insect mesh; Ø8 mm drain at the bay floor |
| Control panel | sealed OLED window, LED gaskets |
| AC outlet | spring flap, IP44 minimum, drip shield above |
| PCB | acrylic conformal coating, plated connectors |
| Target | IPX4 upright for DC sections; AC section IP44 minimum |
| Residual risk | heavy deck rain: tarpaulin per SOP; never submerge; PV panel stays sheltered at the station |

### 12.3 Vibration

| Source | Mitigation |
|---|---|
| Compressor | 4 rubber mounts, 30 Shore, M6 |
| Fans | rubber grommets |
| Battery | hold-down strap + rubber base pad; terminals strain-relieved |
| Inverter | 10 mm rubber standoffs on the battery, clamped |
| PCM plates | foam slots + 10 mm standoff bosses |
| Electronics | foam-potted box |
| Box on vehicle | 4 × M6 tie-down eyes, straps per SOP |
| VIP panels | behind skins, corner guards |

Detection: accelerometer RMS above threshold → VIBRATION HIGH event; sustained shaking flags PCM plate seating and battery strap for inspection.

### 12.4 AC safety (new)

| Item | Rule |
|---|---|
| AC enclosure | inverter + RCD + outlet + compressor leads separated from the DC rail by a barrier plate |
| RCD | 30 mA on the AC outlet; test button accessible at service |
| Bonding | inverter floating output bonded per its manual; PE continuity checked at commissioning |
| Labels | "230 V AC — disconnect inverter before service" on every removable panel over AC terminals |
| Fuse panel | screw-locked lid, not tool-free |
| Cable routing | AC and DC harnesses on separate sides of the bay, crossing at 90° where unavoidable |
| Compressor bay | vented, drained, drip shield above the electronics |

### 12.5 Altitude and pressure (mountain operation)

Design envelope: sea level to 3,000 m. The machine tier is vented (self-equalizing); the sealed cold box gets one pressure-equalization valve.

| Item | Spec / effect |
|---|---|
| Equalization valve | 1 × membrane or duckbill vent, Ø10–15 mm, upper side wall (or lid frame), IPX4, self-sealing |
| Worst-case lid ΔP without valve | ≈ +18 kPa at 2,500 m (sealed warm at sea level) → ≈ 2.1 kN uplift on the 415 × 285 lid — latch load, not gasket load; with the valve ≈ 0 |
| Condenser at 2,000 m | air density −20% (pressure falls ≈ 1.2 kPa per 100 m) → UA ≈ 29 W/K, condensing +2–3 K, capacity −10–20% at 2,000 m (industry rule of thumb: 5–10% loss per 1,000 m) — acceptable with duty monitoring; compressor altitude rating [verify]. On a 22 °C highland day the condensing temp still lands ≈ 34 °C, better than the ≈ 50 °C sea-level worst case |
| PCM plates | 10–15% fill headspace + relief diaphragm or ribbed walls [verify with supplier] |
| BMP390 | logs pressure every record → altitude; ALTITUDE HIGH event above a configurable threshold (default 2,000 m) |
| 230 V side | clearance derate above 2,000 m per IEC 60664 [verify for highland deployments] |
| Thermal upside | 15–25 °C mountain ambient → leak ≈ 4–5 W, holdover > 24 h comfortably |

> Sources: standard-atmosphere pressure curve (≈ −1.2 kPa per 100 m, barometric formula); highland cabinet-AC field data (≈ 5–10% cooling loss per 1,000 m); electrical derating above 2,000 m (Schneider Electric guidance, IEC 60664). Embraco/Nidec publishes the technical bulletin "High Altitude Effects on Refrigeration Systems" — request it with the GQR30TG datasheet.

## 13. Colour scheme summary — unchanged

| Zone | Colour | Rationale |
|---|---|---|
| Outer HDPE skin | RAL 7021 dark charcoal grey | brand consistency; hides field grime |
| Accent stripe + tie-down surrounds | RAL 1023 Sunlight Yellow | medical priority, high visibility |
| Interior PP liner | natural off-white | hygiene inspection |
| Stainless hardware | brushed silver | coastal corrosion resistance |
| Corner guards | matte black rubber | contrast + impact |
| Control bezel | black anodised aluminium | instrument look |
| OLED | navy #001a33 / cyan #00ccff | daylight contrast |
| LEDs | green #00ff44 · red #ff2200 · yellow #ffcc00 | ISO convention |
| PV frame | dark grey aluminium | — |
| PV cells | dark navy | monocrystalline |

Note: the dark skin carries ≈ 2 W of extra solar-equivalent gain (already inside the 1.16 MJ budget). If the pilot shows sustained duty above model, the fallback is a light-grey RAL 7035 skin variant — geometry, PCM and power system unaffected.

## 14. Datasheets still to verify

| # | Item | What is needed |
|---|---|---|
| 1 | GQR30TG compressor | input W at design conditions, running A, LRA, refrigerant + charge, condenser spec, mass, envelope |
| 2 | Battery 100 Ah | exact envelope, mass, terminal layout, BMS continuous/peak, cycle life |
| 3 | Inverter 1,000 W PSW | surge rating + duration, part-load efficiency, no-load draw, eco auto-restart with inductive load |
| 4 | On-board PV 20 W | exact dimensions vs 440 × 320 deck, mass, bond adhesive, output tolerance |
| 5 | PV cover | hinge/latch IP rating, seal compression, lock spec |
| 6 | MPPT-A 10 A / MPPT-B 20 A | max PV Voc, self-consumption, charge profile |
| 7 | Station grid charger | 14.6 V / 20 A profile vs BMS spec |
| 8 | Deployable PV 200 W (option) | folded envelope, mass, connector standard |
| 9 | PCM supplier | latent heat, density, melt tolerance, cycling stability |
| 10 | VIP supplier | aged k certificate |
| 11 | RCD/outlet module | IP rating, mounting depth |
| 12 | Compressor altitude rating | verified operating ceiling (target ≤ 3,000 m) |
| 13 | PCM plates | fill headspace + pressure-relief spec for altitude transport |
| 14 | Pressure-equalization valve | airflow, IP rating, membrane service life |
