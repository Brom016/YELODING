# Kotak Vaksin Hibrida PCM–Kompresor dengan Log Suhu Offline: Menjaga Vaksin 2–8 °C Selama 24 Jam hingga Pulau Terpencil

*International Student Essay Challenge — Smart Healthcare & Cold Chain Logistics*
*UNWAHAS × UMK × Cavite State University — Grup 5*

> **Catatan revisi.** Dokumen ini adalah versi Markdown dari *Grup 5 yeloding.docx* dan menjadi dokumen utama esai. Konsep, struktur, dan gaya penulisan docx dipertahankan; angka-angka teknis diperbarui agar konsisten dengan desain terkini (`detail.md`, `dimension.md`, `price.md`) dan dengan simulasi Wokwi (`wokwi/sketch.ino`, `wokwi/dashboard.html`) yang menjadi bukti logika kendali. Perubahan besar dari draf awal: isolasi PUR 5 cm → **VIP 25 mm**; PCM 11–12 kg → **7,04 kg**; pendinginan pasif murni → **hibrida** (pasif selama transit, kompresor AC GQR30TG di titik stasioner); WiFi lokal → **telemetri LTE-M/NB-IoT dengan log rantai hash**; bobot 18–20 kg → **≈ 48 kg kosong** (dinyatakan jujur, lihat §4.2). Label: **[benchmark]** = angka dari brief penyelenggara; **[estimate]** = perhitungan kami, asumsi dinyatakan; **[sim]** = terverifikasi pada simulasi Wokwi; **[verify]** = menunggu datasheet/RFQ.

---

## Ringkasan Eksekutif

**Masalah.** Vaksin, reagen biologis, dan pasokan medis sensitif suhu harus diangkut dalam kondisi terkendali, terutama pada rentang 2–8 °C. Di daerah terpencil dan pesisir, produk ini sering rusak sebelum sampai tujuan karena listrik padam, kotak sering dibuka, panas luar tinggi, dan perjalanan panjang. Kerusakan itu tidak terlihat: vaksin tampak normal, tetapi perlindungannya berkurang. Dampaknya nyata. Pada 2025 Indonesia mencatat 63.769 kasus suspek campak dan 69 kematian, dan di Sumenep 16 dari 17 anak yang meninggal tidak pernah diimunisasi.

**Solusi.** Kami mengusulkan kotak vaksin 30 liter [benchmark] berarsitektur **hibrida**: **PCM dan isolasi vakum (VIP) sebagai tulang punggung termal** selama perjalanan — suhu bertahan ≥ 24 jam [estimate] tanpa listrik — dan **kompresor AC GQR30TG** yang membekukan ulang PCM di titik stasioner serta menjaga suhu saat kotak menyala. Tenaga datang dari baterai LiFePO₄ 100 Ah melalui inverter pure sine, dengan panel surya 20 W di atas tutup sebagai pengisi tambahan. Lapisan pemantauannya: tiga probe DS18B20 (logika kendali pada median, alarm pada maksimum), sensor ambient DHT22, tekanan udara BMP390 (sekaligus log ketinggian), akselerometer, sensor tutup, GNSS, OLED + tiga LED + buzzer yang bekerja sepenuhnya lokal, dan log suhu **berantai hash bertanda tangan** yang disinkronkan lewat LTE-M/NB-IoT saat jaringan ada (store-and-forward ≥ 72 jam [benchmark]). Aturan tata kelola ditegakkan otomatis: ekskursi kumulatif melebihi 15 menit [benchmark] melatch kotak ke status **QUARANTINE** sampai dirilis QA. Pembeda utama dari kotak dingin standar adalah **bukti**: petugas tidak hanya berharap vaksin aman, tetapi dapat menunjukkan catatan suhunya yang tahan manipulasi.

**Bukti.** Perhitungan desain [estimate]: kebocoran panas 9–10 W pada ambient 40–42 °C berkat VIP, sehingga **7,04 kg PCM** (kapasitas 1.549 kJ) menutup anggaran 24 jam 1,16 MJ dengan margin 34%. Kompresor membekukan ulang PCM dalam ± 2,1 jam. Anggaran energi harian ≈ 810 Wh ditutup pengisian titik stasioner; panel on-board hanya cukup untuk elektronik (65 Wh/hari) — bukan untuk pendinginan. Logika kendali, alarm, anggaran PCM, rantai hash, dan alur karantina **diverifikasi end-to-end pada simulasi Wokwi** (ESP32 + MQTT + dashboard web, 8 skenario uji lulus), sebelum prototipe fisik dibangun.

**Kesimpulan.** Kombinasi PCM, kendali histeresis, log rantai hash, dan daya hibrida adalah pendekatan yang layak dan jujur terhadap batas fisika. Batas terbesarnya adalah **bobot (≈ 48 kg kosong, ≈ 63 kg termuat — angkat dua orang + trolley)** dan ketergantungan pada titik pengisian stasioner. Langkah berikutnya: uji *cold life* 24 jam di ruang 42 °C dengan sensor referensi terkalibrasi, lalu pilot lapangan.

---

## 1. Pendahuluan

