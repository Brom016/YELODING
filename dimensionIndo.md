# dimensionIndo.md — Lembar dimensi (revisi ringkas · pembaruan tenaga kompresor AC)

> Versi bahasa Indonesia dari `dimension.md`. Semua angka identik dengan versi Inggris; jika ada perbedaan, `dimension.md` yang berlaku.
> Pendamping `detailIndo.md`. Angka saja, tanpa turunan. Semua nilai [estimate] kecuali ditandai [benchmark] atau [verify]. Inti payload ditetapkan 40 × 25 × 30 cm = 30,0 L.
> Perakitan akhir: **49 × 35 × 74,2 cm (termasuk cover PV on-board), ≈ 48 kg kosong, ≈ 63 kg termuat (+15 kg payload).**
> Baseline tenaga: kompresor AC GQR30TG (pendinginan 245 W) · LiFePO₄ 12,8 V 100 Ah · inverter 1.000 W PSW · PV on-board 20 W di bawah cover pelindung · charging station (charger grid baseline / opsyen PV deployable).

## 1. Ruang payload (inti, wajib)

| Parameter | Nilai |
|---|---|
| Dimensi internal | 400 × 250 × 300 mm |
| Volume bersih | 30,0 L [benchmark] |
| Guna setelah rak | 3 tray, masing-masing ≤ 90 mm |
| Bukaan tutup | 415 × 285 mm, engsel belakang, gasket double-lip, lug segel tamper |
| Operasi tutup | membuka ke belakang (engsel di tepi panjang belakang); terayun ke atas dan istirahat terbuka ~120° — tanpa penyangga pada massa ini |
| Muka interior tutup | liner PP food-grade 2 mm + VIP 25 mm |
| Sachet silica gel | 20 g, diklip di sudut interior tutup; diganti tahunan |

## 2. Susunan dinding (dalam → luar) — tidak berubah

| Lapisan | Ketebalan | Tambahan per sumbu |
|---|---|---|
| Pelat PCM, 2 dinding panjang + lantai | 13 mm | +2,6 cm (Y), +1,3 cm (Z) |
| Liner, PP food-grade | 2 mm per sisi | +0,4 cm (X, Y, Z) |
| Pelat evaporator, aluminium + kipas 80 mm | 12 mm | +1,2 cm (Z saja) |
| Panel VIP, 6 sisi | 25 mm | +5,0 cm (X, Y, Z) |
| Kulit HDPE | 2 mm per sisi | +0,4 cm (X, Y, Z) |

Pemeriksaan tumpukan, sumbu per sumbu:

| Sumbu | Penjumlahan | Hasil |
|---|---|---|
| X: 0,2+2,5+0,2+40+0,2+2,5+0,2 | 45,8 cm | tidak ada PCM di dinding pendek |
| Y: 0,2+2,5+0,2+1,3+25+1,3+0,2+2,5+0,2 | 33,4 cm | dinding PCM termasuk |
| Z: 0,2+2,5+0,2+1,2+1,3+30+0,2+2,5+0,2 | 38,3 cm | evaporator di bawah PCM lantai |

## 3. Pelat PCM (salt hydrate, melt 5–6 °C, ρ 1,5 kg/L) — tidak berubah

| Pelat | Dimensi (mm) | Volume | Massa |
|---|---|---|---|
| A, dinding panjang (×2) | 400 × 313 × 13 | 1,63 L masing-masing | 2,44 kg masing-masing |
| B, lantai (×1) | 400 × 276 × 13 | 1,44 L | 2,15 kg |
| Total | | 4,70 L | **7,04 kg** |
| Kapasitas laten | 7,04 × 220 kJ/kg | 1.549 kJ | margin 34% atas kebutuhan 1,16 MJ |
| Holdover pasif | 24 jam pada ambient 38–42 °C | [estimate — profil uji diperlukan] |

## 4. Cold box (tier 2) — tidak berubah

| Parameter | Nilai |
|---|---|
| Eksternal | **458 × 334 × 383 mm** (58,6 L) |
| Warna kulit luar | **abu arang gelap**, RAL 7021, HDPE UV-stabilised |
| Garis aksen | **Sunlight Yellow**, RAL 1023, pita 5 mm di perimeter atas |
| Warna liner interior | putih pucat / PP natural food-grade |
| Tumpukan tutup (atas → bawah) | kulit 2 / VIP 25 / liner 2 |
| Tumpukan lantai (bawah → atas) | kulit 2 / VIP 25 / liner 2 / evaporator 12 / PCM 13 |
| Corner guard | 4 pcs, 30 × 30 × 20 mm, karet hitam |
| Tie-down eye | 4 pcs, M6, di sudut alas, powder-coat kuning |
| Handle | 2 sisi recessed, pegangan 160 × 60 mm |
| Latch | 2 depan, cam-action, stainless brushed; dilepas bersamaan |
| Hasp | 1 tengah-depan, menerima segel kawat atau gembok; segel putus menandai custody event |
| Engsel | 2 belakang, stainless brushed, 60 mm; baut M5 × 16 SS ke pelat penyangga HDPE |
| Katup penyama tekanan | 1 × ventilasi membran/duckbill Ø10–15 mm, dinding sisi atas; IPX4, menutup sendiri; menyamakan ΔP ketinggian (lihat §12.5) |

