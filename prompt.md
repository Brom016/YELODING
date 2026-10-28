# prompt.md — Text-to-image prompts (real hardware, not the Wokwi simulation)

Prompt di bawah siap tempel ke generator gambar (Midjourney, DALL-E / GPT Image, SDXL, Flux, Ideogram). Semua komponen mengikuti desain final di `detail.md`: panel 150 W, MPPT 20 A, baterai LiFePO4 12 V 20 Ah, kompresor DC kelas BD35F, TEC trim, ESP32 + LTE-M + GPS, 3 probe DS18B20.

Tiga catatan jujur sebelum mulai:

1. Generator gambar bagus untuk diagram ilustratif, tapi teks label sering kacau (huruf ngawur). Regenerate beberapa kali, atau tambahkan label manual di Figma/Canva setelah gambar jadi. Daftar label untuk ditempel manual ada di bagian paling bawah.
2. Untuk skematik yang benar-benar akurat secara listrik, akhirnya tetap digambar di KiCad / draw.io / Fritzing. Prompt di sini untuk visual presentasi dan poster, bukan pengganti skematik produksi.
3. Satu prompt = satu diagram. Jangan minta semua dalam satu gambar, hasilnya jadi sampah visual.

## 1. Master power wiring diagram (panel surya sampai beban)

```
A clean professional technical wiring diagram, vector illustration style, white background,
showing a 12V off-grid solar power system for a medical cold chain transport box:
a 150W monocrystalline solar panel on the left connected via a 10A blade fuse and a Schottky
blocking diode to an MPPT charge controller (20A), the controller connected to a 12V 20Ah
LiFePO4 battery with integrated BMS, from the battery a 15A fused distribution point feeds
three branches: a 12/24V DC compressor unit (Secop BD35F class) driven through a power MOSFET
with a 1N4007 flyback diode across its coil, a TEC Peltier module 12V 60W through a driver,
and a LM2596 buck converter stepping 12V down to 5V for an ESP32 microcontroller board.
Include red positive wires, black ground wires, clear component symbols, small labeled callout
boxes, subtle blue outline for the cold box enclosure at right side. Flat colors, engineering
documentation style, high detail, 16:9 aspect ratio.
```

## 2. IoT system architecture

```
A modern clean IoT system architecture diagram, flat vector style, white and light cream
background with Starbucks green accents, showing data flow from left to right: three DS18B20
temperature probes and a DHT22 ambient sensor connected to an ESP32 microcontroller, a GPS
module and a LTE-M cellular modem beside it, the ESP32 sending encrypted telemetry over a
cellular tower icon to a cloud MQTT broker, then to a web dashboard on a laptop screen and a
smartphone. Include a small hash-chain icon (three linked blocks) labeled as tamper-evident
log, a bell icon for alarms, a battery icon for the 12V LiFePO4 power. Rounded rectangles for
each subsystem, thin connecting arrows, minimal labels, professional engineering poster look,
no photorealism, 16:9 aspect ratio.
```

## 3. Component-level electronic schematic (controller board)

```
A detailed electronic circuit schematic drawn in the style of a professional KiCad schematic
sheet on white background, centered on an ESP32-WROOM-32 module. Around it: two DS18B20
temperature sensor inputs on one pin with a 4.7k ohm pull-up resistor to 3.3V, a DHT22 sensor
on GPIO5, an SSD1306 OLED on I2C pins GPIO21 and GPIO22, a SIM7080 LTE-M modem on UART2, a
NEO-6M GPS module, an active buzzer on GPIO25, three indicator LEDs (green, red, yellow) each
with a 220 ohm series resistor. Power section on the left: 12V input from battery through a
15A blade fuse, reverse polarity protection Schottky diode, LM2596 buck converter 12V to 5V,
AMS1117-3.3 LDO regulator to 3.3V, decoupling capacitors 100nF ceramic next to every IC plus
one 470uF electrolytic on the 12V rail, a TVS transient suppression diode on the input, and a
voltage divider with 10k ohm and 3.3k ohm resistors feeding the battery voltage sense pin.
Standard schematic symbols, straight orthogonal wires with junction dots, small reference
designators like R1 C3 D2, grid layout, no perspective, flat 2D, 4:3 aspect ratio.
```

