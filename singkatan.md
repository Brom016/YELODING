# singkatan.md — Abbreviations used in the YELODING essay

Short glossary of every abbreviation that appears in `essayfinalFinal_EN.md` (and the project documents behind it). One line each: what it expands to and what it does in this project.

## System and product

| Abbreviation | Full form | What it is here |
|---|---|---|
| YELODING | "yelo" (ice, Tagalog) + "dingin" (cold, Indonesian) + "ding!" | The product name; also the sound of its local alarm |
| PCM | Phase-Change Material | Salt hydrate that absorbs heat while melting at 5–6 °C; the passive cold reserve (7.04 kg) |
| VIP | Vacuum Insulation Panel | 25 mm panel in the walls; the main reason the heat leak is only 9 W |
| TEC | Thermoelectric Cooler (Peltier) | 20 W solid-state backup cooler on the DC rail; holds the leak ~31 h if the compressor fails |
| COP | Coefficient Of Performance | Cooling power delivered per watt of electricity; how compressors and Peltier modules are compared |
| AC / DC | Alternating / Direct Current | The compressor runs on AC from the inverter; sensors and fans run on DC |
| PSW | Pure Sine Wave | Inverter output shape; required by the compressor motor and RCD protection |
| MPPT | Maximum Power Point Tracker | Charges the battery from solar panels at their best operating point (A: 10 A on-board, B: 20 A station) |
| PV | Photovoltaic | The solar panels; 20 W on the lid, optional 200 W foldable at the station |
| BMS | Battery Management System | Built into the battery; balances cells and disconnects on faults |
| DoD | Depth of Discharge | How much of the battery is used; 80% here, giving 1,024 Wh usable |
| LVD | Low Voltage Disconnect | Cuts loads at 10.5 V to protect the battery |
| GQR30TG | (manufacturer model code) | The 245 W AC compressor, 1/10 HP RSIR motor |

## Sensors and control

| Abbreviation | Full form | What it is here |
|---|---|---|
| DS18B20 | (manufacturer part number) | Waterproof digital temperature probes; three of them, control on the median |
| DHT22 | (manufacturer part number) | Ambient temperature and humidity sensor in the machine bay |
| BMP390 | (manufacturer part number) | Barometric pressure sensor; doubles as the altitude log |
| MPU-6050 | (manufacturer part number) | Accelerometer; turns sustained shaking into a logged event |
| OLED | Organic Light-Emitting Diode | The 128×64 status display on the front panel |
| LED | Light-Emitting Diode | Three status lamps: green (running), red (alarm), yellow (battery) |
| RTC | Real-Time Clock | DS3231 keeps time when power and GPS are gone (±2 ppm) |
| GNSS | Global Navigation Satellite System | Position receiver (GPS + GLONASS + Galileo + BeiDou), 1 Hz |
| PPS | Pulse Per Second | GNSS output that disciplines the RTC to UTC |
| ESP32 | (Espressif module name) | The microcontroller: reads sensors, drives alarms, writes the log |
| SIM7080 | (module name) | LTE-M / NB-IoT cellular modem for telemetry |
| LTE-M / NB-IoT | Long-Term Evolution for Machines / Narrowband IoT | Low-power cellular networks used as the telemetry uplink |
| MQTT | Message Queuing Telemetry Transport | Lightweight publish/subscribe protocol between the box and the dashboard |
| I2C | Inter-Integrated Circuit | Two-wire bus shared by the OLED, BMP390, MPU-6050, and RTC |
| OneWire | (protocol name) | Single-wire bus shared by the DS18B20 probes |
| ADC | Analog-to-Digital Converter | Reads battery voltage from a resistor divider |
| TVS | Transient Voltage Suppressor | Diode that absorbs voltage spikes on the 12 V rail |
| Tach | Tachometer signal | Fan speed feedback; zero tach blocks the compressor |
| Reed switch | (reed = magnetic contact) | Lid and PV-cover position sensor; a broken seal is a custody event |

## Operations and compliance

| Abbreviation | Full form | What it is here |
|---|---|---|
| QA | Quality Assurance | The officer role that reviews excursions and releases QUARANTINE |
| SOP | Standard Operating Procedure | The written steps staff follow in the field |
| VVM | Vaccine Vial Monitor | Color label on some vials that shows cumulative heat exposure |
| QUARANTINE | (plain English, latched state) | Box state after a 15-minute excursion; batch unusable until QA decides |
| IPX4 | Ingress Protection, X4 | Splash-proof from any direction (dust rating not claimed) |
| UN 38.3 | UN Manual of Tests and Criteria, section 38.3 | Transport safety tests lithium batteries must pass |
| WHO | World Health Organization | Source of cold-chain guidance and the temperature-mapping protocol |
| PQS | Performance, Quality and Safety | WHO catalogue of approved cold-chain equipment |
| VVM check | (see VVM) | Step in the excursion decision, before any batch is used |

## Data and records

| Abbreviation | Full form | What it is here |
|---|---|---|
| FNV-1a | Fowler–Noll–Vo hash, variant 1a | Hash function used in the simulation; chains one record to the next |
| Ed25519 | (Edwards-curve signature scheme) | Digital signature that signs the chain head on real hardware |
| IoT | Internet of Things | Networked sensors and reporting, the "IoT-enabled" part of the title |
| MQTT broker | (see MQTT) | Server that relays telemetry between box and dashboard |
| OTA | Over The Air | Remote firmware update; not implemented, listed as future work |

## Electrical ratings

| Abbreviation | Full form | What it is here |
|---|---|---|
| RCD | Residual Current Device | 30 mA safety switch on the 230 V AC outlet |
| LRA | Locked Rotor Amps | Worst-case compressor start current; must fit the inverter surge |
| MEGA fuse | (MEGA/ANL fuse format) | 40 A main fuse at the battery terminal |
| Voc | Open-Circuit Voltage | Panel voltage with no load; must stay below the MPPT limit |
| Wh / kWh | Watt-hour / kilowatt-hour | Energy units; the box needs ~810 Wh on a normal day |
| ΔT | Delta T, temperature difference | Outside minus inside temperature; 35 K at design conditions |

## Essay labels

| Label | Meaning |
|---|---|
| [benchmark] | Value supplied with the case benchmarks (Table 1 of the essay) |
| [estimate] | Our own calculation, assumptions stated |
| [sim] | Verified in the Wokwi simulation (S1–S8) |
| [verify] | Still needs a manufacturer datasheet or RFQ |