### Isi interior cold box — rinci

| Item | Rincian |
|---|---|
| Tray vaksin | 3 × tray PP lepas, ≤ 90 mm, footprint 395 × 245 mm |
| Pelat PCM A (×2) | slab 400 × 313 × 13 mm, dua dinding panjang interior; boss jarak 10 mm untuk sirkulasi udara |
| Pelat PCM B (×1) | slab 400 × 276 × 13 mm di lantai, di atas evaporator |
| Pelat evaporator | Al 6063, 400 × 250 × 4 mm, serpentin Cu terikat; −6 sampai −8 °C saat charging |
| Kipas sirkulasi | 80 × 80 × 15 mm aksial, tepi pendek lantai; 1 W, 2.000 RPM |
| Probe suhu | 3 × DS18B20: T1 tengah-atas, T2 tengah-bawah, T3 dinding tengah |
| Reed switch tutup | reed magnetik, dudukan rangka tutup |
| Blok sirip dingin TEC | 40 × 40 × 25 mm, sudut lantai; cadangan DC |
| Sachet silica gel | 20 g, interior tutup, diganti tahunan |

## 4a. Dek PV on-board dan cover pelindung (BARU)

| Parameter | Nilai |
|---|---|
| Panel | 20 W semi-flexible mono, ≈ **440 × 320 × 3 mm**, ≈ 0,7 kg [verify] |
| Pemasangan | direkatkan ke permukaan atas tutup dengan lem struktural di atas pelat adaptor datar; tanpa pengikat tembus-tutup |
| Sifat permanen | panel dan cover adalah bagian dari tutup: ikut berayun saat tutup dibuka dan ikut bepergian dengan kotak — **tanpa bongkar pasang, selamanya** |
| Gerak tutup | garis engsel ko-aksial: tutup payload membuka penuh ~120° dengan panel + cover menempel; loop kabel di sisi engsel diukur untuk jalur penuh |
| SOP cover | dibuka saat operasi dan charging (panel memanen); ditutup hanya untuk penyimpanan, stacking, hujan lebat, atau parkir berisiko pencurian |
| Footprint dek | 440 × 320 mm, terpusat di tutup, margin ≥ 9 mm ke setiap tepi |
| Batas teoretis | footprint 458 × 334 mm → maks ≈ 25 W; 20 W menjaga margin dan kelenturan sourcing |
| Cover | tutup datar HDPE berengsel **≈ 460 × 336 × 2 mm + frame 15 mm**, engsel belakang (ko-aksial dengan garis engsel tutup payload), membuka ~100° |
| Perangkat cover | 2 latch quarter-turn + lubang gembok; **terkunci** (anti-pencurian) |
| Deteksi cover | reed switch pada frame cover — **PV COVER OPEN adalah custody event yang tercatat** |
| Stacking | cover tertutup = dek datar 460 × 336; beban strap menumpang frame cover, bukan panel |
| Pengkabelan | kabel panel lewat sealed gland di tepi belakang tutup, turun di sisi engsel ke machine tier; gland IP67; loop kabel menampung buka penuh tutup |
| Tinggi tambahan | ≈ 10 mm (panel 3 + celah udara + cover 2 + frame) |
| Termal | panas panel berada di atas VIP tutup; tanpa efek payload yang terukur — VIP adalah penghalangnya |
| Energi | ≈ 65 Wh/hari ke baterai (4,5 PSH × 0,8 × 0,9); range extender saja — lihat `detailIndo.md` §6.7 |

## 5. Machine tier (tier 1) — DIREVISI

| Parameter | Nilai |
|---|---|
| Eksternal | **490 × 350 × 332 mm** (57 L) |
| Internal | **480 × 340 × 320 mm** (52,2 L) |
| Separator ke cold box | PUR 15 mm + aluminium 2 mm (total 17 mm) |
| Cangkang | plastik 2,5 mm; **exhaust 320 × 160 mm** di dinding Y+ di belakang kondensor (2 kipas 120 mm, finger guard, mesh); **inlet louvre 200 × 60 mm** di dinding ujung X−, seksi atas, 45° |
| Panel kontrol (muka depan) | panel 90 × 50 mm, sisi kiri; bezel anodised hitam; jendela OLED tersegel + gasket LED |
| Port input daya (muka depan) | barrel jack 12 V DC, sisi kanan; label kuning emboss; cover karet berengsel hitam |
| Colokan AC | colokan Schuko/universal 230 V AC + RCD 30 mA, di muka depan paling kanan (tutup rapat); untuk servis sisi kompresor dan alat station |
| Pemisahan AC/DC | ruang AC (inverter, RCD, colokan, kabel kompresor) berpelindung dari rel DC dan saluran kabel; tutup panel sekring terkunci sekrup |