Rantai dingin ibarat rantai sungguhan: kekuatannya ditentukan mata rantai terlemah. Di kota, mata rantai itu berupa lemari pendingin dengan listrik andal. Di pulau terpencil, mata rantai terlemahnya adalah kilometer terakhir: perjalanan dengan motor, perahu kecil, dan jalan kaki, di bawah matahari tropis, tanpa listrik yang pasti dan tanpa sinyal. Pada segmen inilah suhu paling mudah menyimpang dan paling sulit dipantau.

Lingkup esai ini adalah vaksin imunisasi rutin yang disimpan pada 2–8 °C, bukan vaksin yang membutuhkan suhu ultra-dingin atau beku. Kami memilih campak dan HPV sebagai dua contoh karena keduanya menunjukkan dua wajah risiko yang berbeda. Vaksin campak-rubela (MR) berbentuk kering beku dan peka terhadap panas serta cahaya, sehingga lonjakan suhu di perjalanan adalah ancaman utamanya. Vaksin HPV peka terhadap pembekuan, sehingga suhu yang terlalu dingin di dekat bahan pendingin juga berbahaya. Desain yang aman bagi keduanya harus menjaga suhu di tengah rentang, bukan di tepinya.

Taruhannya besar. Menurut data Kementerian Kesehatan, sepanjang 2025 tercatat 63.769 kasus suspek campak, 11.094 kasus terkonfirmasi laboratorium, dan 69 kematian, dengan kasus suspek naik 147 persen dibanding 2024. Laporan media atas data Kemenkes menyebut cakupan campak-rubela dosis pertama turun dari 92 persen pada 2024 menjadi 82 persen pada 2025. Wabah paling parah muncul di "kantong" berimunisasi rendah: di Kabupaten Sumenep, Jawa Timur, 16 dari 17 anak yang meninggal terkonfirmasi tidak pernah diimunisasi. Untuk HPV, WHO mencatat sekitar 36.000 kasus baru kanker serviks dan 21.000 kematian per tahun di Indonesia, dengan sekitar 99 persen kasus berkaitan dengan infeksi HPV dan sekitar 70 persen terdiagnosis pada stadium lanjut. Pemerintah menargetkan 90 persen anak perempuan usia 15 tahun mendapat imunisasi HPV hingga 2027.

Di sinilah kerusakan akibat suhu berbahaya karena tidak terlihat. Vaksin yang terpapar panas atau beku tidak berubah warna dan tidak berbau. Anak menerima suntikan dan merasa terlindungi, padahal perlindungannya mungkin berkurang. Yang menanggungnya adalah anak itu, keluarganya, dan komunitas pulau yang kecil — beberapa anak rentan saja sudah cukup untuk memicu wabah. Sebagian sumber menunjuk keraguan masyarakat dan cakupan rendah, bukan rantai dingin, sebagai pemicu utama kejadian luar biasa. Argumen kami lebih sempit: **rantai dingin yang gagal memperburuk celah yang sudah ada, dan bukti suhu membantu membangun kepercayaan.**

Pertanyaan utama esai ini: **bagaimana menjaga vaksin tetap pada 2–8 °C selama 24 jam hingga pulau terpencil tanpa bergantung pada listrik dan internet, sekaligus memberi petugas bukti yang dapat diverifikasi?** Tesis kami: **PCM menanggung beban termal, kompresor stasioner menanggung pengisian ulang, surya kecil menanggung data, dan bukti menanggung kepercayaan.**

## 2. Analisis Masalah dan Persyaratan

**Akar penyebab.** Penyimpangan suhu selama perjalanan berasal dari beberapa sumber. Paparan udara luar setiap kali kotak dibuka langsung mengubah suhu di dalam. Panas lingkungan pada siang hari menembus dinding, sementara guncangan dan perjalanan yang tertunda memperpanjang waktu paparan. Pemadaman listrik membuat pendingin berbasis listrik berhenti, dan sekaligus memutus pelacakan: tidak ada yang tahu di mana barang berada dan kapan sampai. Akibatnya, kerusakan sulit dilacak ke tahap mana pun.

**Pemangku kepentingan.** Pengguna utama adalah petugas medis yang mengantar dan memberikan vaksin. Mereka butuh kotak yang andal, mudah dioperasikan dengan sedikit pelatihan, dan memberi tanda yang jelas tanpa perlu membaca angka. Pihak lain yang terdampak: puskesmas sebagai titik pengisian dan serah terima, dinas kesehatan yang membutuhkan data audit, pengirim yang memantau rute dari jarak jauh, serta orang tua dan anak sebagai penerima akhir.

**Kendala nyata.** Listrik tidak andal, ketiadaan sinyal, anggaran terbatas, pelatihan minim, dan lingkungan pesisir yang korosif oleh garam. Dari sisi fisik, kotak ini **berat** (≈ 48 kg kosong) dan cukup besar (49 × 35 × 74 cm), sehingga ergonomi bagi petugas yang membawa dengan motor atau perahu kecil menjadi persoalan serius. Kami menjadikan ini kendala desain, bukan hal yang disembunyikan: pengangkatan dua orang, tali pengikat baku, dan trolley menjadi bagian dari SOP, bukan aksesori.

