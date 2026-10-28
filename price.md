# price.md — Rincian harga per komponen (asumsi pasar Indonesia, 2026 · skenario termurah)

> Semua harga adalah **[estimate]** — asumsi dari harga e-commerce lokal (Tokopedia/Shopee) dan distributor, bukan penawaran resmi. Wajib di-refresh dengan RFQ nyata sebelum anggaran final.
> **Dokumen ini memakai HARGA TERENDAH dari tiap rentang** (skenario termurah yang masih layak). Angka ini floor budget, bukan target — realita biasanya 10–30% di atas floor.
> Kurs asumsi: **Rp 18.000 = USD 1** (bulatkan; harga import mengikuti kurs harian).
> Label: **[verify]** = wajib RFQ/datasheet; harga berubah cepat untuk baterai, panel, dan komponen impor.
> Struktur mengikuti `dimension.md` §7 dan `detail.md` §7 (komponen no. 1–18).

---

## 1. Cold box (tier 2) — mekanik + termal

| # | Komponen | Spesifikasi | Asumsi harga (Rp) | Catatan |
|---|---|---|---|---|
| 1 | Shell cold box (rotasi/celup HDPE 2 mm + frame) | 458 × 334 × 383 mm, RAL 7021 | **1.500.000** | Custom molding mahal; pakai fabrikasi lembar/laminating untuk prototipe [verify] |
| 2 | VIP panel 6 sisi, 25 mm | k aged 0,0075 W/m·K | **1.600.000** | Komponen termahal kedua; impor (Korea/Cina). Alternatif PUR 40 mm: ~Rp 250 rb [verify] |
| 3 | Liner PP food-grade 2 mm | vakum-form custom | **400.000** | |
| 4 | PCM plate A ×2 | salt hydrate 400×313×13, 2,44 kg/pc | **700.000** (2 pcs) | ≈ Rp 140 rb/kg DIY salt hydrate; PCM siap pakai jauh lebih mahal [verify] |
| 5 | PCM plate B ×1 | salt hydrate 400×276×13, 2,15 kg | **350.000** (1 pc) | Sama, basis DIY [verify] |
| 6 | Evaporator plate + coil + kipas 80 mm | Al 6063 400×250×4, Cu serpentin, kipas 1 W | **850.000** | Custom bonding; alternatif plate-ready pendingin DC: ~Rp 500 rb |
| 7 | TEC cold-side fin block | Al 40×40×25 | **60.000** | |
| 8 | Gasket EPDM double-lip + seal lug | 415 × 285 mm keliling | **150.000** | |
| 9 | Latch cam-action stainless ×2 + hasp + engsel ×2 | SS 304 | **350.000** | |
| 10 | Corner guard karet ×4 + handle recessed ×2 | | **200.000** | |
| 11 | Tie-down eye M6 ×4 (powder kuning) | | **100.000** | |
| 12 | Katup penyama tekanan (membran/duckbill) | Ø10–15 mm, IPX4 | **80.000** | Duckbill lokal; GORE vent jauh lebih mahal [verify] |
| 13 | Cover PV (HDPE 2 mm + frame 15 + engsel + latch) | 460 × 336 | **350.000** | |
| 14 | Tray vaksin PP ×3 | 395 × 245 × ≤90 | **250.000** | Tray standar es krim/bekam |
| 15 | Silica gel 20 g | | **15.000** | |

**Subtotal cold box: Rp 6.955.000** (≈ USD 386)

---

## 2. Machine tier — tenaga & pendinginan