### Tata letak internal (kecocokan terverifikasi)

| Item | Dimensi (mm) | Posisi (X, Y, Z dari titik nol tier) |
|---|---|---|
| Baterai LiFePO₄ 12,8 V 100 Ah, flat | 329 × 172 × 214 | 0–329, 0–172, 0–214 |
| Inverter 1.000 W PSW | 300 × 160 × 85 | 10–310, 10–170, 224–309 (di atas baterai, standoff karet 10 mm) |
| MPPT-A 10 A (PV on-board) | 168 × 100 × 30 | 10–178, 180–280, 0–30 |
| MPPT-B 20 A (input PV station) | 123 × 90 × 35 | 10–133, 180–270, 40–75 (ditumpuk di atas MPPT-A) |
| Kotak elektronik | 130 × 80 × 60 | 195–325, 180–260, 0–60 |
| Kompresor GQR30TG (Ø130, vertikal) | 140 × 140 × 170 amplop | 335–475, 5–145, 0–170 |
| Kondensor + 2 kipas 120 mm | face 280 × 150, dalam 80 | 100–380, 260–340, 30–180 (dinding Y+) |
| Panel sekring + sekring utama + distribusi DC | 140 × 100 × 100 | 340–480, 150–250, 0–100 |
| Colokan AC + modul RCD | 90 × 70 × 60 | 390–470, 260–330, 0–60 |
| Konektor input PV (kit station) | Plug gaya-solar, bulkhead IP67 | muka belakang, kanan antena |
| Saluran kabel | strip tersisa | X 380–480, Y 260–340, Z 180–320; X 310–480, Y 0–150, Z 170–220 |
| Heatsink sisi panas TEC | 60 × 60 × 20 | menembus separator, sudut lantai X 5–65, Y 190–250, Z 170–190 |
| Antena GNSS + LTE | patch 25 × 25 mm, bulkhead eksternal | muka belakang, sudut diagonal, ≥ 250 mm terpisah |

Pemeriksaan kecocokan:
- Baterai ↔ inverter: standoff 10 mm di atas puncak baterai; terminal inverter menghadap tepi servis depan.
- Baterai ↔ kompresor: terpisah sumbu X (329 vs 335).
- Inverter ↔ kondensor: terpisah sumbu Y (≤ 170 vs ≥ 260).
- MPPT / elektronik ↔ kondensor: Y ≤ 301 / ≤ 260 dengan kondensor mulai 260 dan Z ≥ 30 → elektronik dibatasi Y ≤ 260.
- Panel sekring ↔ kompresor: terpisah sumbu Y (≥ 150 vs ≤ 145).
- Colokan AC ↔ kondensor: terpisah sumbu X (≥ 390 vs ≤ 380).
- Massa baterai (10,5 kg) di lantai tier → pusat gravitasi rendah.

### Rincian panel kontrol (muka depan, sisi kiri)

| Bagian | Spesifikasi | Posisi di panel |
|---|---|---|
| Layar OLED | SSD1306 128 × 64 px, I2C 0x3C; jendela akrilik tersegel | kiri-atas |
| LED — hijau | 5 mm, kompresor berjalan | kolom kanan, atas |
| LED — merah | 5 mm, ekskursi / karantina | kolom kanan, tengah |
| LED — kuning | 5 mm, baterai lemah | kolom kanan, bawah |
| Grille buzzer | buzzer aktif 5 V, 3 × Ø2 mm | kiri-bawah |
| Isi OLED | state · T1/T2 °C · PCM % / HOLD jam · BAT V / CMP · INV on/off | — |

### Rincian port input daya (muka depan, sisi kanan)

| Parameter | Nilai |
|---|---|
| Konektor | barrel jack 5,5 × 2,1 mm, pusat positif |
| Tegangan | 12 V DC nominal (10,5–14,6 V) |
| Arus maksimum | 10 A (disekring); **hanya elektronik dan beban DC** — kompresor AC tidak pernah berjalan dari port ini |
| Cover | flap karet berengsel pegas, IP54 saat tertutup |
| Ganda-gunakan | socket kendaraan untuk beban DC / top-up lambat via charger DC-DC opsional; kabel PV station di titik charging |

