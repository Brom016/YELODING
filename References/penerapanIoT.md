


Diterima: 26-12-2024 | Revisi: 13-01-2025 | Diterbitkan: 31-03-2025 | doi: 10.35134/komtekinfo.v12i1.589
## 1



Jurnal KomtekInfo
https://jkomtekinfo.org/ojs
2025   Vol. 12 N o .   1
## Hal:  1-11
e-ISSN: 2502-8758

Penerapan IoT pada Alat Temperature Monitoring System Cold Chain
Box Vaccine Menggunakan Sensor DS18B20
## Akmal Darman Putra
## 
## , Sarjon Defit, Gunadi Widi Nurcahyo
Fakultas Ilmu Komputer, Universitas Putra Indonesia YPTK, Padang, 25221, Indonesia
akmaldaput@gmail.com
## Abstract
Unit Pelaksana Teknis (UPTD) Farmasi Dinas Kesehatan Kabupaten Siak  Office Pharmacy is fully responsible for maintaining
the quality of the vaccine until the vaccine is distributed, the process of storing vaccines in the cold chain box has a problem,
namely, it is not equipped with a real-time temperature monitoring device that can provide a warning to pharmacists if the cold
chain box temperature rises due to internal or external damage. In addition to the problems mentioned, there is another problem,
namely the temperature recording process is still done manually every 2 hours on the log sheet by pharmacists. Based on this,
the purpose of this study is to develop technological innovation in the pharmaceutical field, namely by creating an IoT-based
temperature  monitoring  tool  that  is  integrated  with  the  Telegram  application  and  the  Blynk  IoT  application.  The  research
methods  used in  this  study  are  the  waterfall  method,  experiments,  and  UML  modeling.  The  process  of  running  this  system
begins when the sensor is inserted into the cold chain box then the sensor will send temperature data to the Blynk IoT application
to  be  displayed  in  real-time.  The  performance  of  this  technology  works  with  the  provision  that  if  the  temperature  does  not
comply with the provisions, a warning will appear on the Blynk IoT and Telegram applications, the temperature data is then
saved  and  will  be  used  as  a  basis  for  making  a  report  by  the  pharmacist.  This  research  produces  a  temperature  monitoring
device using a DS18B20 temperature sensor and an ESP8266 microcontroller with an accuracy rate of more than 95% and this
system  can  also  provide  real-time  temperature  data  information  and  warnings  via  telegram.  This  research  is  expected  to
contribute to the pharmaceutical field as well as the benefits and convenience for pharmacists in monitoring temperature and
recording temperature data..
Keywords:  Vaksin, Cold Chain Box, Internet of Things, Sensor Suhu DS18B20
## Abstrak
Unit Pelaksana Teknis Dinas (UPTD) Farmasi Dinas Kesehatan Kabupaten Siak bertanggung jawab penuh menjaga kualitas
vaksin  hingga  vaksin  didistribusikan, proses  penyimpanan vaksin pada cold  chain box memiliki  permasalahan  yaitu tidak
dilengkapi alat pemantauan suhu secara realtime yang bisa memberikan peringatan kepada apoteker jika terjadi kondisi suhu
cold  chain  box naik  yang  disebabkan  oleh  kerusakan  internal  maupun  kerusakan  eksternal.  Selain  masalah  yang  telah
disebutkan terdapat masalah lain yaitu proses pencatatan suhu masih dikerjakan secara manual setiap 2 jam sekali pada log
sheet oleh apoteker. Berdasarkan hal tersebut maka tujuan penelitian ini adalah untuk mengembangkan inovasi teknologi dalam
bidang kefarmasian yaitu dengan menciptakan alat pemantauan suhu berbasis IoT yang terintegrasi dengan aplikasi telegram
dan aplikasi Blynk IoT. Metode  penelitian  yang  digunakan  pada penelitian ini yaitu  metode  waterfall, eksperimen, dan
pemodelan UML.  Proses berjalannya sistem ini dimulai ketika sensor dimasukan ke dalam cold chain box kemudian sensor
akan mengirimkan data  suhu  ke  aplikasi  Blynk  IoT  untuk ditampilkan secara realtime. Kinerja  teknologi  tersebut  bekerja
dengan ketentuan jika terjadi suhu tidak sesuai ketentuan muncul peringatan pada aplikasi Blynk IoT dan Telegram, data suhu
kemudian  disimpan  dan  akan  dijadikan  sebagai  dasar  dalam  membuat  laporan  oleh  apoteker. Penelitian  ini  menghasilkan
sebuah alat pemantauan suhu menggunakan sensor suhu DS18B20 dan mikrokontroler ESP8266 dengan tingkat akurasi lebih
95% dan sistem ini juga dapat memberikan informasi data suhu secara realtime serta peringatan melalui Telegram. Penelitian
ini diharapkan memberikan kontribusi dalam bidang farmasi serta manfaat dan kemudahan bagi apoteker dalam pemantauan
suhu dan pencataan data suhu.
Keywords:  Vaksin, Cold Chain Box, Internet of Things, Sensor Suhu DS18B20
KomtekInfo is licensed under a Creative Commons Attribution-Share Alike 4.0 International License.

## 1. Pendahuluan
## Peraturan  Menteri  Kesehatan  Nomor  26  Tahun  2020
tentang   Standar   Pelayanan   Kefarmasian   dijelaskan
bahwa    pengelolaan    sediaan    farmasi    di    fasilitas
pelayanan kesehatan harus melalui sistem satu pintu dan
menjadi  tanggung  jawab  Apoteker  penanggungjawab
kefarmasian.   Apoteker   bertanggung   jawab   terhadap
sediaan  dan  menjamin  keamanan,  mutu  dan  khasiat
vaksin   mulai   dari   penerimaan,   penyimpanan   dan
distribusi  hingga  saat  digunakan.  Dalam  semua  proses
penyediaan vaksin hingga sampai ke fasilitas pelayanan
kesehatan,  hal  yang  paling  mendapat  perhatian  adalah
menjaga kualitas vaksin tetap sesuai standar hingga pada
saat   penggunaan.   Namun   dalam   praktiknya   sering
ditemukan    masalah    terkait    vaksin    seperti    vaksin

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 2