| # | Komponen | Spesifikasi | Asumsi harga (Rp) | Catatan |
|---|---|---|---|---|
| 16 | Kompresor AC **GQR30TG** | 220–240 V, 245 W cooling, 1/10 HP RSIR | **750.000** | Harga kompresor rumah tangga kelas ini; [verify] ketersediaan model persis |
| 17 | Kondensor wire-tube 3 baris (280×150) + 2 kipas 120 mm | Cu Ø6, kipas 2,4 W/pc | **600.000** | Kondensor custom; kipas DC 120 mm ~Rp 60–90 rb/pc |
| 18 | Kapiler + jalur refrigeran Cu + brazing | R134a charge | **250.000** | Servis AC lokal bisa rakit [verify] |
| 19 | **Baterai LiFePO₄ 12,8 V 100 Ah** + BMS ≥100 A | pak prismatik | **2.600.000** | Merk lokal/Cina value tier; garansi penting [verify] |
| 20 | **Inverter pure sine 1.000 W** (surge ≥2.000 VA) | 12 V DC → 230 V AC | **1.400.000** | Merek lokal/Cina; uji start RSIR sebelum komit [verify surge] |
| 21 | MPPT-A 10 A (PV on-board) | input ≤ 25 V | **250.000** | |
| 22 | MPPT-B 20 A (PV station) | input ≤ 100 V | **500.000** | Kelas EPEver value |
| 23 | Panel surya on-board **20 W semi-flexible** | 440 × 320 × 3 | **350.000** | Semi-flex mono value tier |
| 24 | Panel PV deployable **200 W lipat** (opsyen station) | 600 × 430 × 50 terlipat | **2.400.000** | Opsyen — **tidak dihitung di subtotal** (station diasumsikan punya grid) |
| 25 | Charger grid AC-DC 14,6 V / 20 A | | **800.000** | Charger LiFePO4 dedikasi value; alternatif PSU adjustable + CC/CV |
| 26 | TEC modul 40×40 (60 W) + heatsink | Peltier | **120.000** | |
| 27 | Sekring & distribusi: 40 A main, 30 A inverter, 30 A MPPT-B, 15 A PV, 15 A DC | MEGA/blade + holder | **250.000** | |
| 28 | Kabel 10 mm² (inverter), 6 mm², konektor, gland | | **400.000** | |
| 29 | Shell machine tier + separator (PUR 15 + Al 2) | 490 × 350 × 332 | **900.000** | |
| 30 | Rubber mount kompresor ×4 + standoff inverter | | **100.000** | |

**Subtotal machine tier (tanpa PV deployable): Rp 9.270.000** (≈ USD 515)

---

## 3. Elektronik & telemetri

| # | Komponen | Spesifikasi | Asumsi harga (Rp) | Catatan |
|---|---|---|---|---|
| 31 | ESP32-WROOM-32 devkit / custom PCB | | **80.000** | Devkit |
| 32 | Probe DS18B20 waterproof ×3 | kabel 1,5 m | **90.000** | ~Rp 30 rb/pc |
| 33 | DHT22 / SHT4x ambient | | **60.000** | DHT22 |
| 34 | BMP390 (barometrik — log ketinggian) | I2C | **90.000** | BME280 alternatif Rp 40–80 rb |
| 35 | MPU-6050 accelerometer | I2C | **25.000** | |
| 36 | OLED SSD1306 128×64 | I2C 0x3C | **30.000** | |
| 37 | SIM7080 LTE-M/NB-IoT breakout | + antena | **350.000** | Modul + SIM kartu data terpisah |
| 38 | GNSS u-blox NEO-M8N/MAX-M10S + antena patch IP67 | PPS | **400.000** | NEO-6M murah Rp 80 rb tapi akurasi turun |
| 39 | RTC DS3231 + CR1220 | | **30.000** | |
| 40 | Relay + driver MOSFET + flyback (kontrol inverter/kompresor) | | **60.000** | |
| 41 | RCD 30 mA + colokan AC + flap | | **150.000** | |
| 42 | Buzzer + LED ×3 + resistor + PCB kecil + konektor | | **100.000** | |
| 43 | Buck LM2596 + LDO + TVS + kapasitor | | **80.000** | |
| 44 | Kotak elektronik foam-potted + panel depan (bezel anodised) | 130 × 80 × 60 | **250.000** | |
| 45 | Antena LTE + kabel coax SMA | | **100.000** | |

**Subtotal elektronik: Rp 1.895.000** (≈ USD 105)

---

## 4. Rekap total per unit (harga terendah)

| Blok | Harga (Rp) | ≈ USD |
|---|---|---|
| Cold box (mekanik + termal) | 6.955.000 | 386 |
| Machine tier (tenaga + pendinginan, tanpa PV deployable) | 9.270.000 | 515 |
| Elektronik & telemetri | 1.895.000 | 105 |
| **Total komponen (BOM)** | **Rp 18.120.000** | **≈ 1.005** |
| Perakitan, brazing refrigeran, kalibrasi, ujicoba, container | + Rp 2.500.000 | + 139 |
| **Total per unit siap pakai** | **≈ Rp 20.620.000** | **≈ USD 1.145** |