## 6. Elektronik (papan kontroler)

| Bagian | Nilai / spesifikasi | Jumlah |
|---|---|---|
| Papan MCU | ESP32-WROOM-32 | 1 |
| Probe suhu | DS18B20 waterproof, kabel 1,5 m | 3 |
| Resistor pull-up | 4,7 kΩ, 1/4 W | 1 per bus |
| Sensor ambient | DHT22 (atau SHT4x) | 1 |
| Barometrik + kelembapan (berfungsi ganda sebagai log ketinggian) | BMP390 (atau BME280), I2C | 1 |
| Accelerometer | MPU-6050, I2C | 1 |
| Layar | OLED SSD1306 128×64, I2C 0x3C | 1 |
| Seluler | SIM7080 LTE-M / NB-IoT | 1 |
| Penerima GNSS | kelas u-blox NEO-M8N / MAX-M10S, UART + PPS | 1 |
| RTC | DS3231, ±2 ppm | 1 |
| Backup GNSS | coin cell CR1220 pada V_BCKP | 1 |
| Antena GNSS | patch aktif 25 × 25 mm, IP67, bulkhead SMA | 1 |
| Buzzer | aktif, 5 V | 1 |
| Input tach kipas | monitor RPM, alarm stall | 3 (2 kondensor + 1 sirkulasi) |
| LED indikator | 5 mm, hijau / merah / kuning | 3 |
| Resistor seri LED | 220 Ω, 1/4 W | 3 |
| Kapasitor decoupling | 100 nF keramik, per IC | 4+ |
| Kapasitor bulk | 470 µF elektrolitik, 16 V, di rel 12 V | 1 |
| Dioda TVS | SMBJ15A pada input 12 V | 1 |
| Pembagi sense baterai | 10 kΩ + 3,3 kΩ, 1% | 1 pasang |
| Buck converter | modul LM2596, 12 V → 5 V, 3 A | 1 |
| LDO | AMS1117-3.3 | 1 |
| Kontrol kompresor | relay remote-enable inverter (koil DC 12 V) + dioda flyback | 1 |
| Sekring utama | Blade/ANL: 40 A utama baterai, 30 A inverter, 30 A MPPT-B, 5 A MPPT-A, 15 A PV, 15 A distribusi DC | 6 |
| Dioda pemblokiran | Schottky, input PV | 1 |
| RCD / GFCI | 30 mA, pada colokan AC 230 V | 1 |

## 7. Sistem tenaga

| Item | Dimensi (mm) | Massa | Catatan |
|---|---|---|---|
| Baterai LiFePO₄ 12,8 V 100 Ah | 329 × 172 × 214 | 10,5 kg [verify] | BMS terintegrasi, ≥ 100 A kontinu |
| Inverter pure sine 1.000 W | 300 × 160 × 85 | 2,2 kg [verify] | 12 V DC → 230 V AC, surge ≥ 1.500–2.000 VA, eco ≤ 2 W |
| MPPT-A 10 A (PV on-board) | 168 × 100 × 30 | 0,3 kg [verify] | input panel 20 W |
| MPPT-B 20 A (PV station) | 123 × 90 × 35 | 0,5 kg [verify] | input PV deployable, konektor bulkhead belakang |
| PV on-board 20 W semi-flexible | ≈ 440 × 320 × 3 | 0,7 kg [verify] | direkatkan di atas tutup, di bawah cover |
| Cover pelindung PV | 460 × 336 × 2 + frame | 0,9 kg | berengsel, terkunci, dimonitor reed switch |
| Kompresor AC GQR30TG | Ø130 × 165 t | 8,0 kg [verify] | 220–240 V, pendinginan 245 W, 1/10 HP RSIR, start PTC |
| Kondensor wire-tube + 2 kipas 120 mm | 280 × 150 face, dalam 80 | 1,9 kg | pembuangan 365 W, ≈ 64 CFM melalui core |
| Pelat evaporator (coil-bonded) | 400 × 250 × 12 | 2,0 kg | serpentin Cu + kipas 80 mm |
| Charger grid station (baseline) | 14,6 V / 20 A | 1,2 kg | tetap di station charging |
| PV deployable 200 W lipat (opsyen) | ≈ 600 × 430 × 50 terlipat | ≈ 8 kg [verify] | tetap di station; menyuplai MPPT-B via konektor belakang |
| Charger DC-DC opsional | 12 V / 20 A | 0,8 kg | charging alternator saat berkendara |

### Setpoint proteksi