rusak/kedaluwarsa   atau   vaksin   palsu.   Ada   banyak
penyebab     yang     menimbulkan     masalah     tersebut
diantaranya  penyimpanan  vaksin  pada  suhu  yang  tidak
sesuai atau rantai distribusi vaksin yang tidak sesuai. [1].
Dinas  Kesehatan  Kabupaten  Siak  yang  beralamat  di
## Komp.   Perkantoran   Sei.   Betung   Kabupaten   Siak
memiliki Unit Pelaksana Teknis Dinas (UPTD) Farmasi
yang secara khusus bertanggung jawab menjaga kualitas
vaksin.  Menjaga  kualitas  vaksin  diperlukan  dukungan
dalam  melakukan  pengelolaan  vaksin  salah  satunya
yaitu  penyimpanan  yang  efektif  dan  efisien  sehingga
dapat mencegah terjadinya kerusakan vaksin.
Permasalahan yang muncul dari kerusakan vaksin yang
diakibatkan   oleh   penyimpanan   yang   tidak   sesuai
ketentuan  dapat terjadi  karena  penggunaan cold  chain
box sebagai  media  penyimpanan  dan  pendingin  vaksin
tidak  dilengkapi  alat  pemantauan  suhu  secara realtime
yang bisa memberikan peringatan kepada apoteker jika
terjadi  kondisi  dimana  suhu cold  chain  box naik  yang
disebabkan  oleh  kerusakan internal maupun  kerusakan
eksternal seperti apoteker lupa menutup rapat cold chain
box,  mati  lampu, freezer tidak  berfungsi,  masa  pakai
sudah  terlalu  lama,  peletakan vaksin  yang  tidak  teratur
dan   lain   sebagainya.   Selain   masalah   yang   sudah
dijelaskan  diatas  masih  terdapat  masalah  lain  yaitu
proses pencatatan suhu masih dikerjakan secara manual
setiap   2   jam   sekali   pada log   sheet oleh   apoteker
kemudian   melaporkannya   kepada   Dinas   Kesehatan
## Kabupaten.
Tujuan   dari   penelitian   ini   adalah   untuk   membantu
apoteker di UPTD  Farmasi Dinas Kesehatan Kab. Siak
dalam   beberapa   hal   diantaranya   memahami   konsep
penerapan Teknologi Internet Of Things (IoT) pada clod
chain box vaccine, memahami cara kerja
menghubungkan  antara Sensor  Suhu  DS18B20 Water
Proof dengan  mikrokontroler  NODEMCU  ESP8266,
memahami  cara  kerja  aplikasi  telegram  dan  aplikasi
blynk  dalam  memberikan  peringatan  kepada  apoteker,
memahami cara kerja aplikasi blynk dalam
menghasilkan   laporan   data   suhu   yang dibutuhkan
apoteker,  menganalisa  data  suhu  yang  diperoleh  dari
termometer    manual  dengan  data  suhu  yang  diperoleh
dari  alat pemantauan  suhu  berbasis Internet  Of  Things
(IoT).
Penelitian-penelitian   tentang teknologi Internet   Of
Things (IoT)    dan    mikrokontroler    sudah    pernah
dilakukan     sebelumnya. Penelitian     dengan     judul
“Rancang   Bangun   Sistem   Monitoring   Suhu   Cold
Storage Berbasis Internet Of Things (IoT) Menggunakan
Wemos  D1  R2  Di  PT.  Aerofood  Acs  Denpasar” yang
membahas tentang pencegahan terjadinya keruskan pada
bahan baku makanan yang disimpan di Cold Storage [2].
Penelitian    selanjutnya    yakni    perancangan    sisgtem
## Prototype  Monitoring Suhu  Berbasis Mikrokontroler
Pada Cool  Box Ikan  Menggunakan  Sensor  DS18B20
(Studi  Kasus  di  Batulicin  Simpang  Empat  Pelabuhan
## PPI) [3].
Permasalahan  yang  diangkat  dalam  penelitian  ini  yaitu
sering  kali  dalam  penyuplaian  ikan  kepada  konsumen
membutuhkan  jarak  dan  waktu  yang  relatif  panjang,
sedangkan  konsumen  selalu  mengharapkan  ikan  segar
[4]. Sistem  Monitoring  Suhu  dan  Kelembapan  Ruang
Server  Berbasis  Wemos  D1,  server  yang  beroperasi
secara  terus  menerus  pasti  akan  mengalami  kenaikan
suhu  yang  akan  menyebabkan  server  tersebut overheat
yang    menjadi    permasalahan    [5]. Prototipe Alat
Monitoring    Suhu    dan    Kelembaban    pada    Rumah
Penyimpan Tembakau Berbasis Internet of Thing (IoT)
yang  menggunakan  sensor  suhu  DHT22.  Pengukuran
suhu dan kelembaban dilakukan sebanyak 10 percobaan
dan   diulang   sebanyak   5   kali.   Presentase   akurasi
pengukuran suhu adalah 96,36% dengan
membandingkan sensor DHT22 dengan termometer [6].
Penelitian  dengan  judul Smart  Healthcare  Monitoring
System  Using Internet  of  Thing (IoT)  yang  membahas
tentang    bagaimana Internet    of    Things hari    ini
memainkan peran penting dalam pelacakan,
pendokumentasian,     penyimpanan,     presentasi     dan
komunikasi  di  bidang  perawatan  kesehatan.  Penelitian
ini    difokuskan    pada        pemantauan    suhu    tubuh
(DS18B20),  detak  jantung  dan  SPO2  (MAX30100).
Raspberry   Pi  4B   digunakan   sebagai   mikrokontroler
untuk   mengumpulkan   data   dari   sensor   parameter
kesehatan [7].
## Penelitian Sistem Pemantauan Kuantitas Air Permukaan
dan Analisis Kualitas Air Secara Realtime
Menggunakan Mikrokontroler, Sistem ini
diimplementasikan menggunakan berbagai sensor untuk
mengukur kualitas air seperti Ph, suhu, sensor kekeruhan
dan  untuk  menganalisis  kuantitas  air  digunakan  sensor
aliran  atau  level  [8]. Pemantauan  dan  Pengendalian
Proses Inkubasi Ayam Menggunakan Sistem Internet of
Things,  penelitian  ini  membahas  tentang  pemantauan
dan   pengendalian   proses   produksi   ayam   didalam
inkubator.
Penelitian ini bertujuan untuk mengembangkan inovasi
teknologi   dalam   bidang   kefarmasian   yaitu   dengan
menciptakan   alat   pemantauan   suhu cold   chain   box
berbasis IoT menggunakan sensor suhu DS18B20 Water
Proof serta mikrokontroler ESP8266  yang  terintegrasi
dengan   aplikasi Telegram   dan   aplikasi Blynk IoT
sehingga   data   suhu   yang   didapat   akan   langsung
tersimpan  dan  bisa  ditampilkan  atau  diunduh. Proses
sistem  ini  dimulai saat  mikrokontroler  esp8266  telah
terhubung jaringan internet kemudian sensor dimasukan
ke   dalam cold   chain   box setelah   itu sensor   akan
mengirimkan  data  suhu  ke  aplikasi  Blynk  IoT  untuk
ditampilkan secara realtime dan memberikan peringatan
jika terjadi suhu naik atau tidak sesuai ketentuan vaksin,
sistem  ini  dapat  menyimpan  data  suhu  guna  dijadikan
sebagai laporan oleh apoteker.  Metode  penelitian  yang
digunakan  pada penelitian ini yaitu  metode  waterfall,
eksperimen,    dan    pemodelan    UML,    metode    ini
menjelaskan analisis perancangan alat secara
keseluruhan, hardware dan software yang  digunakan

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 3


serta   pengembangan   sistem yang   diterapkan   dalam
penelitian. Penelitian   ini   menghasilkan   sebuah   alat
pemantauan suhu cold chain box dengan tingkat akurasi
lebih 95%. Teknologi IoT yang dikembangkan pada alat
pemantauan   suhu ini memiliki   kemampuan   untuk
membaca   data   suhu   secara realtime,   memberikan
peringatan  dan  rekapan  data  suhu  yang diharapkan
dapat memberikan kontribusi dalam bidang farmasi serta
manfaat    dan    kemudahan    bagi    apoteker    dalam
menjalankan tanggungjawabnya sesuai dengan
## Peraturan Menteri Kesehatan Nomor 26 Tahun 2020.
## 2. Metodologi Penelitian
Dalam  melakukan  setiap  penelitian  diperlukan  suatu
metode ilmiah atau aturan yang telah ditetapkan. Hal ini
bertujuan untuk mendapatkan hasil yang maksimal dari
penelitian   tersebut.   Struktur   penulisan   yang   telah
mengacu  pada  metode-metode  yang  telah  ditetapkan
dapat   menjadi   elemen   yang   sangat   penting dalam
menyelesaikan  masalah  yang  dihadapi. Penelitian  ini
menggunakan  model waterfall yang  dapat  dilihat  pada
## Gambar 1.

## Gambar 1. Waterfall Model
Gambar  diatas  menjelaskan  terdapat  5  tahapan  proses
yang harus dilakukan dalam model waterfall, penelitian
ini    menggunakan    metode    waterfall    yang banyak
digunakan dalam pengembangan sebuah sistem. Model
waterfall digunkan karena dapat melakukan pendekatan
secara sistematis dan berurutan dalam membangun suatu
sistem.  Proses  pengerjaan  dari  pengembangan  suatu
sistem    dilakukan    secara    berurutan.    Sistem    yang
dihasilkan akan berkualitas baik, dikarenakan
pelaksanaannya secara bertahap sehingga tidak terfokus
pada tahapan tertentu.
2.1  Tahapan Analisa dan Perancangan
Tahapan ini   akan   dijelaskan   mengenai   analisa   dan
perancangan  dari  sistem  pemantauan  suhu Cold  Chain
Box   Vaccine Menggunakan   Sensor   Suhu   DS18B20
Water Proof  Berbasis Android. Analisa pada penelitian
ini  meliputi  analisa  sistem    dan  alat  serta  perancangan
pada  penelitian  ini  meliputi  perancangan  diagam  blok,
perancangan rangkaian perangkat  keras  mikrokontroler
ESP8266, perancangan arsitektur sistem IoT,
perancangan sistem dan flowchart.

Analisa  sistem  dilakukan  untuk  mengetahui  spesifikasi
dari  kebutuhan  aplikasi  yang  akan  dibangun dalam
menciptakan alat pemantauan suhu.

## 2.2  Model Pengembangan Sistem

Penelitian     ini menggunakan     pemodelan Unifed
Modeling   Language (UML). UML   muncul   karena
adanya kebutuhan pemodelan visual untuk
menspesifikasikan,  menggambarkan,  membangun  dan
dokumentasi dari perangkat lunak yang akan dibangun.
UML  merupakan  bahasa  visual  untuk  pemodelan  dan
komunikasi mengenai sebuah sistem dengan
menggunakan  diagram  dan  teks  pendukung.  Adapun
diagram  yang  digunakan  pada  penelitian  ini  sebagai
berikut:

a. Usecase Diagram
Usecase Diagam   adalah   salah   satu   diagram   pada
pemodelan  yang  menggunakan  UML  digunakan  untuk
memodelkan  hubungan  atau  interaksi  antara  pengguna
dan    sistem. Perancangan Usecase Diagram    pada
penilitian     ini     berfungsi     untuk     menggambarkan
kebutuhan  fungsional  dari  sistem  yang  dibuat.  Dengan
dirancangnya Usecase Diagram    ini,    maka    dapat
dideskripsikan   interaksi   dan   hubungan   antara user
dengan  sistem  pemantau suhu  cold  chain  box vaksin.
Usecase Diagram disajikan pada Gambar 2.

## Gambar 2. Usecase Diagram
Pada Usecase Diagram   digambarkan   bahwa   Alat
Temperature Monitoring sebagai aktor yang berinteraksi
secara    langsung    dengan Usecase Sensor    Suhu
DS18B20, Usecase Mikrokontroler Nodemcu ESP8266
dan Usecase Sistem  Pemantauan  Suhu  IoT. Interaksi
tersebut  dapat  dijelaskan  bahwa Usecase Sensor  Suhu
DS18B20 sebagai input yang  didapat  setelah  apoteker
meletakan sensor suhu DS18B20 ke dalam Cold Chain
Box vaksin. Sehingga  menghasilkan  data  suhu  yang
dapat  diproses  oleh Usecase Mikrokontroler  Nodemcu
ESP8266  yang  kemudian ditampilkan  dan disimpan
dalam database aplikasi Blynk IoT.


A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 4


b. Activity Diagram
Diagram   aktifitas   menggambarkan   suatu work   flow
(aliran  kerja)  atau  aktifitas  dari  sebuah  proses  kerja.
Dengan dibuatnya Activity Diagram, logika berjalannya
sebuah  sistem  dapat  dipelajari  dan  dimengerti  dengan
mudah. Perlu diperhatikan di sini adalah bahwa diagram
aktifitas  menggambarkan  aktifitas  sistem  bukan  apa
yang  dilakukan  aktor. Activity Diagram  dapat  dilihat
pada Gambar 3.

## Gambar 3. Activity Diagram
Pada Activity diagam  ini  dijelaskan mulai  dari  awal
hingga  akhir  dari  sistem  yang  dibuat.  Sensor  suhu
DS18B20 yang telah terhubung dengan mikrokontroler
ESP8266  melalui  jaringan  internet  dapat  memberikan
informasi   data   suhu   yang   disimpan   pada   database
aplikasi  Blynk  IoT  kemudian  menampilkan  data  suhu
tersebut pada aplikasi. Jika terjadi suhu naik maka akan
ada notifikasi jika suhu normal maka data suhu disimpan
untuk digunakan sebagai laporan.

c. Sequnce Diagram
Perancangan Sequence Diagram  atau  diagram  sekuen
adalah  diagram  yang  menggambarkan  kelakuan  objek
pada usecase dengan  mendeskripsikan  waktu  hidup
objek dan message yang dikirimkan dan diterima  antar
objek.  Berdasarkan usecase yang  telah  dibuat.  Berikut
ini  perancangan Sequence Diagram  Sistem  Pemantau
Suhu  Cold  Chain  Box  Vaksin  menggunakan  Sensor
Suhu   DS18B20   berbasis   Android disajikan   pada
## Gambar 4.
Sequnce Diagram mendeskripsikan   bahwa   kegiatan
pertama yang dilakukan dari usecase Alat Temperature
Monitoring adalah menghubungkan ke jaringan internet
Sensor  Suhu  DS18B20  dan  Mikrokontroler  ESP8266
agar  dapat  memberikan  informasi  data  suhu  dari Cold
Chain  Box. Informasi  data  suhu  tersebut  kemudian
dikirim  ke  sistem  IoT  untuk dapat  diproses  jika  terjadi
suhu  naik  maka  akan  ada  notifikasi  melalui  Aplikasi
Blynk  IoT  dan  Aplikasi  Telegram  kemudian  data  suhu
disimpan dan ditampilkan melalui smart phone.


## Gambar 4. Sequnce Diagram
d. State Machine Diagram
State  Machine Diagram adalah  representasi  visual  dari
sebuah mesin status (state machine), yang
menggambarkan  berbagai  status  (state)  yang  mungkin
dialami  oleh  suatu  sistem  atau  objek,  serta  transisi
(transition)  yang  terjadi  antara  status-status  tersebut
berdasarkan  berbagai  kejadian  atau kondisi  tertentu.
State   Machine   Diagram pada penelitian ini dirancang
dengan  tujuan  untuk  menggambarkan    suatu    perilaku
dinamis  dari  alat  yang akan dibuat  serta  kontrol pada
sistem. Alur State Machine Diagram pada Gambar 5.
Gambar   5 dapat   dijelaskan   alat   pemantauan   suhu
dimulai   dari   menghidupkan   alat   yaitu   dengan   cara
menghubungkan esp8266 dengan arus listrik,
menghubungkan  dengan  internet  kemudian  membuka
halaman  aplikasi  Blynk  IoT  untuk  menampilkan  data
suhu. Jika kondisi normal maka data suhu akan disimpan
sebagai  laporan.  Jika  suhu  tidak  sesuai  ketentuan  atau
naik  maka  akan ada  notifikasi  melalui  telegram blynk
iot.

e. Flowchart Sensor Suhu DS18B20
Dalam flowchart yang  disusun  akan  menggambarkan
urutan  proses  mendetail  antara  suatu  proses  dengan
proses yang lain dalam sebuah sistem. Pada  sistem ini,
flowchart menjelaskan alur input, proses dan output dari
sistem.   Adapun   perancangan   flowchart   alur   sistem
seperti Gambar 6.

Flowchat Sensor  Suhu DS18B20 menjelaskan  antara
sensor  suhu  yang  digunakan  dapat  terhubung  dengan
mikrokontroler ESP8266 yang terkoneksi dengan server
aplikasi blynk IoT untuk digunakan dalam pengambilan
data suhu pada cold chain box vaccine. Yang kemudian
data tersebut akan ditampilkan pada aplikasi Blynk IoT
## Android.

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 5


f. Blok Diagram Rangkaian
Blok diagram rangkaian merupakan gambaran dasar dari
rangkaian  sistem  yang  akan  dirancang.  Setiap  diagram
blok  dari  sistem  yang  akan  dirancang  memiliki  fungsi
masing-masing.  Adapun  diagram  blok  rangkaian  yang
dirancang pada sistem pemantauan suhu cold chain box
vaksin seperti pada Gambar 7.



## Gambar 5. State Machine Diagram



Gambar 6. Flowchart Sensor Suhu DS18B20

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 6


## Gambar 7. Blok Diagram

Prinsip    kerjanya    dengan    memasang    sensor    suhu
DS18B20  dimana  penerima  akan  mendeteksi  berupa
sinyal  digital  yang  akan  dikirimkan  ke  mikrokontroler
Nodemcu   ESP8266   yang   telah   terhubung   internet.
Nodemcu  ESP8266  berfungsi  sebagai  pemroses  data
lalu mengirimkan data tersebut ke server Blynk IoT dan
Telegram. Output menggunakan   aplikasi  blynk  IoT
android dan blynk IoT cloud.

g. Perancangan Rangkaian Hardware Mikrokontroler
Pada perancangan  ini terdapat  komponen-komponen
yang saling mendukung. Komponen tersebut
membentuk     sebuah     rangkaian hardware sistem
pemantauan  suhu  pada cold  chain  box vaksin  berbasis
IoT   Android.   Komponen   mikrokontroler   ESP8266
terdapat pin yang digunakan untuk menghubungkan dari
satu komponen dengan komponen yang lain, komponen
sensor  DS18B20,  komponen  pendukung  lain  seperti
resistor, kabel jumper dan usb connector disajikan pada
## Gambar 8.

## Gambar 8. Perancangan Rangkaian Hardware

Sensor suhu DS18B20 memiliki komponen yang terdiri
dari  3  pin  yaitu  pin  VCC  terhubung  dengan  sumber
tegangan pin 3V, pin GND (ground) terhubung dengan
pin GND  (ground), pin data  terhubung dengan pin D2.
Komponen  resistor  memiliki  2  kaki  pin  yang  yang
terhubung dengan sumber tegangan pin 3V dan pin basis
terhubung  dengan pin  data  dari  mikrokontroler.  Dalam
rangkaian  tersebut  juga  terdapat  kabel-kabel  jumper
yang berfungsi untuk menghubungkan antara
mikrokontroler NODEMCU ESP8266 dengan
komponen-komponen lain yang terdapat pada
breadboard.
h. Perancangan Arsitektur Internet of Things (IoT)
Perancangan Arsitektur Sistem Internet of Things (IoT)
ini merupakan bentuk dari keseluruhan perangkat keras
yang    saling    terhubung    untuk    menciptakan    alat
## Temperature   Monitoring   System Cold   Chain Box
Vaccine. Pada  perancangan  ini  komponen-komponen
yang  digunakan  terdiri  dari cold  chain  box, rangkaian
hardware, internet,    aplikasi    Blynk    dan    aplikasi
Telegram tersaji pada Gambar 9.


Gambar 9. Perancangan Arsitektur Sistem Internet of Things (IoT)

Penjelasan     hubungan     antar     komponen-komponen
tersebut   yaitu cold   chain   box vaksin   yang   sudah
dipasangkan     suhu     DS18B20     kedalamnya     akan
mengirimkan  data  suhu  ke  rangkaian  mikrokontroler
Nodemcu     Esp8266     untuk     disimpan     sementara.
Kemudian mengirimkan data suhu tersebut ke servernya
aplikasi Blyk   IoT   agar   bisa   disimpan,   diolah   dan
diunduh  sesuai  kebutuhan  apoteker.  Pemantauan  suhu
juga  dapat  dilakukan  secara realtime melalui  aplikasi
blyk IoT, jika suhu di dalam cold chain box naik maka
akan ada  notifikasi melalui aplikasi Blynk dan aplikasi
Telegram   yang   sudah   dipasangkan   melalui   ID Bot
## Telegram.

- Hasil dan Pembahasan
3.1 Implementasi alat
Setelah    perancangan    alat    dilakukan    maka    tahap
selanjutnya  yaitu  implementasi  alat.  Alat  pemantauan
suhu    dibuat    dalam    rangkaian    yang    terdiri    dari
mikrokontroler nodemcu    ESP8266,    sensor    suhu
DS18B20,  resistor  dan  lampu  LED  yang  dihubungkan
menggunakan kebel jumper serta usb connector sebagai
penghubung arus daya. Rangkaian alat ini berjalan pada
tegangan 3.3V sampai 5V disajikan pada Gambar 10.

## Gambar 10. Rangkaian Alat

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 7


Ukuran cold chain box yang digunakan pada penelitian
ini  sesuai  dengan  yang  digunakan  oleh  UPTD  Farmasi
Dinas  Kesehatan  Kab.  Siak.  Sensor  suhu  DS18B20
diletakan  didalam cold  chain  box vaksin  setelah  itu
sensor akan bekerja mengirimkan data suhu ke nodemcu
esp8266 yang  telah  terhubung  internet. Aplikasi Blynk
IoT kemudian menampilkan   data   suhu tersaji   pada
## Gambar 11.


## Gambar 11. Cold Chain Box
Cold Chain Box digunakan sebagai media penyimpanan
vaksin  untuk menjaga  suhu  rendah. Fungsi  dari Cold
Chain   Box adalah   menjaga   kualitas   produk   yang
membutuhkan lingkungan dengan suhu yang terkontrol.
Peran  penting  dari  penggunaan  media  penyimpanan
vaksin  ini  adalah  untuk  memastikan  keamanan  dan
efektifitas  mulai  dari penerimaan,  penyimpanan  dan
distribusi hingga saat digunakan

## 3.2 Implementasi Sistem

Komponen  utama  Blynk  yaitu  aplikasi,  Server,  dan
Libraries.   Blynk   server   berfungsi   untuk   menangani
semua  komunikasi  diantara smartphone dan hardware.
Widget  yang  tersedia  pada  Blynk  diantaranya  adalah
Button,  Value  Display,  History  Graph,  Twitter,  dan
Email.   Blynk   tidak   terikat   dengan   beberapa   jenis
mikrokontroler  namun  harus  didukung hardware yang
dipilih. Temperature  monitoring system cold chain box
vaccine diimplementasikan pada aplikasi Blynk  IoT
Android dan Blynk IoT Cloud sebagai media monitoring
suhu secara realtime.  Berikut  tampilan  pada  aplikasi
android tersaji pada Gambar 12.

Gambar 12. Aplikasi Blynk IoT Android
Aplikasi Blynk IoT dapat digunakan dengan memasukan
username dan password terlebih  dahulu  agar  dapat
mengakses  fitur-fitur  didalam  Blynk  IoT.Gambar  12.
dapat dilihat bahwa  Blynk  IoT  Android menampilkan
status  alat  pemantaun  suhu,  menampilkan  data  suhu
dalam   bentuk   angka,   grafik   pemantauan   suhu   dan
pengaturan ambang batas. Ambang batas pada penelitian
ini  dibuat dinamis agar  sistem  pemantauan  suhu  yang
dikembangkan ini dapat menyesuaikan jenis vaksin yang
ada di dalam cold chain box.

Gambar 13. Aplikasi Blynk IoT Web
Selain  dapat  diakses  melalui  android  sistem  ini  juga
dapat diakses memalui aplikasi web. Pada tampilan web
kita   dapat   melihat   status   perangkat   apakah dalam
keadaan terhubung atau tidak, mengontrol ambang batas
atas  dan  batas  bawah  suhu  sesuai  jenis  vaksin  yang
diletakan dalam clod chain box, melakukan pemantauan
suhu  secara realtime dengan  memperhatikan  indikator
Temp C dan Temp F pada aplikasi, terdapat grafik suhu
dan penyimpanan data suhu.
## 3.3 Hasil
Untuk   mengetahui   hasil   bahwa   perangkat   sistem
pemantauan suhu cold chain box vaksin berfungsi sesuai
dengan    harapan    maka    perlu    dilakukan    skenario
pengujian step   by   step pengujian      ini   terdiri   dari
pengujian hardware, software dan pengujian
keseluruhan    sistem.    Pengujian hardware meliputi
pengujian  daya,  pegujian  eso8266,  pengujian  sensor
suhu  ds18b20.  Pengujian software meliputi  pengujian
program    arduino,    pengujian    aplikasi    Blynk    IoT,
pengujian  notifikasi  dan  pengujian  laporan.  Pengujian
keseluruhan sistem meluputi pengujian hasil pembacaan
suhu   pada clod   chain   box,   pengujian   keseluruhan
perangkat   sistem   pemantauan   suhu cold   chain   box
vaccine.

a. Pengujian Daya
Perancangan  alat  pemantauan  suhu pada  penelitian  ini
menggunakan   daya   5V   sebagai   konsumsi   modul
mikrokontroler  esp8266  dan  sensor  suhu  DS18B20,
dalam  proses pengujian  daya  menggunakan  alat  ukur
multimeter   digital. Hasil   pengujian   ini rangkaian

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 8


Mikrokontroler     NODEMCU     ESP8266 terhubung
dengan daya tersaji pada Tabel 1.
## Tabel 1. Pengujian Daya
## No Waktu
## Menit
## Output V Multimeter Selisih
## V
## 1 00 5 5 0
## 2 05 5 5 0
## 3 10 5 5 0
## 4 15 5 5 0
## 5 20 5 5 0
## Rata-rata 5

Proses   pengambilan   data   pengujian   daya   dilakukan
sebanyak   5   kali   dengan   durasi   20   menit,   hasil
pengukuran    rata-rata    5    Volt.    Setelah    dilakukan
pengujian   dengan multimeter   digital   maka   proses
pengujian daya dilanjutkan dengan menghubungkan usb
connector  sebagai  media  pengantar  daya  dari  sumber
listrik, maka lampu indikator pada modul akan menyala
dan   indikator   akan   berkedip   satu   kali   jika   telah
terhubung arus listrik. Tujuan dari pengujian ini adalah
untuk  melihat  apakah  mikrokontroler  ESP8266  dapat
terhubung dengan arus listrik.

b. Pengujian ESP8266
Alat  pemantauan  suhu  yang  dirancang  menggunakan
esp8266   memiliki   modul   WIFI   untuk   mengakses
internet    dengan    cara    membuat    koneksi    TCP/IP.
Perangkat  ini  diprogram  menggunakan  Arduino  IDE
dengan  menambahkan  library  ESP8266  pada board
manager. Pengujian dilakukan dengan menghubungkan
esp8266 dengan tegangan 5V dan dimasukan program,
maka  lampu  indikator  daya  akan  menyala  dan  lampu
indikator  wifi  akan  berkedip  ketika  terhubung  jaringan
internet.  Pengujian  ini  dilakukan  untuk  melihat  apakah
mikrokontroler    ESP8266 dapat    terhubung    dengan
jaringan internet.



Gambar 14. Konfigurasi Jaringan WIFI
Gambar  14.  Menampilkan  wifi manager dari  esp8266
terdapat     menu     pilihan configurasi wifi     untuk
memasukan username dan password.  Info   untuk
melihat  status  wifi.  Exit  untuk  keluar  dari  halaman
konfigurasi  dan  update  untuk  melakukan  pembaruan
dari  jaringan  wifi  yang  tersedia. Hasil  pengujian  dapat
dilihat pada Gambar 15.


Gambar 15. IP Nodemcu ESP8266

Dari  hasil Gambar  15. menjelaskan  tampilan  esp8266
yang terkoneksi internet dengan IP address
192.168.43.164  sehingga  disimpulkan  modul  tersebut
berfungsi  dengan  baik. Perancangan  alat  pemantauan
suhu ini menggunakan  esp8266 yang  telah  memiliki
modul  WIFI  untuk  mengakses  internet  dengan  cara
membuat   koneksi   TCP/IP. Dengan   menambahkan
library ESP8266  pada board  manager perangkat  ini
dapat diprogram menggunakan Arduino IDE.
c. Pengujian Sensor Suhu DS18B20
DS18B20 adalah sensor suhu yang memiliki keakuratan
dan kemampuan dalam pengukuran suhu yaitu antara -
55°C hingga +125°C. Pengujian dilakukan dengan cara
meletakan termometer digital dan sensor suhu DS18B20
kedalam cold chain box.Tujuan dari pengujian ini adalah
untuk  mencari  selisih  antara  output  sensor  ds18b20
dengan termometer digital disajikan pada Tabel 2.

## Tabel 2. Pengujian Suhu Cold Chain Box
## Waktu
## 09/02/24
DS18B20 Pembanding Selisih
## 11:54:00 PM 7,9 7,9 0
## 11:53:00 PM 7,9 7,9 0
## 11:52:00 PM 7,9 7,9 0
## 11:51:00 PM 7,8 7,9 0,1
## 11:50:00 PM 7,9 7,9 0
## 11:49:00 PM 7,9 7,9 0
## 11:48:00 PM 7,9 7,9 0
## 11:47:00 PM 7,8 7,9 0,1
## 11:46:00 PM 7,7 7,8 0,1
## 11:45:00 PM 7,8 7,9 0,1
## 11:44:00 PM 7,8 7,9 0,1
## 11:43:00 PM 7,9 7,9 0
## 11:42:00 PM 8 7,9 0,1
## 11:41:00 PM 8 7,9 0,1
## 11:40:00 PM 8,1 7,9 0,2
## 11:39:00 PM 8,2 7,9 0,3
## 11:38:00 PM 8,2 7,9 0,3
## 11:37:00 PM 8,2 7,9 0,3
## 11:36:00 PM 8,2 7,9 0,3
## 11:35:00 PM 8,2 7,9 0,3
## Jumlah 159,3 157,9 2,4
## Rata-rata 8,0 7,9 0,12


A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 9


Kesalahan (%) sensor suhu =(0,12/7,9)x100%=0,15%
Akurasi = 100% - Persentase kesalahan
## = 100%-0,15%
## = 99,85%

Pengujian    pada Tabel 2 dilakukan    berdasarkan
Permenkes Nomor 12 tahun 2017 tentang
penyelenggaraan  imunisasi  disebutkan  bahwa  vaksin
merupakan produk biologis yang mudah rusak sehingga
harus disimpan pada suhu tertentu, yakni pada suhu 2°C
s.d 8°C untuk vaksin sensitif beku (tidak boleh beku) dan
pada  suhu -15°C s.d -25°C untuk vaksin yang sensitif
panas.   Dalam   pengujian   ini   digunakan   ketentuan
ambang batas atas 8°C dan dilakukan sebanyak 20 kali
pengukuran  dengan  mengambil  data  setiap  satu  menit,
maka   didapat  rata-rata  alat  pamantaun  suhu  8,0°C,
sedangkan pada alat termometer digital didapat rata-rata
7,9°C, sehingga dari data tersebut didapat selisih 8,0-7,9
=  0,1°C  dan  kesalahan  pada  sensor  suhu  0,15%  dan
akurasi  99,85%,  sehingga  bisa  dikatakan  masih  layak
dan akurat.

d. Pengujian Program Arduino
Serial  Monitor  pada  Arduino  digunakan sebagai  alat
untuk berkomunikasi antara komputer dengan perangkat
arduino  melalui antarmuka serial. Tujuan dari pengujian
ini  adalah  untuk  mengetahui  program  yang  diterapkan
pada  mikrokontroler  ESP8266  dapat  berfungsi  baik.
Hasil  uji  coba  alat  pemantauan  suhu cold  chain  box
vaksin  bisa  dilihat  pada  serial  monitor  arduino  ide
disajikan pada Gambar 16.

Gambar 16. Serial Monitor Arduino IDE.

Gambar 16. menjelaskan  bahwa  pemrograman  arduino
yang diterapkan pada mikrokontroler ESP8266 memiliki
AP-NAME  “AP-DSB20”  dan  AP-PASS  “12345678”
yang   digunakan   untuk   menghubungkan   ke   jaingan
internet. CHAT_ID “6232233229” dan
DEVICE_NAME “PROTO-01” yang digunakan untuk
menghubungkan     mikrokontroler     dengan     Aplikasi
Telegram.     Aplikasi     Blynk     IoT     dengan     nama
"Monitoring Suhu Vaksin Box" Token dari aplikasi yang
digunakan    untuk    menghubungkan    mikrokontroler
ESP8266  dengan  Blynk  IoT  Android  dan  Blynk  IoT
cloud serta aturan karakteristik penulisan kode program
arduino lainnya.
e. Pengujian Notifikasi Blynk IoT dan Telegram
Notifikasi  berguna  bagi  apoteker  untuk  memberikan
peringatan   jika   terjadi   kondisi   suhu   tidak   sesuai
ketentuan. Tujuan   dari   pengujian   ini   adalah   untuk
mengetahui  apakah  notifikasi  dari  Aplikasi  Telegram
dan  Aplikasi  Blynk  IoT  berfungsi  dengan  baik  saat
terjadi  kondisi  suhu  dalam cold  chain  box tidak  sesuai
ketentuan. Pengujian    ini    dilakukan    dengan    cara
menjadikan  suhu  dalam cold  chain  box naik  sehingga
akan  mengirimkan  notifikasi  berupa  bunyi  alarm  pada
Aplikasi Telegram  dan Aplikasi  Blynk  IoT disajikan
pada Gambar 17.

Gambar 17. Notifikasi Android dan Telegram

Gambar  diatas  dapat  dijelaskan  bahwa  notifikasi  pada
Blynk  IoT  dan  Telegram  dapat  berjalan  secara  baik
ditandai  dengan  terdapatnya  notifikasi  alat  terhubung
dan  juga  notifikasi  ketika  suhu  berada  pada  ambang
batas.  Notifiasi  atau  peringatan  ini  dapat  di  program
melalui  arduino  ide  dan  melauli  bot  telegram  dengan
memasukan  id  telegram  terlebih  dahulu.  Notifikasi  ini
akan terus terkirim hingga suhu didalam cold chan box
sudah sesuai dengan ketentuan vaksin.

f. Pengujian Laporan Data Suhu
Tujuan  dari pengujian  ini  adalah  untuk  mengetahui
apakah  data  suhu  dapat  disimpan dan  dapat  diunduh
yang  akan  digunakan  sebagai  laporan  oleh  apoteker.
Pengujian  ini  dilakukan  dengan  mengunduh  data  suhu
dari  aplikasi  blynk  IoT.  Hasil  unduhan  berupa  rekapan
data suhu disajikan pada Gambar 18.

## Gambar 18. Unduh Rekapan Data Suhu

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 10


Hasil  unduhan  rekapan data  suhu  menampilkan  waktu,
temperatur serta status. Setiap satu menit data suhu akan
disimpan data tersebut berupa angka suhu Temp C dan
Temp F. Status yang disimpan berupa status alat online
dan offline serta status ambang batas suhu.

g. Pengujian Keseluruhan Perangkat Sistem
## Pemantauan Suhu
Fungsi pengujian ini yaitu agar alat yang dikembangkan
dapat  berjalan  sesuai dengan  yang  diharapkan yaitu
dapat melakukan pemantauan suhu secara langsung dan
memberikan peringatan jika  suhu tidak normal. Tujuan
dari pengujian ini adalah untuk mengetahui atau menguji
secara  keseluruhan  perangkat  sistem  pemantauan  suhu
cold  chain  box. Pengujian  ini  dilakukan  menggunakan
alat   pemantauan   suhu ds18b20 dengan   termometer
digital.

## Tabel 3. Pengujian Keseluruhan
## Time Temp C
## Termometer
## Digital
## Status
## 09/02/24
## 11:54:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:53:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:52:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:51:00 PM
## 7,8 7,8 Suhu Aman
## 09/02/24
## 11:50:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:49:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:48:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:47:00 PM
## 7,8 7,8 Suhu Aman
## 09/02/24
## 11:46:00 PM
## 7,7 7,7 Suhu Aman
## 09/02/24
## 11:45:00 PM
## 7,8 7,8 Suhu Aman
## 09/02/24
## 11:44:00 PM
## 7,8 7,8 Suhu Aman
## 09/02/24
## 11:43:00 PM
## 7,9 7,9 Suhu Aman
## 09/02/24
## 11:42:00 PM
## 8 8 Suhu Aman
## 09/02/24
## 11:41:00 PM
## 8 8 Suhu Aman
## 09/02/24
## 11:40:00 PM
## 8,1 8,1
## Suhu Di
Ambang    batas
tinggi Panas
## 09/02/24
## 11:39:00 PM
## 8,2 8,2
## Suhu Di
Ambang    batas
tinggi Panas
## 09/02/24
## 11:38:00 PM
## 8,1 8,2
## Suhu Di
Ambang    batas
tinggi Panas
## 09/02/24
## 11:37:00 PM
## 8,1 8,2
## Suhu Di
Ambang    batas
tinggi Panas
## 09/02/24
## 11:36:00 PM
## Online

Tabel 3 menunjukan  hasil  pengambilan  data  suhu  dari
alat pemantauan suhu cold chain box dengan termometer
digital bahwa pada jam 11:36:00 PM terjadi pencatatan
data  suhu  8,1°C  dan  8,2°C  selisih  0,1°C  dikarenakan
suhu  dalam cold  chain  box terjadi  peningkatan  dengan
status  suhu  diambang  batas  tinggi,  pada  jam 11:41:00
PM terjadi pencatatan suhu yang sama yaitu 8°C dengan
status   suhu   aman,   pada   jam   11:54:00   PM   terjadi
penurunan suhu 7.8 dengan status suhu aman disajikan
pada Gambar 19.


Gambar 19. Penerapan Alat Pemantauan Suhu Cold Chain Box di
UPTD Farmasi DINKES Siak

Alat   Pemantauan   Suhu Cold   Chain   Box di   UPTD
Farmasi DINKES Siak ini mendukung pemantauan suhu
real-time, peringatan data suhu jika terjadi kondisi suhu
diatas ambang batas, serta laporan data suhu yang dapat
memberikan   kontribusi   dalam   bidang   farmasi   serta
manfaat  dan  kemudahan  bagi  apoteker. Keberlanjutan
terkait  penerapan  alat  pemantauan  suhu  bagi  apoteker
memberikan  kemudahan  dalam  pemantauan  suhu yaitu
bisa   dilakukan   pemantauan   suhu   dimanapun   dan
kapanpun  tanpa  harus  melakukan  pemantauan  setiap  2
jam ke ruangan farmasi. Sedangkan bagi bidang farmasi
dapat menjadi contoh pengelolan vaksin yang efisien.
## 4. Kesimpulan
Berdasarkan  hasil  penelitian  yang  telah  dilakukan  di
Dinas Kesehatan Kabupaten Siak UPTD Farmasi, serta
didukung  oleh  pembuatan,  pengujian  dan  pembahasan
yang  telah  dilakukan,  dapat  ditarik  kesimpulan  yakni
alat temperature  monitoring  system  cold chain box
vaccine dapat saling terintegrasi dengan baik dan dapat
terhubung dengan jaringan internet. Sistem pemantauan
suhu   berjalan   satu   arah   yaitu   ketika   sensor   suhu
DS18B20 dimasukan kedalam cold chain box maka akan
mengirimkan    data    suhu    ke    esp8266    kemudian
melanjutkannya     ke server dan terakhir akan
mengirimkannya   ke   aplikasi   blynk   iot   agar   bisa

A.D.Putra, dkk

Jurnal KomtekInfo − Vol. 12  No. 1 (2025) 1-11
## 11


dilakukan   pemantauan   suhu   secara realtime oleh
apoteker. Peringatan  atau  notifikasi  dapat  dikirimkan
melalui  aplikasi  blynk  iot  dan  telegram    jika  terjadi
kondisi suhu cold chain box tidak sesuai standar. Kinerja
apoteker  lebih  efektif  dan  efisien  dalam  memonitoring
kondisi clod chain box vaksin melalui apilikasi blynk iot
karena dapat diakses dimanapun dan kapanpun. Rekapan
data   suhu   dapat   diunduh   untuk   digunakan   sebagai
laporan oleh  apoteker  ke  Kepala  UPTD  Farmasi  Dinas
## Kesehatan Kabupaten Siak.
## Daftar Rujukan
[1] Kementerian Kesehatan RI.2020. Pedoman Pengelolaan Vaksin
di    Fasilitas    Pelayanan    Kesehatan. Direktorat    Jenderal
Kefarmasian dan Alat Kesehatan.
[2] D.  W.  Kusuma  Budi,  R.  Sari  Hartati,  D.  Arjana,  “Rancang
Bangun  Sistem  Monitoring  Suhu  Cold  Storage  Berbasis  IoT
Menggunakan Wemos D1 R2 di PT. Aerofood Acs Denpasar,”
## J. Spektrum Vol. 9, No. 4 Desember 2022.
## [3] E. S. Wijaya, M. Maulida, Y. Sari, A. R. Baskara, A. Rivaldy,
“Prototype  Monitoring  Suhu  Berbasis  Mikrokontroler  Pada
Cool Box Ikan Menggunakan Sensor DS18B20 Dengan Metode
Fuzzy,” Kumpulan  Jurnal  Ilmu  Komputer  (KLIK) Volume 07,
No. 3 Oktober 2020 ISSN: 2406-7857.
## [4] N.  F.  Khobariah,  P.  D.  S.  Hermawan,  R.  S.  Kusumadiarti,
“Sistem   Monitoring  Suhu   Dan  Kelembapan   Ruang  Server
Berbasis Wemos D1, ” J. Ilmiah Penelitian dan Pembelajaran
## Informatika Volume 07, Nomor 01, Maret 2022 : 32-42.
[5] Muthmainnah,  A.  Syaifudin,  N.  Chamidah,  “Prototipe  Alat
monitoring  Suhu  dan  Kelembaban  pada  Rumah  Penyimpan
Tembakau  Berbasis  Internet  of  Thing  (IoT),” J.Pendidikan
MIPA Volume 13. Nomor 1, Maret 2023 ISSN: 2088-0294, e-
## ISSN: 2621-9166, .
[6] Bzhar   Ghafour   Mohammed,   Dler   Salih   Hasan, "Smart
Healtcare Monitoring System Using IoT," International Journal
of   Interactive   Mobile   Technologies   (iJIM), January   2023
DOI:10.3991/ijim.v17i01.34675.
## [7] M.  Shahul  Hameed,  E.  Ramya,  Lawanya  Pillai,  K.  Jaraline
Kirubavathy, D.S. Dharshan Shylesh , Dr.V. Thulasi Bai, Dr.R.
Jaganathan, "  Realtime  Monitoring  System  for  Surface  Water
Quantity and Analyzing of Water Quality Using
Microcontroller," Journal of Pharmaceutical Negative Results
Volume 13 Special Issue 3 2022, DOI:
10.47750/pnr.2022.13.S03.073  .
## [8] Hossein    Roshanghiyasi1,    Ali    Haji    Ahmad,    Soleiman
## Hosseinpour,  Ali  Jafari,  Hossein  Mousazadeh,  Amirhossein
Asadollahzadeh, "Monitoring   and   controlling   the   chicken
Incubation  Process  Using  the  Internet  of  Things  System,"
Journal  of  Agricultural  Mechanization 7  (1):  73-77, DOI:
https://dx.doi.org/10.22034/jam.2021.15710
[9] Salsabila Alnitri Arrahma, Riki Mukhaiyar, "Pengujian ESP32-
Cam  Berbasis  Mikrokontroler ESP32",  JTEIN:Jurnal  Teknik
Elekro  Indonesia  Vol.4,  No.  1,  2023,pp.60-66,  e-ISSN  2723-
0589, DOI:https://doi.org/10.24036/jtein.v4i1.347.
## [10] M    Wujut    Hariyanto,    Ade    Hendri    Hendrawan,    Ritzkal,
"Monitoring  the  Environmental  Temperature  Using  Arduino
and Telegram", Journal of Robotics and Control (JRC) Vol. 1,
No.   3,   May   2020,   pp.   96-101   ISSN:   2715-5072,   DOI:
## 10.18196/jrc.1321.
## [11] Muhammad   Awaluddin,   Syahrir,   Ahmad   Zarkasi,   Erlinda
Ratnasari  Putri,"Rancang  Bangun  Prototipe  Monitoring  Suhu
dan Kelembaban Udara Berbasis Internet of Things (IoT) Pada
Laboratorium  Kalibrasi  Balai  Pengujian  dan  Sertifikasi  Mutu
## Barang  Samarinda",  Progressive  Physics  Journal  Volume  3,
Nomor 1, Juni 2022 ISSN 2722-7707 (online)
http://jurnal.fmipa.unmul.ac.id/index.php/ppj/index.
## [12] Andi  Boy  Panroy  Manullang,  Yuliarman  Saragih,  Rahmat
Hidaya,"Implementasi   Nodemcu   Esp8266   Dalam   Rancang
Bangun  Sistem  Keamanan  Sepeda  Motor  Berbasis  Iot",  JIRE
(Jurnal Informatika & Rekayasa Elektronika) Volume 4, No 2,
November  2021 http://e-
journal.stmiklombok.ac.id/index.php/jire.
## [13] Fredy   Susanto,   Ni   Komang   Prasiani,   Putu   Darmawan,"
## Implementasi  Internet  Of  Things  Dalam  Kehidupan  Sehari-
Hari",  JURNAL  IMAGINE  Vol.  2  No 1 – April 2022  p-ISSN
2776-5342   (Print),   e-ISSN   2776-9836   (Online)   Available
Online at: https://jurnal.std-bali.ac.id/index.php/imagine.
[14] Siddharth  Chittora," Home  Automation  System",  international
Research  Journal  of  Engineering  and  Technology  (IRJET)  e-
ISSN:    2395-0056    Volume:    04    Issue:    12    |    Dec-2017
www.irjet.net p-ISSN: 2395-0072.
## [15] Aulia  Desy  Nur  Utomo,  Anggi  Zafia,  Bita  Parga  Zen,  Dimas
## Fanny   Hebrasianto   Permadi,   Henri   Tantyoko,   Yoso   Adi
Setyoko," Implementasi Internet of Things (IoT) pada SMK AL
Hikmah 2 dalam mendukung Revolusi Industri 4.0", Indonesian
Journal of Community Service and Innovation (IJCOSIN) Vol.
3,   No.   2,   Juli   2023,   Hal.   49-57   e-ISSN:   2807 - 6370
http://journal.ittelkom-pwt.ac.id/index.php/ijcosin.
## [16] Widya   Nugraheni   Widiningrum,   Siti   Hadijah,   Supriyadi,
## Sulhadi,"     Rancang     Bangun     Alat     Ukur     Suhu     Skala
Celcius,Reaumur, Fahrenheit Dan Kelvin Dalam Pembelajaran
Fisika",  Jurnal  inovasi  dan  pembelajaran  fisika  JIPF-UNSRI,
ejournal.unsri.ac.id/index.php/JIPF.
## [17] Handi,  Hurriyatul  Fitriyah,  Gembong  Edhi  Setyawan," Sistem
Pemantauan Menggunakan Blynk dan Pengendalian
## Penyiraman  Tanaman  Jamur Dengan  Metode  Logika  Fuzzy",
Jurnal Pengembangan Teknologi Informasi dan Ilmu Komputer
e-ISSN: 2548-964X Vol. 3, No. 4, April 2019, hlm. 3258-3265
http://j-ptiik.ub.ac.id.
## [18] Ramadhina Trie Ananda, Djamaludin, Dadang Sujana," Sistem
## Tempat  Sampah  Pintar  Berbasis  Iot  Menggunakan  Aplikasi
Blynk",  Jurnal  Elektro  Telekomunikasi  Terapan,  ISSN  (p)  :
2407-1323 ISSN (e): 2442-4404 DOI
https://doi.org/10.25124/jett.v8i2.4073| Vol. 8 | No. 2 | Halaman
## : 1027 - 1038
## [19] Yohanes  Bowo  Widodo,  Ahmad  Gunawan,  Tata  Sutabri,"
Perancangan    Sistem    Monitoring    Nutrisi    pada    Tanaman
Hidroponik Berbasis Arduino Uno",Jurnal Teknlogi
Informatika dan Komputer MH. Thamrin    p-ISSN 2656-9957;
e-ISSN  2622-8475  Volume  8  No  1;  30  Maret  2022,  DOI  :
https://doi.org/10.37012/jtik.v8i1.850
## [20] Deni  Ahmad  Jakaria  ,  Muhammad  Rifki  Fauzi," Aplikasi
## Smartphone   Dengan   Perintah   Suara   Untuk  Mengendalikan
Saklar Listrik Menggunakan Arduino", JUTEKIN Vol 8 No. 1
(2020) – ISSN  :  2338-1477 – EISSN  :  2541-6375,  Halaman
Jurnal: http://jurnal.stmik-dci.ac.id/index.php/jutekin/.
## [21] Dani    Orlando,    Daniel    R.    Kaparang,    Kristofel    Santa,"
## Perancangan     Sistem     Kontrol     Suhu     Ruangan     Server
## Menggunakan  Arduino  Uno  Di  Pusat  Komputer    Universitas
Negeri Manado", JOINTER – JOURNAL OF INFORMATICS
## ENGINEERING , VOL. 02, NO. 02,DESEMBER 2021.