> Ini **floor budget** — realita pembelian biasanya 10–30% di atas angka ini. Untuk anggaran esai, pakai floor + kontingensi 15% ≈ **Rp 23.700.000 (≈ USD 1.320)**.
> Bandingkan: revisi lama (DC 20 Ah) diestimasi Rp 15 – 28,6 jt — kenaikan utama dari baterai 100 Ah (+Rp 2–3 jt), inverter (+Rp 1,4 jt), dan VIP yang tetap dominan.

---

## 5. Biaya operasional & TCO 5 tahun (per unit, harga terendah)

| Item | Interval | Asumsi biaya |
|---|---|---|
| Listrik charging station | bulanan | ≈ 810 Wh/hari × 30 hari = 24 kWh × Rp 1.500/kWh = **Rp 36.000/bulan** |
| Kuota SIM data (LTE-M) | bulanan | **Rp 25.000/bulan** |
| Penggantian sachet silica | tahunan | Rp 25.000 |
| Kalibrasi probe (bandingkan referensi) | tahunan | **Rp 150.000** |
| Servis ringan (gasket, sekring, kipas) | tahunan | **Rp 200.000** |
| **OPEX tahunan** | | **≈ Rp 1.100.000** |
| Penggantian baterai (end of life ~2.000 siklus ≈ 5–7 thn) | sekali / 5–7 thn | Rp 2.600.000 |
| Penggantian VIP (jika bocor, jarang) | 10+ thn | Rp 1.600.000 |

**TCO 5 tahun per unit: ≈ Rp 26.200.000** (≈ USD 1.455)
(BOM Rp 20,62 jt + OPEX 5 thn Rp 5,54 jt; baterai baru +Rp 2,6 jt bila perlu di tahun ke-6)

> ≈ Rp 435.000/bulan. Bandingkan dengan nilai satu pengiriman vaksin yang rusak (jutaan–puluhan juta rupiah per kejadian) — inilah argumen ekonomi esai.

---

## 6. Sensitivitas harga — 3 varian konfigurasi

| Varian | Perbedaan utama | Estimasi total unit |
|---|---|---|
| **Hemat** | PUR 40 mm (bukan VIP), PCM gel lokal, kompresor DC 12/24 V (tanpa inverter), baterai 50 Ah | **≈ Rp 14.000.000** (USD 778) |
| **Baseline (desain ini)** | VIP 25 mm, GQR30TG + inverter, baterai 100 Ah, PV on-board 20 W | **≈ Rp 20.600.000** (USD 1.145) |
| **Premium** | VIP + kondensor uprated + baterai 150 Ah + inverter Victron + PV deployable 200 W + dual sensor | **≈ Rp 34.000.000** (USD 1.889) |

> Varian "Hemat" adalah fallback esai jika VIP tidak terjangkau — geometri berubah (kotak lebih besar, PCM 12 kg), tapi konsep dan elektronik tetap.

---

## 7. Harga yang wajib di-RFQ (paling berfluktuasi)

1. **Baterai LiFePO₄ 100 Ah** — harga paling volatil; selisih merek bisa 2×. Wajib cek garansi siklus.
2. **Inverter pure sine 1.000 W dengan surge ≥2.000 VA** — uji dulu dengan motor RSIR; unit murah sering gagal start.
3. **VIP panel** — harga per m²; import L/C biasanya min. order.
4. **PCM salt hydrate siap pakai** — harga per kg sangat bervariasi (Rp 150–400 rb/kg); DIY jauh lebih murah tapi kualitas tidak terjamin.
5. **GQR30TG** — pastikan ketersediaan + datasheet input daya, LRA, refrigeran, rating ketinggian.
6. **Panel surya semi-flex 20 W** — harga per watt; cek garansi vs rigid.

---

## 8. Catatan mata uang & inflasi

- Semua angka dalam **Rupiah, asumsi kurs Rp 18.000/USD**, inflasi komponen impor ±5–10%/tahun.
- Harga e-commerce Tokopedia/Shopee sering lebih murah 10–30% dari harga distributor — angka di sini pakai rentang wajar retail.
> Untuk anggaran esai dipakai **harga terendah dari tiap rentang** (skenario hemat, sourcing e-commerce) — bukan titik tengah. Angka Rupiah tetap rentang penuh; USD mengikuti harga terendah.