| Item | Nilai |
|---|---|
| Sekring utama baterai | 40 A |
| Cabang inverter | 30 A, kabel 10 mm², ≤ 0,5 m |
| MPPT / PV | cabang MPPT-B 20 A, sekring sisi PV 15 A, MPPT-A 5 A |
| Distribusi DC | 15 A |
| Output AC | RCD 30 mA |
| LVD baterai (BMS + firmware) | beban dilepas di bawah 11,0 V, potong keras 10,5 V |

## 8. Perakitan akhir

| Parameter | Nilai |
|---|---|
| Keseluruhan (P × L × T) | **490 × 350 × 742 mm** termasuk cover PV, footprint berundak |
| Cold box | 458 × 334 × 383 mm |
| Dek PV + cover (di tutup) | ≈ 460 × 336 × 10 mm |
| Machine tier | 490 × 350 × 332 mm |
| Volume eksternal total | ≈ 119 L |
| Volume payload | 30,0 L bersih [benchmark] |
| Berat kosong | **≈ 48 kg** |
| Massa baterai | 10,5 kg [verify] |
| Berat, +15 kg payload | **≈ 63 kg** |
| Energi PV on-board | ≈ 65 Wh/hari — range extender saja |
| Kit charging station | charger grid 1,2 kg (baseline) atau PV deployable ≈ 8 kg (opsyen) |
| Pusat gravitasi | rendah — baterai di lantai tier |
| Pengangkutan | **angkat 2 orang + trolley wajib**; 4 × tie-down eye M6 |
| Basis trolley | +40 mm, +4 kg |

## 9. Perbandingan dengan revisi sebelumnya

| Parameter | 20 Ah / DC (lama) | **100 Ah / AC (kini)** |
|---|---|---|
| Keseluruhan | 460 × 335 × 575 mm | **490 × 350 × 742 mm** |
| Volume eksternal | 89 L | **119 L** |
| Payload | 30,0 L | 30,0 L |
| Kebocoran panas | 9 W | 9 W (10 W pada 42 °C) |
| Massa PCM | 7,0 kg | 7,0 kg |
| Kompresor | DC BD35F, 115 W pendinginan | **AC GQR30TG, 245 W pendinginan** |
| Daya input pendinginan | 88 W DC | **145 W AC / 161 W sisi-DC [estimate]** |
| Baterai | 240 Wh (216 guna) | **1.280 Wh (1.024 guna)** |
| PV | 200 W terpisah | **20 W on-board di bawah cover + kit station** |
| Inverter | tidak ada | **1.000 W PSW** |
| Energi harian | ≈ 385 Wh | **≈ 810 Wh** |
| Otonomi aktif | ≈ 15 jam | **≈ 30 jam** |
| Pasif + telemetri | ≈ 18 jam | **≈ 94 jam** |
| Berat kosong | ≈ 28,5 kg | **≈ 48 kg** |

### Perbandingan kapasitas baterai (untuk argumen sizing esai)

| Kapasitas | Guna @ DoD 80% | Operasi aktif | Pasif + telemetri | Putusan |
|---|---|---|---|---|
| 20 Ah (240 Wh) | 192 Wh | ≈ 6 jam | ≈ 19 jam | tidak memadai untuk beban AC |
| 50 Ah (640 Wh) | 512 Wh | ≈ 15 jam | ≈ 46 jam | minimum absolut |
| 80 Ah (1.024 Wh) | 819 Wh | ≈ 24 jam | ≈ 74 jam | minimum untuk hari full-aktif 24 jam |
| **100 Ah (1.280 Wh)** | **1.024 Wh** | **≈ 30 jam** | **≈ 94 jam** | **dipilih — margin sehat** |
| 150 Ah (1.920 Wh) | 1.536 Wh | ≈ 45 jam | ≈ 140 jam | berlebihan untuk duty ini; +5 kg, +8 L |

## 10. Loop pendinginan — DIREVISI

### 10.1 Titik desain siklus

| Parameter | Nilai | Catatan |
|---|---|---|
| Suhu evaporasi | −8 °C | pelat harus berada di bawah titik bekukan PCM 5–6 °C |
| Suhu kondensasi | 50–55 °C | ambient 40 °C, bay mesin hingga 50 °C |
| Kapasitas pendinginan | 245 W rating → ≈ 220 W pada desain [estimate] | [verify] kondisi rating |
| Input listrik | 145 W baseline (skenario 130–180 W) | [verify] |
| COP | ≈ 1,5 pada desain | 1,2–1,7 lintas skenario |
| Panas dibuang | **≈ 365 W** | kapasitas + input |
| Refrigeran | R134a atau R600a, charge menunggu konfirmasi | [verify] — R600a mudah terbakar, bay tetap berventilasi |
| Ekspansi | kapiler, orifice tetap | [verify] panjang/ID dari kit kompresor |
| Recharge PCM penuh | 1.549 kJ pada 210 W bersih = **2,1 jam** | lebih cepat dari desain DC lama |