**Kriteria keberhasilan.** Suhu: rentang kerja kendali 5–7 °C (histeresis, terverifikasi [sim]) di dalam batas aman 2–8 °C [benchmark], sehingga ada ruang untuk akurasi sensor dan keterlambatan respons. Peringatan: LED dan buzzer bekerja ≤ 30 detik lokal [estimate]; telemetri terkirim ≤ 2 menit saat tersambung. Tata kelola: ekskursi kumulatif > 15 menit di atas 8 °C [benchmark] otomatis melatch **QUARANTINE** sampai dirilis QA — kotak tidak boleh "lupa" peristiwa bahaya. Ketahanan: 24 jam pasif pada 42 °C [estimate, profil uji dinyatakan]. Data: catatan tidak dapat dipalsukan diam-diam (rantai hash + tanda tangan). Biaya: per unit ≈ Rp 23,7 juta dengan kontingensi (§5.2).

**Data dasar kerusakan.** Angka kerusakan 25 persen yang kerap dipakai dalam diskusi adalah hipotetis, bukan temuan. Untuk menggantinya dengan data nyata, tahap pilot akan memasang pencatat suhu pada pengiriman rute yang ada selama beberapa minggu, lalu menghitung berapa persen perjalanan yang keluar dari 2–8 °C dan berapa lama. Angka itulah yang menjadi data dasar penilaian manfaat kotak.

**Di luar lingkup.** Vaksin beku atau ultra-dingin (beberapa vaksin mRNA, penyimpanan ≤ −15 °C) tidak tercakup karena membutuhkan teknologi pendinginan yang berbeda.

## 3. Solusi yang Diusulkan dan Metodologi

### 3.1 Arsitektur keseluruhan

Kotak terdiri dari dua tier bertumpuk dan lima lapisan fungsi:

1. **Dinding berisolasi VIP 25 mm** (kulit HDPE 2 mm + VIP 25 mm + liner PP food-grade 2 mm), dimensi luar cold box 458 × 334 × 383 mm;
2. **PCM 7,04 kg** sebagai penahan panas (dua dinding panjang + lantai, 13 mm) dengan evaporator pelat aluminium di bawahnya;
3. **Paket tenaga**: baterai LiFePO₄ 12,8 V 100 Ah (1.280 Wh), inverter pure sine 1.000 W untuk kompresor AC, MPPT ganda, panel surya 20 W yang direkat permanen di atas tutup di bawah cover pelindung, port 12 V, dan charger grid di titik stasioner;
4. **Rangkaian sensor dan antarmuka**: 3 × DS18B20, DHT22, BMP390, MPU-6050, reed switch tutup, GNSS + RTC, OLED 128×64, tiga LED, buzzer, panel kontrol di muka depan;
5. **Modul data**: ESP32 + LTE-M/NB-IoT (SIM7080), log rantai hash, buffer 72 jam [benchmark], dasbor pemantauan.

Di bawah cold box ada **machine tier** (490 × 350 × 332 mm) yang menampung kompresor, kondensor, baterai, inverter, MPPT, dan panel sekring — dipisahkan separator PUR 15 mm + aluminium. Total perakitan 490 × 350 × 742 mm, ≈ 48 kg kosong. Kompresor dipilih tipe **AC 220–240 V (GQR30TG, 245 W kapasitas pendinginan, motor 1/10 HP RSIR)** yang dijalankan lewat inverter: murah, tersedia, dan mudah diservis di daerah target; rugi konversi ± 10% sudah dihitung dalam anggaran energi.

### 3.2 Mengapa pasif sebagai tulang punggung, aktif sebagai penopang

Pendingin aktif membutuhkan listrik yang tidak dapat dijamin di lapangan. PCM menahan suhu karena menyerap panas saat berubah fasa pada suhu tetap, sehingga tidak bergantung pada daya. Bila listrik dan baterai habis, PCM tetap bekerja — itulah mengapa elektronik dan kompresor dirancang sebagai **lapisan pengawas dan pemulih**, bukan penentu hidup-matinya vaksin. Kompresor bekerja paling berat di titik stasioner (membekukan ulang PCM, ± 2,1 jam) dan hanya bersele ± 5% waktu saat transit untuk mengganti kebocoran panas.

| Aspek | Peltier (trim) | Kompresi uap (GQR30TG via inverter) | PCM pasif |
|---|---|---|---|
| COP pada kondisi beku | 0,3–0,6 | ≈ 1,5 [estimate, datasheet [verify]] | tidak berlaku |
| Daya listrik | 20 W (trim) | ≈ 145 W [estimate; skenario 130–180 W] | 0 W |
| Peran | cadangan DC bila inverter/kompresor gagal (≈ 31 jam) | pembekuan ulang + pemeliharaan | **penanggung utama 24 jam** |
| Getaran/bising | rendah | ada (dudukan karet) | tidak ada |
| Ketergantungan daya | DC langsung | AC via inverter | nol |