## 4. Photorealistic cutaway of the real cold box

```
Photorealistic product cutaway render of a two-tier portable medical cold chain transport
box, isometric three-quarter view, studio lighting on a warm cream background. Top tier is an
insulated cold box with a 30 liter payload chamber holding three stacked vaccine trays, the
wall cross-section visibly showing the layer stack from inside out: food-grade liner, 13mm
phase change material plates with a pale blue waxy texture, vacuum insulation panels, and a
dark grey HDPE outer skin. A chilled aluminum evaporator plate under the floor. Bottom tier
is the machine bay containing a small DC compressor with copper tubing, a flat 20Ah LiFePO4
battery, and a compact green electronics board with an antenna. A control panel with a small
OLED display and three indicator LEDs on the front face. Thin white callout lines with label
placeholders pointing to each internal component, realistic materials and soft shadows,
technical product photography look, 3:2 aspect ratio.
```

## 5. Real controller board, macro photo style

```
Macro photograph of a real custom perfboard electronic assembly on a workbench, shallow depth
of field: an ESP32-WROOM-32 devkit wired to a small green PCB carrying a SIM7080 LTE modem
with a thin coax antenna cable, a NEO-6M GPS module with ceramic patch antenna, three DS18B20
waterproof temperature probe cables entering from the left, an SSD1306 OLED display, a black
piezo buzzer, three 5mm LEDs with 220 ohm resistors, neat red and black silicone wires going
to a XT60 connector, a small LM2596 buck converter module set to 5V, 100nF ceramic and 470uF
electrolytic capacitors visible near the power entry, clean soldering, realistic solder joints,
warm workshop lighting, shot on 100mm macro lens, f/4, photorealistic, no text overlays.
```

## 6. Installed system in context (untuk bagian pilot di esai)

```
Photorealistic scene of the cold chain transport box strapped to the deck of a small island
fishing boat under bright tropical sun, the two-tier grey and green box with tie-down straps
over its four lashing eyes, a health worker in a light blue uniform checking a smartphone that
shows a temperature dashboard, calm turquoise sea and a distant coastline in the background,
realistic lighting and materials, documentary photography style, 3:2 aspect ratio.
```

## Negative prompt (untuk SDXL / Flux)

```
blurry, low quality, watermark, signature, cartoon, chibi, extra wires, tangled spaghetti
wiring, garbled text, gibberish labels, oversaturated, collage, multiple panels, jpeg artifacts
```

## Setting per tool

| Tool | Saran |
|---|---|
| Midjourney | tambahkan ` --ar 16:9 --style raw --v 6.1` (skematik pakai `--ar 4:3`) |
| DALL-E / GPT Image | minta "wide landscape image" di awal prompt kalau rasio tidak bisa diisi langsung |
| SDXL / Flux | 1344 × 768 untuk 16:9, 1024 × 1024 untuk skematik, CFG 5-7 |
| Ideogram | paling kuat untuk teks label pendek, cocok untuk diagram 1 dan 2 |

## Label untuk ditempel manual setelah gambar jadi

Kemungkinan besar teks dari AI kacau. Ini daftar label yang layak diketik ulang di atas gambar:

- Power: `PV 150 W`, `Fuse 10 A`, `Schottky blocking diode`, `MPPT 20 A`, `LiFePO4 12 V 20 Ah + BMS`, `Fuse 15 A`, `DC compressor 12/24 V`, `Flyback 1N4007`, `TEC 60 W`, `Buck 12 V to 5 V`
- IoT: `3x DS18B20 (30 s sampling)`, `DHT22 ambient`, `GPS`, `LTE-M / NB-IoT`, `MQTT broker (TLS)`, `Web dashboard`, `Hash-chained log`
- Board: `ESP32-WROOM-32`, `4.7 k pull-up`, `220 ohm LED resistors`, `100 nF decoupling`, `470 uF bulk`, `TVS diode`, `10 k / 3.3 k battery sense`
- Box: `Payload 30 L (2-8 C)`, `PCM plates 7 kg`, `VIP 25 mm`, `Evaporator plate`, `Compressor bay`, `Battery 20 Ah`, `Separator PUR 15 mm`