### 10.2 Evaporator (cold plate) — tidak berubah

| Bagian | Spesifikasi |
|---|---|
| Pelat dasar | aluminium 6063, 400 × 250 × 4 mm, anodized |
| Coil | tembaga Ø8 × 0,5 mm dinding, serpentin 6-pass, 2,8 m, epoksi termal di alur miling |
| Penjepit | bar 400 × 30 × 4 mm, 6 × baut M5 |
| Suhu permukaan saat charging | −6 sampai −8 °C |
| Massa | 2,0 kg termasuk kipas 80 mm |
| Embun beku | dapat diabaikan di ruang 2–8 °C; 20 g silica gel di payload |

### 10.3 Kipas sirkulasi — tidak berubah

| Spesifikasi | Nilai |
|---|---|
| Ukuran | 80 × 80 × 15 mm aksial |
| Daya | 12 V, 0,08 A, ≈ 1 W |
| Aliran udara | 30 CFM free air |
| Putaran / bising | 2.000 RPM, ≤ 24 dBA |
| Tugas | kontinu, dijepit di tepi pendek pelat lantai |

### 10.4 Kondensor — DIREVISI

| Spesifikasi | Nilai |
|---|---|
| Tipe | wire-tube, tembaga Ø6 dengan kawat baja, 3 baris |
| Face | **280 × 150 mm**, rapat di dinding Y+ |
| Permukaan kawat | ≈ 0,62 m², UA ≈ 35 W/K |
| Tugas | **pembuangan 365 W** pada ΔT udara ≈ 10 K |
| Aliran udara dibutuhkan | ≈ 64 CFM melalui core |

### 10.5 Kipas kondensor — DIREVISI (2 unit)

| Spesifikasi | Nilai |
|---|---|
| Ukuran / jumlah | 120 × 120 × 25 mm aksial, **2 pcs** |
| Daya | 12 V, 0,20 A masing-masing (total 4,8 W) |
| Aliran udara | 65 CFM free air masing-masing, ≈ 90 CFM free gabungan |
| Putaran / bising | 1.900 RPM masing-masing, ≈ 30 dBA gabungan |
| Bearing + umpan balik | dual ball, kabel tach per kipas |
| Interlock | firmware tidak akan menjalankan kompresor saat tach mana pun membaca nol |
| Dudukan | grommet karet, menarik udara bay melalui kondensor dan keluar |

### 10.6 Ventilasi dan aliran udara — DIREVISI

| Bukaan | Ukuran | Posisi |
|---|---|---|
| Exhaust | **320 × 160 mm** | dinding sisi Y+ di belakang kondensor, finger guard + mesh serangga |
| Inlet | **200 × 60 mm** | dinding ujung X−, seksi atas, louvre 45°, mesh |
| Jalur | inlet → melintasi bay melewati elektronik DC → kompresor → kipas → kondensor → exhaust |
| Drainase | Ø8 mm | lantai bay, sudut terendah |

### 10.7 Jalur refrigeran

| Jalur | Spesifikasi |
|---|---|
| Discharge | tembaga Ø6, 150 mm, kompresor ke kondensor |
| Kapiler | orifice tetap, dililit di outlet kondensor |
| Suction | tembaga Ø8, 250 mm, isolasi busa 10 mm, grommet tersegel menembus separator |
| Sambungan | dibrazing; port Schrader opsional |

### 10.8 Modul TEC trim — tidak berubah (cadangan DC)

| Bagian | Spesifikasi |
|---|---|
| Modul | Peltier 40 × 40 mm, maks 60 W, dijalankan 20 W |
| Sisi dingin | blok sirip 40 × 40 × 25 mm, sudut lantai cold box |
| Sisi panas | heatsink 60 × 60 × 20 mm di machine tier |
| Peran | menahan kebocoran 10 W selama ≈ 31 jam hanya dengan baterai (COP 0,45 → 22 W + 11 W beban DC) bila kompresor atau inverter gagal |

## 11. Penerima GNSS, antena, dan waktu — tidak berubah

| Item | Spesifikasi |
|---|---|
| Modul | kelas u-blox NEO-M8N atau MAX-M10S, multi-GNSS |
| Antarmuka | UART2, GPIO16 RX / GPIO17 TX, NMEA 9600 baud |
| Output PPS | GPIO35, mendisiplinkan jam sistem |
| Suplai | 3,3 V, ≈ 0,15 W |
| Akurasi | 2,5 m CEP langit terbuka [benchmark]; 3–6 m pada patch menghadap samping |
| Antena | patch aktif 25 × 25 mm, IP67 bulkhead, muka belakang sudut atas; antena LTE sudut diagonal ≥ 250 mm terpisah |
| Ground plane | foil tembaga 100 × 100 mm |
| Jam | PPS GNSS mengatur jam; DS3231 menahan waktu saat outage; flag sumber jam per catatan |
| Privasi | 4 desimal (≈ 11 m) di telemetri; 5 desimal hanya untuk peran QA |