Kami tidak mengklaim salah satu selalu unggul: untuk 24 jam tanpa listrik andal, pasif lebih tepat; kompresor masuk akal di titik stasioner dan sebagai pemelihara; TEC 20 W adalah jaring pengaman terakhir.

### 3.3 Dimensi dan volume

Payload **tetap 30,0 L [benchmark]** (400 × 250 × 300 mm; tiga tray ≤ 90 mm). Seluruh lapisan dinding dibangun mengelilinginya: PCM 13 mm → liner 2 mm → VIP 25 mm → HDPE 2 mm, ditambah evaporator 12 mm di lantai. Tutup 415 × 285 mm berengsel belakang, membuka ~120°, gasket double-lip, hasp segel tamper; di atasnya panel surya 20 W dan cover pelindung yang ikut berayun dengan tutup — tanpa bongkar pasang. Untuk operasi pegunungan (sampai 3.000 m) dinding dilengkapi **katup penyama tekanan** sehingga latch tidak menanggung beban ΔP (± 2,1 kN bila tanpa katup).

### 3.4 Titik leleh PCM dan perlindungan dari pembekuan

Titik leleh PCM 5–6 °C — di atas 2 °C sehingga sekitarnya tidak membekukan vaksin, di bawah 8 °C sehingga masih menyimpan dingin. PCM ditempatkan di dinding dan lantai, tidak menempel langsung pada vaksin; boss jarak 10 mm membentuk saluran udara, dan kipas sirkulasi 80 mm meratakan suhu. Probe ditempatkan **dalam botol buffer** berisi air/glikol yang meniru massa termal vial, sehingga pembacaan mendekati suhu vaksin sebenarnya, bukan sekadar suhu udara. Evaporator menjaga pelat pada −6 sampai −8 °C saat membekukan PCM, tetapi lapisan PCM 5–6 °C adalah perisai antara pelat dingin dan vaksin.

### 3.5 Sensor, alarm lokal, dan logika kendali (sesuai firmware Wokwi)

Sensor DS18B20 tahan air; prototipe simulasi memakai **dua probe** (atas, bawah), desain penuh **tiga probe** sesuai rencana pemetaan suhu — kendali pada **median**, alarm pada **maksimum**. DHT22 mengukur ambient (di simulasi: drag slider 38–42 °C), BMP390 mencatat tekanan/ketinggian, reed switch memantau tutup, MPU-6050 mendeteksi getaran. Alarm bekerja sepenuhnya lokal: **LED hijau** aman, **kuning** baterai lemah (< 11,0 V; < 10,5 V kompresor dilepas), **merah** suhu keluar rentang, buzzer mengikuti kondisi merah. OLED menampilkan status dalam empat baris tanpa perlu ponsel.

Logika kendali pada firmware (dan simulasi Wokwi) adalah inti yang berpindah utuh ke perangkat nyata:

- **Histeresis kompresor**: menyala saat suhu ≥ 7 °C, mati saat ≤ 5 °C [sim] — di 6 °C kompresor tetap bekerja, persis seperti termostat sungguhan;
- **Anggaran PCM**: SoC PCM menurun sesuai ΔT ambient; holdover tersisa ditampilkan dalam jam [sim], kapenuhan penuh = 24 jam cerita pada ΔT 35 K [benchmark];
- **Hilang daya** (saklar utama): status **PASSIVE-HOLD**, kompresor dipaksa mati, PCM mengambil alih [sim];
- **Ekskursi kumulatif 15 menit** [benchmark]: deteksi ≤ 30 detik, alarm seketika; pada 15 menit cerita status melatch **QUARANTINE** sampai restart [sim] — keselamatan dengan desain, bukan pengaturan yang bisa dilupakan petugas;
- **Serah terima**: tombol khusus mencatat event dan mencetak **struk rantai hash** untuk dibandingkan penerima [sim].

### 3.6 Waktu, data, dan keamanan

Catatan tanpa waktu yang andal tidak dapat dipercaya: RTC DS3231 (± 2 ppm) disinkronkan dari PPS GNSS; setiap record membawa flag sumber waktu (GNSS/RTC/unsynced); gap posisi dicatat sebagai **GPS OUTAGE** dan tidak pernah diinterpolasi. Sampling 30 detik [benchmark] menghasilkan ± 2.880 pembacaan/hari/sensor — puluhan kilobita per minggu, sehingga buffer lokal 72 jam [benchmark] murah. Setiap catatan dihubungkan hash catatan sebelumnya (FNV-1a pada simulasi; Ed25519 bertanda tangan pada perangkat nyata): mengubah satu catatan memutus seluruh rantai setelahnya — terverifikasi pada skenario uji tamper [sim]. Pola **store-and-forward**: log tersimpan lokal, disinkronkan ke dinas kesehatan lewat LTE-M/NB-IoT saat jaringan ada. Tidak ada data pengenal pasien; posisi ditrunkasi 4 desimal (≈ 11 m) untuk peran non-QA.

### 3.7 Pemantauan jarak jauh dan dasbor pengirim

