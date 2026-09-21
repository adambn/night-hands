# Bill of materials & where to buy

> **Prices are approximate (Sept 2026, US) — verify at checkout.** Feetech servo
> pricing in particular varies a lot between resellers; the same part shows up
> anywhere from $15 to $50. Buy from the robotics shops below, not from random
> eBay listings.

Buy in **three waves**, so nothing sits in a box for a month.

---

## Wave 1 — buy today (~$90)

Enough to get a motor moving next Sunday. Nothing here is wasted later.

| Qty | Part | ~$ ea | Where |
|---|---|---|---|
| 1 | **Seeed XIAO ESP32S3 Sense** (camera + mic on board) | $24 | [Seeed](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) · [Mouser](https://www.mouser.com) · [DigiKey](https://www.digikey.com) · Amazon |
| 1 | **Bus Servo Driver Board for XIAO** — the Feetech UART adapter | $10 | [Seeed](https://www.seeedstudio.com/Bus-Servo-Driver-Board-for-XIAO-p-6413.html) · [wiki + example code](https://wiki.seeedstudio.com/xiao_bus_servo_adapter/) |
| 2 | **Feetech SCS0009** serial bus servo (6 V, 2.3 kg·cm) | $16 | [Seeed](https://www.seeedstudio.com/Feetech-SCS0009-Servo-p-6535.html) · [Abra](https://abra-electronics.com/electromechanical/motors/servo-motors-feetech/scs0009.html) · [Evelta](https://evelta.com/scs0009-6v-2-3kg-300deg-serial-bus-servo-motor/) |
| 1 | **6 V 5 A regulated supply**, 5.5×2.1 mm barrel | $14 | Amazon — search "6V 5A power supply 5.5x2.1" |
| 1 | USB-C data cable (a *data* cable, not a charge-only one) | $8 | anywhere |
| 1 | **Braided Dyneema fishing line**, 30–50 lb | $10 | Amazon / any sporting goods store |
| 1 | **PTFE (Bowden) tube**, 2 mm OD / 1 mm ID, 1 m | $8 | Amazon — sold as 3D printer Bowden tube |

**Why 2 servos and not 1:** so Jonathan can set two different IDs and see the
bus actually address them separately. That's the lesson.

---

## Wave 2 — order when the hand design is locked (~$170)

| Qty | Part | ~$ ea | Where |
|---|---|---|---|
| 1 | **Feetech SCS0009** (3rd finger) | $16 | as above |
| 3 | **Feetech STS3032 C001** (6 V, 4.5 kg·cm) — shoulder, elbow, wrist | $20 | [Babsco](https://shop.babsco.com/feetech-sts3032-4-5kg-compact-smart-servo-c001) · [AIFITLAB](https://aifitlab.com/products/feetech-sts3032-servo-motor) · [Robotdoo](https://robotdoo.com/products/feetech-sts3032-360-degree-serial-bus-servo) |
| 1 | **VL53L1X time-of-flight distance sensor** (Jonathan's "1 Sensor") | $15 | [Pololu](https://www.pololu.com) · [Adafruit](https://www.adafruit.com) · [SparkFun](https://www.sparkfun.com) |
| 1 | **M2 brass heat-set insert kit** + M2/M3 screw assortment | $25 | Amazon; precision hardware from [McMaster-Carr](https://www.mcmaster.com) |
| 1 | **1.5 mm brass rod** (hinge pins), 300 mm | $8 | hobby shop / Amazon (K&S Metals) |
| 1 | **Elastic cord** 1 mm (finger return springs) | $7 | craft store / Amazon |
| 1 | Servo bus extension cables, 3-pin, assorted lengths | $10 | wherever you buy the servos — **buy spares** |
| — | **Filament** — PLA+ for structure, TPU for fingertips | $25 | [Prusament](https://prusa3d.com) / Polymaker / Overture |

**Send the filament to your friend with the printer.** People are much happier
printing for you when the plastic shows up with the job.

---

## Wave 3 — Phase 3, only if it's going well (~$150)

| Part | ~$ | Note |
|---|---|---|
| MAX98357A I²S amp + 3 W 4 Ω speaker | $18 | the *talk* function |
| Raspberry Pi 5 (4 GB) + PSU + SD card | $95 | the thinking head |
| 4× more STS3032 + 3× SCS0009 (second arm) | $130 | Phase 2 repeated, much faster the second time |
| Solder practice kit | $10 | **buy this in Wave 1 if Jonathan is keen** |

---

## Printing — you don't own a printer

Your three friends are the plan. Make it easy for them:

- **Send them filament** and a ready-to-print `.3mf` with the profile already set.
- **Batch it.** One bed per phase, not one part per week. Print 3 variants of the
  small parts at once so we pick the winner instead of re-printing.
- **Backup if a friend is slow:** [JLC3DP](https://jlc3dp.com) (cheapest, ~1 wk),
  [Craftcloud](https://craftcloud3d.com) (price-compares many vendors),
  [PCBWay](https://pcbway.com). Also check your **public library** — many now
  have printers and will run a job for a few dollars.
- **If you buy one later:** a **Bambu Lab A1 mini** (~$250) is the right call for
  this project — fast, near-zero tuning, and small enough that Jonathan can
  actually operate it. The P1S (~$700) only matters if you move to ABS/ASA.

---

## Tools you probably already have

Soldering iron · flush cutters · hobby knife · small files · calipers ·
hot glue gun · **cardboard** (the most-used material in Phase 1) · masking tape
and a Sharpie (for labelling servo IDs — do not skip this).

---

## Rough totals

| | |
|---|---|
| Wave 1 | ~$90 |
| Wave 2 | ~$170 |
| **Phase 0–2 total (working arm + hand)** | **~$260** |
| Wave 3 (full mini robot) | +~$150 |