## 12. Matriks telemetri, hujan, getaran, keselamatan AC

### 12.1 Matriks telemetri

| Parameter | Sensor | Interval | Saat link putus |
|---|---|---|---|
| Suhu payload, 3 titik | DS18B20 | 30 detik [benchmark] | buffer 72 jam, sinkron saat tersambung kembali |
| Suhu ambient + kelembapan | DHT22 / SHT4x | setiap catatan | sama |
| Tekanan barometrik | BMP390 | setiap catatan | sama |
| Posisi, kecepatan, HDOP, satelit | GNSS, 1 Hz internal | setiap catatan | sama; gap dicatat, tidak pernah diinterpolasi |
| Tegangan baterai | pembagi di ADC | setiap catatan | sama |
| Keadaan tutup | reed switch | event + setiap catatan | sama |
| Keadaan cover PV | reed switch cover | event + setiap catatan | sama |
| Getaran RMS | accelerometer | setiap catatan + event ambang | sama |
| Duty kompresor + state inverter | penghitung runtime + umpan balik relay | setiap catatan | sama |
| Sumber jam | PPS GNSS / RTC | per catatan | drift ditandai |

Tangga fallback: LTE-M dulu, NB-IoT kedua, lalu buffer store-and-forward 72 jam. Buzzer lokal dan OLED tidak pernah bergantung pada link.

### 12.2 Hujan dan masuknya air

| Jalur | Perlindungan |
|---|---|
| Tutup | gasket double-lip + hasp segel-tamper |
| Kabel probe dan antena | sealed gland; bulkhead antena IP67 |
| Ventilasi | louvre 45° + mesh serangga; drainase Ø8 mm di lantai bay |
| Panel kontrol | jendela OLED tersegel, gasket LED |
| Colokan AC | flap pegas, minimum IP44, pelindung tetes di atasnya |
| PCB | coating akrilik konformal, konektor terplating |
| Target | IPX4 tegak untuk seksi DC; seksi AC minimum IP44 |
| Risiko tersisa | hujan geladak lebat: terpal sesuai SOP; jangan pernah tenggelam; panel PV tetap teduh di station |

### 12.3 Getaran

| Sumber | Mitigasi |
|---|---|
| Kompresor | 4 dudukan karet, 30 Shore, M6 |
| Kipas | grommet karet |
| Baterai | strap penahan + alas karet; terminal diberi strain relief |
| Inverter | 10 mm standoff karet di atas baterai, dijepit |
| Pelat PCM | celah busa + boss jarak 10 mm |
| Elektronik | kotak terisi busa (foam-potted) |
| Kotak di kendaraan | 4 × tie-down eye M6, strap sesuai SOP |
| Panel VIP | di belakang kulit, corner guard |
| Loop kabel PV | lengan bebas di sisi engsel, tanpa tarikan kaku saat tutup membuka |

Deteksi: RMS accelerometer di atas ambang → event VIBRATION HIGH; getaran berkelanjutan menandai dudukan pelat PCM dan strap baterai untuk pemeriksaan.

### 12.4 Keselamatan AC (baru)

| Item | Aturan |
|---|---|
| Ruang AC | inverter + RCD + colokan + kabel kompresor dipisahkan dari rel DC oleh pelat penghalang |
| RCD | 30 mA pada colokan AC; tombol uji terjangkau saat servis |
| Bonding | output floating inverter di-bonding sesuai manualnya; kontinuitas PE diperiksa saat commissioning |
| Label | "230 V AC — lepas inverter sebelum servis" pada setiap panel lepas di atas terminal AC |
| Panel sekring | tutup terkunci sekrup, bukan bebas-alat |
| Jalur kabel | harness AC dan DC di sisi berlawanan bay, menyilang 90° bila tak terhindarkan |
| Bay kompresor | berventilasi, berdrainase, pelindung tetes di atas elektronik |

### 12.5 Ketinggian dan tekanan (operasi pegunungan)

Amplop desain: permukaan laut sampai 3.000 m. Machine tier berventilasi (menyamakan tekanan sendiri); cold box yang tersegel mendapat satu katup penyama tekanan.