Telemetri lewat MQTT: `state` (suhu, status, baterai, PCM, ekskursi, hash, GNSS), `event`, `settings`, `status`, dan `cmd`. Dasbor web menampilkan grafik suhu melawan batas 2–8 °C, badge status, cadangan PCM, log peristiwa, rantai hash, dan peta rute (track Simongan Semarang → Kudus pada simulasi). Dasbor dipagukan **akses khusus pengirim** (kode akses + sesi), karena broker publik demo dapat dibaca siapa saja; deployment nyata memakai broker terautentikasi over TLS dengan kunci per-perangkat. Perintah jarak jauh (mode kompresor, setpoint, bisukan alarm) **dicatat di rantai hash sebagai REMOTE CMD** — kendali jarak jauh sepenuhnya dapat diaudit [sim].

### 3.8 Pengisian ulang

PCM harus dibekukan terlebih dahulu: titik stasioner (puskesmas) dengan charger grid 14,6 V / 20 A membekukan PCM ± 2,1 jam dan mengisi baterai; kompresor dapat dijalankan langsung dari grid lewat transfer switch tanpa melewati baterai. Dua set PCM dirotasi. Panel surya 20 W di tutup hanya pengisi tambahan (± 65 Wh/hari) — cukup untuk menopang telemetri, tidak pernah cukup untuk pendinginan; opsi PV lipat 200 W deployable tersedia untuk station tanpa grid.

### 3.9 Alur kerja petugas

Petugas menerima kotak yang sudah diisi (PCM dingin, baterai penuh, segel utuh), memuat vaksin, menekan tombol serah terima. Selama perjalanan ia cukup membaca warna lampu; pengirim memantau peta dan suhu dari dasbor. Di tujuan, penerima memverifikasi struk hash, membuka segel, dan halaman status menampilkan suhu puncak serta durasi di luar rentang. Bila kotak melatch QUARANTINE, batch tidak boleh digunakan sebelum keputusan QA sesuai label produk dan pedoman WHO/nasional. **Sistem menyajikan bukti; keputusan kelayakan tetap pada manusia dan pedoman.**

### 3.10 Verifikasi logika melalui simulasi Wokwi

Sebelum prototipe fisik, seluruh logika kendali dijalankan pada simulasi Wokwi (ESP32, 2 × DS18B20, DHT22, OLED, buzzer, 3 LED, 3 tombol, saklar daya, potensiometer baterai) yang terhubung ke broker MQTT publik dan dasbor web. Delapan skenario uji, semuanya lulus:

| # | Skenario | Kriteria lulus | Status |
|---|---|---|---|
| S1 | Operasi normal | OLED OK, PCM 100%, rantai hash bertambah, tanpa alarm | Lulus [sim] |
| S2 | Histeresis | Kompresor nyala di ≥ 7 °C, mati baru di ≤ 5 °C | Lulus [sim] |
| S3 | Hilang daya → holdover | PASSIVE-HOLD, PCM terkuras sesuai ΔT, kompresor terkunci mati | Lulus [sim] |
| S4 | Tutup terbuka | Event DOOR OPEN + note, drain PCM ×1,3 selama terbuka | Lulus [sim] |
| S5 | Ekskursi → karantina | 15 menit cerita di atas 8 °C → latch QUARANTINE + catatan QA | Lulus [sim] |
| S6 | Baterai lemah | < 11,0 V kuning; < 10,5 V kompresor dilepas, prioritas ke log | Lulus [sim] |
| S7 | Serah terima | Struk rantai hash tercetak untuk penerima | Lulus [sim] |
| S8 | Uji tamper | Sunting satu catatan lama memutus seluruh rantai setelahnya | Lulus [sim] |

Firmware simulasi dan perangkat nyata memakai struktur kendali yang sama (histeresis, anggaran PCM, latch karantina, rantai hash, store-and-forward); yang berubah hanyalah perifernya (3 probe, LTE-M, GNSS sungguhan).

### 3.11 Metode analisis

Tiga pendekatan: perhitungan termal (beban panas dan massa PCM), anggaran energi (kebutuhan versus produksi/pengisian), dan rencana uji laboratorium dengan sensor referensi terkalibrasi memakai bahan simulan — bukan vaksin sungguhan — didahului verifikasi logika pada simulasi Wokwi di atas.

## 4. Analisis dan Diskusi

### 4.1 Beban panas dan massa PCM

Asumsi [estimate]: cold box 458 × 334 × 383 mm; dinding VIP 25 mm dengan k aged 0,0075 W/m·K (R = 3,33 m²·K/W); luas rata-rata dinding 0,77 m²; ambient desain 40 °C (42 °C untuk uji), target 5 °C.

```
Q = ΔT × A / R = 35 × 0,77 / 3,33 = 8,1 W  → +15% thermal bridge = 9 W
(42 °C: ΔT 37 K → ≈ 10 W)
```

