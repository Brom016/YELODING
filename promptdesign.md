# Fusion 360 MCP Prompt — Smart Cold Chain Transport Box

> Paste prompt ini ke Claude MCP yang terhubung ke Autodesk Fusion 360. Satu prompt = satu model jadi.
> Cocok dengan `detail.md` / `dimension.md` terkini: kompresor AC GQR30TG via inverter, baterai 100 Ah,
> PV 20 W permanen di atas tutup dengan cover pelindung, machine tier 490 × 350 × 332 mm.

---

## PROMPT

```
Build the complete "Smart Cold Chain Transport Box" model in a new Fusion 360 document
named "ColdChainBox_v2". Units: millimeters. Build everything in one session, bottom-up,
using the exact dimensions and positions below. Do not ask for confirmation between steps —
finish the whole model, then present the result.

═══════════════════════════════════════════════
1. BASE GEOMETRY (bottom-up stack)
═══════════════════════════════════════════════
- "MachineTier_Shell": box 490 × 350 × 332, bottom face at Z = 0, centered on XY origin.
- "Separator_PUR_Al": box 458 × 334 × 17, bottom at Z = 332.
- "ColdBox_Shell": box 458 × 334 × 383, bottom at Z = 349 (top at Z = 732).
  The cold box is centered on the machine tier, leaving a 16 mm ledge around it at
  Z = 332 — this stepped footprint is intentional, do not "fix" it.

═══════════════════════════════════════════════
2. COLD BOX WALL STACK (hollow the cold box)
═══════════════════════════════════════════════
Inside ColdBox_Shell, working inward:
- Shell 2 mm on all faces except the bottom → "HDPE_Skin_ColdBox" (charcoal matte R:54 G:54 B:56, RAL 7021).
- VIP layer 25 mm inward → "VIP_Insulation" (cream R:220 G:210 B:160).
- PP liner 2 mm inward → "PP_Liner" (off-white R:248 G:248 B:245).
- The remaining void must measure 400 × 250 × 300 mm: this is the payload chamber.
  Add a reference body "PayloadChamber_Void" at that volume.

═══════════════════════════════════════════════
3. LID + HARDWARE (rear-hinged, opens 0–120°)
═══════════════════════════════════════════════
- "Lid_Body": box 458 × 334 × 29 on top of the cold box (skin 2 + VIP 25 + liner 2),
  same charcoal RAL 7021.
- "LidGasket": 4 mm EPDM band (R:40 G:40 B:40) around the lid bottom face perimeter.
- Two brushed-stainless hinges Ø12 × 60 on the rear top edge (long edge, Y = +167),
  centers 100 mm in from each end.
- Revolute joint "LidHinge" about that rear edge axis, limits 0° (closed) to 120° (open).
- Two stainless latch blocks 30 × 20 × 15 on the lid front bottom edge, 100 mm from ends.
- "TamperHasp": stainless block 30 × 10 × 25 at the front center.
- Yellow accent stripes (RAL 1023, R:255 G:237 B:0), 5 mm bands, extruded 1 mm proud:
  full perimeter on the lid bottom edge, cold box top edge, and machine tier top edge.

═══════════════════════════════════════════════
4. PV DECK + COVER ON THE LID (moves with the lid)
═══════════════════════════════════════════════
Build inside the Lid component so everything inherits the hinge motion:
- "PV_AdapterPlate": flat plate 440 × 320 × 2, centered on the lid top, charcoal.
- "PV_Panel_20W": 440 × 320 × 3 bonded on it — cell surface navy R:20 G:30 B:60 with a
  metallic sheen, grey frame border 8 mm (R:50 G:50 B:50), subtle 6 × 10 cell grid
  (0.5 mm ridges, R:10 G:15 B:40), junction box 60 × 40 × 8 at the rear edge.
- "PV_Cover": HDPE plate 460 × 336 × 2 with a 15 mm perimeter frame (8 × 15 section),
  charcoal, with a 5 mm yellow stripe on the frame front edge.
- Revolute joint "PVCoverHinge" between PV_Cover and Lid_Body on the SAME rear axis
  as LidHinge (co-axial), limits 0° (closed) to 100° (open). The panel and cover swing
  with the lid — permanent fit, never removed.
- Cover hardware: 2 stainless quarter-turn latches 20 × 20 × 10 at the cover front edge,
  a stainless padlock eye (torus Ø12, wire Ø3) center front, and a reed-switch block
  15 × 8 × 6 (R:10 G:10 B:10) named "PVCoverReedSwitch".
- "PV_CableLoop": sweep Ø4 along a spline from the junction box down the rear hinge side
  into the machine tier, shaped as a U-loop with slack for the full 120° lid travel.
- Collision check: the cover must not hit the cold box rear wall at any angle between
  closed and fully open; if it clips, reduce PVCoverHinge travel to 90°.

═══════════════════════════════════════════════
5. PCM + EVAPORATOR (inside the payload chamber)
═══════════════════════════════════════════════
- "PCM_PlateA_Left" and "PCM_PlateA_Right": 400 × 13 × 313 flush against the two long
  interior walls. "PCM_PlateB_Floor": 400 × 276 × 13 on the payload floor.
  Appearance pale blue R:200 G:225 B:245.
- "Evaporator_Plate": 400 × 250 × 12 directly under the floor plate,
  aluminum anodized R:160 G:160 B:155.
- "Evaporator_Coil": 6-pass serpentine, 6 lines 380 mm long spaced 35 mm with U-turns;
  sweep Ø8 copper (R:184 G:115 B:51) along it.
- "CircFan_80mm": cylinder Ø80 × 15 at the payload floor short edge, dark grey.
- Probes (visual, orange R:200 G:100 B:20, Ø6 × 150):
  "Probe_T1" top-centre, "Probe_T2" bottom-centre, "Probe_T3" mid-wall.
- "TEC_ColdSide_Fin": 40 × 40 × 25 fin block at the payload floor corner, purple R:100 G:50 B:180.

═══════════════════════════════════════════════
6. MACHINE TIER INTERNALS (positions in mm from the tier origin,
   bottom-front-left corner of the INTERNAL space 480 × 340 × 320)
═══════════════════════════════════════════════
POWER CHAIN
- "Battery_LiFePO4_100Ah": 329 × 172 × 214 at X 0–329, Y 0–172, Z 0–214.
  Dark navy R:20 G:40 B:80, terminal blocks on top.
- "Inverter_1000W_PSW": 300 × 160 × 85 at X 10–310, Y 10–170, Z 224–309 —
  on the battery via 4 rubber standoffs Ø20 × 10. Dark grey R:35 G:35 B:35,
  fin pattern on top, AC terminal strip on the front edge.
- "MPPT_A_10A": 168 × 100 × 30 at X 10–178, Y 180–280, Z 0–30. Dark grey.
- "MPPT_B_20A": 123 × 90 × 35 at X 10–133, Y 180–270, Z 40–75 (stacked above MPPT-A). Dark grey.
- "ElectronicsBox": 130 × 80 × 60 at X 195–325, Y 180–260, Z 0–60. Dark purple R:25 G:15 B:50.

COOLING CHAIN
- "Compressor_GQR30TG": vertical cylinder Ø130 × 165 (envelope 140 × 140 × 170) at
  X 335–475, Y 5–145, Z 0–170, on 4 rubber mounts Ø20 × 10. Dark green R:30 G:60 B:30, domed top.
- "Condenser_WireTube": face 280 × 150, 55 deep, flush on the Y+ interior wall at
  X 100–380, Y 285–340, Z 30–180, with horizontal copper Ø6 tube lines every 15 mm.
- "CondenserFan_1" and "CondenserFan_2": 120 × 120 × 25 fans side by side in front of
  the condenser (Y ≈ 260), centered at X 170 and X 310, Z 30–180 — body, 5-blade rotor,
  finger-guard ring each.

ELECTRICAL PROTECTION
- "FusePanel": 140 × 100 × 100 at X 340–480, Y 150–250, Z 0–100, near-black,
  3 MEGA-style fuse carriers on the face.
- "AC_Outlet_RCD": 90 × 70 × 60 at X 390–470, Y 260–330, Z 0–60 — Schuko-style socket
  + red RCD test button on the face.

VENTS
- Cut "ExhaustOpening" 320 × 160 through the Y+ tier wall behind the condenser
  (X 90–410, Z 30–190); add finger-guard + insect-mesh grille.
- Cut "InletOpening" 200 × 60 on the X− end wall upper section (Z 240–300);
  add 6 louvre slats angled 45°.

MISC
- "TEC_HotSide_Heatsink": 60 × 60 × 20 finned block at X 5–65, Y 190–250, Z 170–190,
  passing through the separator, purple.
- Rear face (exterior): "GNSS_Antenna_Bulkhead" and "LTE_Antenna_Bulkhead",
  Ø15 × 5 cylinders at diagonal corners ≥ 250 mm apart, light grey R:200 G:200 B:195;
  copper foil "GroundPlane_Copper" 100 × 100 × 0.5 behind the GNSS antenna.
- Sanity check: no two bodies intersect; the 16 mm ledge at Z = 332 stays clear
  except where the exhaust duct passes.

═══════════════════════════════════════════════
7. FRONT PANEL + PORTS (machine tier front face)
═══════════════════════════════════════════════
- "ControlPanel_Bezel": 90 × 50 × 3 plate, left side of the front face
  (30 mm from the left edge, 70 mm from the bottom), black anodized.
- "OLED_Display": 44 × 22 × 2 window, upper-left of the bezel — EMISSIVE navy
  R:0 G:26 B:51 with cyan text feel R:0 G:204 B:255.
- Three EMISSIVE Ø5 LED spheres, right column: green R:0 G:255 B:68 (top),
  red R:255 G:34 B:0 (mid), yellow R:255 G:204 B:0 (bottom).
- "BuzzerGrille": 3 × Ø2 holes, lower-left of the bezel.
- "PowerPort_12VDC": barrel socket Ø10 × 15 deep, right side of the front face
  (30 mm from the right edge, vertically centred), brushed stainless.
  "PowerPort_Label": 30 × 1 × 8 plate under it, RAL 1023 yellow.
  "PowerPort_Cover": black rubber hemisphere Ø14 hinged over the port.
- "AC_Outlet_Flap": spring flap 95 × 75 on the front face far right over the AC outlet,
  charcoal with a yellow warning stripe.

═══════════════════════════════════════════════
8. EXTERNAL HARDWARE
═══════════════════════════════════════════════
- 4 corner guards 30 × 30 × 20, matte black rubber, at the cold box base corners.
- 4 tie-down eyes (tori Ø20 outer / Ø10 inner / 8 tall), yellow powder coat,
  at the machine tier base corners.
- 2 recessed handle pockets 160 × 60 × 25 deep, centred vertically on each side wall
  of the cold box, grip surface dark grey.
- 1 pressure-equalization valve: flush membrane vent Ø15 with a stainless mesh face,
  on the cold box upper side wall near the front — equalizes sea-level ↔ mountain
  pressure so the lid latches never carry a ΔP load.

═══════════════════════════════════════════════
9. APPEARANCES (global pass)
═══════════════════════════════════════════════
- All exterior skins, lid, PV cover, adapter plate: charcoal RAL 7021 R:54 G:54 B:56 matte.
- Yellow RAL 1023 R:255 G:237 B:0: all stripes, tie-down eyes, power port label, cover stripe.
- Stainless (built-in "Stainless Steel (Brushed)"): hinges, latches, hasp, power port.
- Copper R:184 G:115 B:51: evaporator coil, condenser tubes, ground plane.
- OLED + LEDs: EMISSIVE (apply last, in the rendering workspace).
- Do not use white for the exterior — charcoal is intentional (a light-grey RAL 7035
  variant exists as a thermal fallback; it is NOT the default).

═══════════════════════════════════════════════
10. USER PARAMETERS (create these and drive the model with them)
═══════════════════════════════════════════════
cb_L 458 · cb_W 334 · cb_H 383 · mt_L 490 · mt_W 350 · mt_H 332 · sep_t 17 ·
skin_t 2 · vip_t 25 · liner_t 2 · pcm_t 13 · evap_t 12 · pay_L 400 · pay_W 250 ·
pay_H 300 · lid_t 29 · lid_angle 120 · pv_L 440 · pv_W 320 · pv_t 3 · cov_angle 100 ·
bat_L 329 · bat_W 172 · bat_H 214 · inv_L 300 · comp_d 130 · comp_h 165 ·
cond_L 280 · cond_H 150  (mm; lid_angle and cov_angle in degrees)

═══════════════════════════════════════════════
11. FINISH
═══════════════════════════════════════════════
- Set the hero pose: LidHinge = 100°, PVCoverHinge = 60°, ground plane visible at Z = 0.
- Save the document.
- Render 4K PNGs: (1) "hero" front-right isometric at the hero pose;
  (2) "front" straight-on front face; (3) "open" lid 120° + cover 100° showing payload.
- Export STL: "ColdChainBox_full.stl" and "ColdChainBox_lid_PV.stl" (lid + panel + cover).
```

---

## CATATAN UNTUK MCP

- Kalau sebuah fitur gagal di tengah jalan, perbaiki dulu dari timeline sebelum lanjut — jangan skip.
- Dua joint revolute yang krusial: `LidHinge` (0–120°) dan `PVCoverHinge` (0–100°, ko-aksial).
  Cover tidak boleh menabrak dinding belakang cold box di sudut mana pun.
- Footprint berundak (machine tier lebih lebar dari cold box) memang disengaja.
- Tampilan EMISSIVE untuk OLED/LED butuh rendering workspace — terapkan terakhir.
- Semua dimensi dan posisi berasal dari `dimension.md` §5 dan §8; jangan diubah tanpa
  mengubah dokumen sumbernya dulu.