| Item | Spesifikasi / efek |
|---|---|
| Katup penyama tekanan | 1 × ventilasi membran atau duckbill, Ø10–15 mm, dinding sisi atas (atau frame tutup), IPX4, menutup sendiri |
| ΔP tutup terburuk tanpa katup | ≈ +18 kPa pada 2.500 m (tersegel hangat di permukaan laut) → ≈ 2,1 kN angkat pada tutup 415 × 285 — beban latch, bukan beban gasket; dengan katup ≖ 0 |
| Kondensor pada 2.000 m | densitas udara −20% (tekanan turun ≈ 1,2 kPa per 100 m) → UA ≈ 29 W/K, kondensasi +2–3 K, kapasitas −10–20% pada 2.000 m (aturan praktis industri: kehilangan 5–10% per 1.000 m) — dapat diterima dengan monitoring duty; rating ketinggian kompresor [verify]. Pada hari 22 °C di dataran tinggi, suhu kondensasi tetap ≈ 34 °C, lebih baik dari kasus terburuk ≈ 50 °C di permukaan laut |
| Pelat PCM | headspace isi 10–15% + diafragma relief atau dinding bergerigi [verify dengan pemasok] |
| BMP390 | mencatat tekanan setiap catatan → ketinggian; event ALTITUDE HIGH di atas ambang yang bisa diatur (default 2.000 m) |
| Sisi 230 V | clearance terderating di atas 2.000 m per IEC 60664 [verify untuk deployment dataran tinggi] |
| Keuntungan termal | ambient pegunungan 15–25 °C → kebocoran ≈ 4–5 W, holdover > 24 jam dengan leluasa |

> Sumber: kurva tekanan atmosfer standar (≈ −1,2 kPa per 100 m, formula barometrik); data lapangan cabinet-AC dataran tinggi (kehilangan pendinginan ≈ 5–10% per 1.000 m); derating listrik di atas 2.000 m (panduan Schneider Electric, IEC 60664). Embraco/Nidec menerbitkan buletin teknis "High Altitude Effects on Refrigeration Systems" — minta bersama datasheet GQR30TG.

## 13. Ringkasan skema warna — tidak berubah

| Zona | Warna | Alasan |
|---|---|---|
| Kulit HDPE luar | RAL 7021 abu arang gelap | konsistensi identitas; menyembunyikan kotoran lapangan |
| Garis aksen + sekitar tie-down | RAL 1023 Sunlight Yellow | prioritas medis, visibilitas tinggi |
| Liner PP interior | putih natural | inspeksi higiene |
| Perangkat keras stainless | silver brushed | ketahanan korosi pesisir |
| Corner guard | karet hitam matte | kontras + benturan |
| Bezel kontrol | aluminium anodised hitam | tampilan instrumen |
| OLED | navy #001a33 / cyan #00ccff | kontras siang hari |
| LED | hijau #00ff44 · merah #ff2200 · kuning #ffcc00 | konvensi ISO |
| Frame PV | aluminium abu gelap | — |
| Sel PV | navy gelap | monocrystalline |

Catatan: kulit gelap menanggung ≈ 2 W gain surya-ekuivalen ekstra (sudah di dalam anggaran 1,16 MJ). Jika pilot menunjukkan duty di atas model, fallback-nya adalah varian kulit abu terang RAL 7035 — geometri, PCM, dan sistem tenaga tidak terpengaruh.

## 14. Datasheet yang masih harus diverifikasi

| # | Item | Yang dibutuhkan |
|---|---|---|
| 1 | Kompresor GQR30TG | input W pada kondisi desain, arus jalan, LRA, refrigeran + charge, spesifikasi kondensor, massa, dimensi |
| 2 | Baterai 100 Ah | dimensi persis, massa, tata letak terminal, kontinu/puncak BMS, cycle life |
| 3 | Inverter 1.000 W PSW | rating surge + durasi, efisiensi part-load, tarikan no-load, auto-restart eco dengan beban induktif |
| 4 | PV on-board 20 W | dimensi persis vs dek 440 × 320, massa, lem perekat, toleransi output |
| 5 | Cover PV | rating IP engsel/latch, kompresi seal, spesifikasi kunci |
| 6 | MPPT-A 10 A / MPPT-B 20 A | PV Voc maksimum, konsumsi sendiri, profil charge |
| 7 | Charger grid station | profil 14,6 V / 20 A vs spesifikasi BMS |
| 8 | PV deployable 200 W (opsyen) | dimensi terlipat, massa, standar konektor |
| 9 | Pemasok PCM | panas laten, densitas, toleransi melt, stabilitas siklus |
| 10 | Pemasok VIP | sertifikat k aged |
| 11 | Modul RCD/colokan | rating IP, kedalaman pemasangan |
| 12 | Rating ketinggian kompresor | plafon operasi terverifikasi (target ≤ 3.000 m) |
| 13 | Pelat PCM | headspace pengisian + spesifikasi relief tekanan untuk transportasi ketinggian |
| 14 | Katup penyama tekanan | aliran udara, rating IP, masa pakai membran |