Anggaran 24 jam pasif: konduksi 778 kJ + pembukaan tutup 4 × 30 kJ + kipas/sensor 86 kJ + solar gain kulit gelap 173 kJ = **≈ 1,16 MJ**. Dengan kalor laten PCM 220 kJ/kg: kebutuhan teoretis 5,3 kg; plat yang dipasang **7,04 kg = 1.549 kJ → margin 34%** untuk penuaan PCM, hari 42 °C, pembukaan ekstra, dan operator yang kurang disiplin. VIP 25 mm inilah yang memangkas PCM dari 11–12 kg (versi PUR 5 cm, beban 19 W) menjadi 7,04 kg sekaligus menjaga janji 24 jam [benchmark]. Klaim holdover adalah **estimasi yang hanya berlaku pada profil uji yang dinyatakan** — 38–42 °C, muatan didinginkan ke 4 °C, ≤ 4 pembukaan tutup — dan belum jaminan sampai diukur.

### 4.2 Bobot dan klaim "mudah dibawa"

Dengan baterai 100 Ah (10,5 kg), kompresor (8 kg [verify]), PCM 7 kg, dan shell, bobot kosong **≈ 48 kg; termuat ≈ 63 kg**. Itu tidak seringan kotak pengantar makanan, dan kami tidak akan mengklaimnya demikian. Kami mendefinisikan ulang "portabel" secara jujur: **angkat dua orang, trolley wajib, empat tie-down eye M6 untuk pengikatan di motor/perahu**; pusat gravitasi rendah karena baterai di lantai. Versi 18–20 kg draf awal ditinggalkan karena menuntut kompromi yang tidak jujur (PCM kurang atau tanpa pemulihan aktif). Bila anggaran sangat terbatas, varian "hemat" (PUR 40 mm, kompresor DC, baterai 50 Ah, ≈ Rp 14 juta) tersedia sebagai fallback dengan geometri berbeda.

### 4.3 Energi dan otonomi

| Beban | Daya | Catatan |
|---|---|---|
| Elektronik, sensor, GNSS, LTE, OLED | 5 W | jalur 5 V |
| Kipas sirkulasi + 2 kipas kondensor | ≈ 6 W | jalur 12 V |
| Kompresor via inverter | 161 W sisi-DC saat menyala | 145 W ÷ η inverter 0,90 |
| Standby inverter (eco) | 2 W | [verify] |

**Hari operasi normal ≈ 810 Wh** (recharge PCM 2,1 jam = 338 Wh + transit duty 5% = 177 Wh + standby 44 Wh + DC 264 Wh); hari ekstrem 42 °C ≈ 900 Wh. Otonomi dari 1.024 Wh (80% DoD): **94 jam** pasif + telemetri saja; **≈ 30 jam** operasi aktif; **31 jam** dengan TEC saja bila inverter gagal. Panel on-board 20 W menyumbang ± 65 Wh/hari — cukup untuk menopang telemetri (memperpanjang otonomi pasif menjadi ± 5 hari), **tidak pernah cukup untuk pendinginan**; pengisian besar adalah tugas titik stasioner. Untuk mendung beruntun, baterai menjembatani ± 3,8 hari tanpa matahari.

### 4.4 Skenario terburuk

Tutup terbuka terlalu lama: reed switch + laju suhu memicu merah dan buzzer, durasi dicatat, drain PCM ×1,3 [sim]. Satu sensor gagal: voting antar-probe menandai kanal, kendali pindah ke median, batch ditandai "tidak terverifikasi". Perjalanan tertunda: PCM menahan ± 24 jam, dasbor menampilkan "sisa holdover" sebagai jam aman. Baterai kritis: kompresor dilepas otomatis, log dan alarm diprioritaskan [sim]. Ekskursi > 15 menit kumulatif: **QUARANTINE melatch sampai QA melepas** [sim]; bukti (kurva suhu, durasi, sensor, pintu, GPS) terekspor otomatis; bila bukti kurang, putusan default adalah **jangan dipakai**.

### 4.5 Operasi dataran tinggi (tekanan rendah)

Amplop desain sampai 3.000 m. Dua risikonya sudah dijawab: (1) **tekanan** — katup penyama tekanan menetralkan ΔP ± 18 kPa yang seharusnya membebani latch; (2) **udara tipis** — kapasitas pendinginan turun 10–20% pada 2.000 m (aturan praktis 5–10% per 1.000 m), tetapi ambient yang lebih dingin membuat suhu kondensasi tetap ≈ 34 °C — lebih baik daripada 50 °C di pantai. BMP390 mencatat ketinggian di setiap catatan dan memicu event **ALTITUDE HIGH** di atas ambang; rating ketinggian kompresor menjadi item datasheet yang wajib [verify].

### 4.6 Validasi

Rencana uji: uji *cold life* 24 jam di ruang 42 °C dengan sensor referensi terkalibrasi (ISO/IEC 17025), pemetaan suhu multi-titik muatan, uji latensi alarm, uji jatuh dan getar (profil shaker + 200 km jalan campur), uji air dan korosi garam (target IPX4 tegak), uji start RSIR pada inverter, uji distribusi suhu saat recharge PCM, serta uji telemetri store-and-forward. Sebelum semua itu, verifikasi logika sudah dilakukan pada simulasi Wokwi (§3.10).

### 4.7 Estimasi versus terukur

Semua angka di bagian ini adalah **estimasi desain** atau **hasil simulasi [sim]**. Yang akan diukur: massa PCM efektif, durasi ketahanan, bobot akhir, konsumsi energi nyata, akurasi sensor pasca kalibrasi, dan distribusi akurasi GNSS (target 2,5 m CEP [benchmark]; diperkirakan 3–6 m pada antena dinding belakang).

### 4.8 Risiko dan keterbatasan

Risiko terbesar: **bobot**, ketergantungan titik pengisian, kegagalan inverter menutup start RSIR (LRA wajib diverifikasi), penuaan VIP, dan kesalahan prosedur. Mitigasi: trolley + SOP angkat, transfer switch grid, TEC 20 W sebagai cadangan DC, corner guard + monitoring duty-cycle kompresor (kenaikan duty = indikasi VIP bocor), serta pelatihan singkat berbasis warna lampu. Kriptografi menjamin catatan tidak diubah setelah ditulis — **bukan** bahwa sensor akurat; kalibrasi dan segel fisik tetap wajib.

### 4.9 Perlukah blockchain?

Tidak untuk kebanyakan kasus. Log berantai hash dengan tanda tangan perangkat sudah cukup mendeteksi manipulasi; pada simulasi, menyunting satu catatan lama memutus seluruh rantai setelahnya [sim]. Blockchain baru relevan bila audit melibatkan banyak pihak yang saling tidak percaya — dan bahkan itu tidak bisa membuktikan sensor akurat atau petugas jujur.

### 4.10 Pembeda dari pembawa vaksin standar WHO PQS

Pembawa standar menjaga suhu dengan kemasan dingin dan isolasi, tetapi umumnya tidak menyediakan catatan terverifikasi, alarm lokal, telemetri rute, maupun latch karantina otomatis. Pembeda kami: **PCM yang dirancang untuk 24 jam + log offline tahan manipulasi + kendali yang menegakkan aturan sendiri + tenaga hibrida berbiaya rendah.**

## 5. Dampak dan Implementasi

### 5.1 Sosial dan kesehatan

Satu kotak 30 liter membawa vaksin untuk banyak anak sekaligus, termasuk kegiatan imunisasi sekolah. Setiap perjalanan yang aman berarti kelompok anak yang benar-benar terlindungi; bukti suhu membantu petugas menjawab keraguan orang tua. Dosis per kotak bergantung jenis vaksin dan kemasan — angka pastinya ditentukan saat pilot.

### 5.2 Ekonomi

BOM harga terendah **Rp 18,1 juta**; siap pakai (perakitan, brazing, kalibrasi, uji) **≈ Rp 20,6 juta (USD 1.145)**; anggaran esai dengan kontingensi 15% **≈ Rp 23,7 juta**. Biaya siklus hidup: OPEX ± Rp 1,1 juta/tahun (listrik stasioner ± Rp 36 rb/bulan, kuota data, kalibrasi, servis) → **TCO 5 tahun ≈ Rp 26,2 juta (± Rp 435 rb/bulan)**, belum termasuk penggantian baterai di tahun ke-6 (+Rp 2,6 juta). Angka ini dibagi jumlah perjalanan selama masa pakai, lalu dibandingkan dengan nilai satu pengiriman vaksin yang rusak (jutaan hingga puluhan juta rupiah per kejadian) — itulah argumen ekonominya. Varian hemat (PUR, DC, 50 Ah) tersedia di ≈ Rp 14 juta bila anggaran menjadi kendala utama.

### 5.3 Lingkungan

Tanpa bahan bakar dan generator, jejak karbon operasional rendah; kompresor hanya berjalan 2,1 jam per siklus pengisian dan 5% selama transit. Baterai LiFePO₄ lebih aman dan awet (2.000+ siklus), PCM dipakai ulang berkali-kali, dan R600a/R134a dalam charge kecil (< 110 g) sesuai regulasi refrigeran. Rencana daur ulang baterai dan PCM menjadi bagian prosedur pemeliharaan.

### 5.4 Keselamatan

Risiko baterai dikendalikan BMS + MPPT + sekring bertingkat (40 A utama, 30 A inverter, RCD 30 mA pada sisi AC). Sisi 230 V terkurung di machine tier dengan pelat pemisah dan label peringatan; tidak ada kabel AC di ruang dingin. PCM salt hydrate dipilih yang tidak beracun dan tidak mudah terbakar. Risiko keputusan keliru dikurangi prinsip bahwa sistem hanya menyajikan bukti — keputusan pakai/buang mengikuti label produk dan pedoman WHO/nasional, dengan VVM diperiksa untuk vaksin yang memilikinya.

### 5.5 Implementasi

Pemeliharaan dan kalibrasi bersama dinas kesehatan: ice-point check bulanan, kalibrasi tahunan, penggantian silica gel tahunan, inspeksi VIP via tren duty-cycle. Pelatihan: ½ hari operator, 1 hari teknisi facility, 1 hari QA. Tahapan: pilot satu kabupaten kepulauan (data dasar kerusakan + uji prototipe) → evaluasi dan perbaikan → perluasan bertahap. Titik pengisian stasioner bertenaga surya/grid di puskesmas adalah prasyarat, bukan pelengkap.

### 5.6 Bila anggaran dipotong 50 persen

Yang dipertahankan: VIP, PCM, sensor suhu, log rantai hash, alarm lokal, dan katup tekanan — inti perlindungan vaksin. Yang dikorbankan berurutan: GNSS dan seluler (kembali ke baca manual + struk lokal), akselerometer, BMP390, panel surya on-board, lalu OLED diganti stiker status.

## 6. Kesimpulan dan Rekomendasi

Jawaban atas pertanyaan utama adalah **ya**: vaksin 2–8 °C dapat dijaga ≥ 24 jam hingga pulau terpencil tanpa listrik andal dan tanpa internet, bila beban termal ditanggung PCM + VIP, pengisian ulang ditanggung kompresor di titik stasioner, elektronik hanya mengawasi dan membuktikan, dan aturan 15 menit ditegakkan otomatis oleh perangkat itu sendiri.

**Tiga temuan terpenting.** Pertama, VIP 25 mm memangkas beban panas dari 19 W menjadi 9–10 W, sehingga 7,04 kg PCM cukup dengan margin 34% — harga fizikalnya adalah bobot total ≈ 48 kg, dan kami memilih mengakuinya daripada mengurangi perlindungan. Kedua, panel di atas kotak hanya cukup untuk elektronik (65 Wh/hari); pengisian besar adalah tugas titik stasioner, dan kompresor AC murah via inverter adalah jalan paling realistis untuk membekukan ulang PCM (± 2,1 jam). Ketiga, nilai terbesar sistem ini bukan pada pendinginnya, melainkan pada **bukti suhu yang tahan manipulasi, alarm lokal yang bekerja tanpa jaringan, dan latch karantina yang menegakkan aturan 15 menit secara otomatis** — semuanya telah diverifikasi berjalan pada simulasi Wokwi sebelum satu pun komponen fisik dibeli.

**Langkah berikutnya.** Membangun prototipe, menjalankan uji 24 jam pada 42 °C dengan sensor referensi terkalibrasi, memverifikasi LRA kompresor terhadap surge inverter (datasheet GQR30TG), lalu pilot lapangan untuk memperoleh data dasar kerusakan yang nyata. Pemerintah dan mitra dapat membantu dengan titik pengisian stasioner di puskesmas, integrasi log ke sistem pelaporan imunisasi, serta dukungan kalibrasi dan pelatihan.

Di pulau yang listriknya padam dan sinyalnya hilang, vaksin tidak boleh menunggu, dan petugas tidak boleh menebak. Kotak ini dirancang agar bekerja justru saat segalanya tidak ada — dan memberi petugas **bukti, bukan sekadar harapan**, bahwa vaksin yang ia suntikkan masih aman.

## Referensi

1. Kementerian Kesehatan RI. *Kemenkes Waspadai Dinamika Campak Nasional dan Global*. kemkes.go.id.
2. WHO Indonesia. *Sumenep Successfully Ended Measles Outbreak*. 9 Februari 2026. who.int/indonesia.
3. detikJateng. *Sumenep KLB Campak, 17 Meninggal, Mayoritas Belum Pernah Imunisasi*. 26 Agustus 2025.
4. Media Indonesia / Metro TV. *KLB Campak, IDAI: Imunisasi Harus Diperkuat*. 27 Agustus 2025.
5. Popmama. *Kasus Campak di Indonesia Tertinggi Kedua di Dunia*. (rangkuman media atas data Kemenkes; verifikasi ke sumber primer sebelum dikutip).
6. WHO Indonesia & UNFPA. *WHO, UNFPA Commend Indonesia's Efforts to Eliminate Cervical Cancer*. 15 November 2024. who.int/indonesia.
7. Kementerian Kesehatan RI. *Sehat Negeriku* — bahan imunisasi HPV dan kanker serviks. sehatnegeriku.kemkes.go.id.
8. WHO. *Immunization in practice* & PQS catalogue (E004/E03 cold-chain equipment). who.int.
9. GS1. *EPCIS 2.0 Standard* — event chain untuk serah terima. gs1.org.
10. IEC 60664-1. *Insulation coordination for equipment within low-voltage systems* — derating ketinggian.
11. Schneider Electric. *Altitude derating FAQ* — panduan derating peralatan listrik di atas 2.000 m. se.com.
12. Wikipedia. *Atmospheric pressure* — kurva barometrik (−1,2 kPa per 100 m; kasus botol tersegel 4.300 m). Diakses 2026.
13. Embraco/Nidec. *High Altitude Effects on Refrigeration Systems* — buletin teknis (diminta bersama datasheet GQR30TG).
14. Dokumen proyek internal: `detail.md`, `dimension.md`, `price.md` — perhitungan, dimensi, dan anggaran; `wokwi/sketch.ino` + `wokwi/dashboard.html` — verifikasi logika kendali (skenario S1–S8).

*Catatan integritas akademik: seluruh angka teknis diberi label [benchmark]/[estimate]/[sim]/[verify]; angka simulasi Wokwi adalah verifikasi logika, bukan hasil ukur perangkat fisik. Penggunaan alat bantu AI diungkapkan sesuai aturan penyelenggara.*
