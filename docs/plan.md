# The build plan

Sunday mornings, ~90 minutes each. Every session ends with **something that
moves**, or **something Jonathan made**. Never end a session on a cliffhanger.

---

## Phase 0 — "It's alive" (1 Sunday)

**Goal:** a motor moves because Jonathan told it to.
**Needs:** Wave 1 shopping only. No printing.

1. Plug XIAO ESP32-S3 into the Bus Servo Driver Board. Plug in one SCS0009.
2. Run the ID-setting tool once per servo — each motor gets a number, 1 to 6.
   *(Jonathan picks which motor is which number and writes it on masking tape.)*
3. Upload a sketch with one line: `servo.move(1, 512);`
4. Jonathan changes `512` to other numbers and watches what happens. He finds
   the smallest and biggest numbers that work. **Write them down.** That is
   calibration, and he just did it.
5. Tape a cardboard finger to the table, tie fishing line to it, tie the other
   end to the servo horn. Run the code. **The cardboard finger curls.**

> That last step is the whole project in miniature. Do not skip it.

---

## Phase 1 — The Hand (4 Sundays)

### S1 · Design the hand
- Trace Jonathan's hand on paper. Measure finger lengths with a ruler — he does
  the measuring, Adam writes the numbers in a table.
- Jonathan decides: which 3 fingers? How long? Pointy or round tips?
- Adam + Claude turn the numbers into `cad/hand.scad`. Render it on screen.
  Jonathan changes numbers until he likes it.
- **Build the whole hand in cardboard first.** Check it fits a high-five.
- Send STLs to the friend with the printer. *(Print 3 fingertip variants —
  round, flat, TPU-grippy — and pick the winner later.)*

### S2 · Print week — build the controller
Printing takes a week, so this Sunday is software.
- Flash the web-slider firmware: the XIAO makes its own WiFi network, Jonathan
  opens a page on the iPad with 6 sliders, and drags them to move motors.
- No parts yet — he drags sliders and watches bare servos spin. Still fun.
- Jonathan names the sliders.

### S3 · Assemble the fingers
- Press M2 heat-set inserts (Adam, hot iron).
- Cut 1.5 mm brass rod to length for hinge pins (Adam cuts, Jonathan deburrs
  with a file and pushes the pins home).
- **Jonathan threads the tendons.** Fishing line through PTFE tube, through each
  finger segment, knot at the tip. This is a real fine-motor job and it's his.
- Elastic cord on the back of each finger.
- Bolt servos into the forearm.

### S4 · Make it work
- Calibration: for each finger, find the "all the way open" number and the "all
  the way closed" number. Jonathan reads them off the slider page; Adam pastes
  them into `firmware/calibration.h`.
- Set the **torque limit**. Explain it: "this number is how hard it's allowed to
  push." Jonathan picks a number and tests it against his own hand.
- Write the first gestures: `fist`, `open`, `point`, `count-to-3`.
  **Jonathan chooses and names them.**
- **Milestone: the hand high-fives you.**

---

## Phase 2 — The Arm (4 Sundays)

### S5 · Sensor: make it high-five by itself
- Add the VL53L1X distance sensor to the palm.
- One rule, in plain words: *"if something is closer than 20 cm, close the
  fingers."* Jonathan writes the rule in English, Adam writes it in C.
- Jonathan tests it by waving his hand at it, and finds the distance where it
  triggers. Tune the number together.

### S6 · Design + print the arm
- Three joints: shoulder, elbow, wrist. Jonathan measures his own arm.
- Same loop: numbers → `cad/arm.scad` → cardboard mock → send to print.
- **The DOF lesson:** count the joints in a real arm vs ours. Why did we pick
  these three and not others?

### S7 · Build the arm
- Assemble, mount to a heavy base (a wooden block — Jonathan can drill it).
- Fit the rubber-band counterbalance. Let him feel the arm with and without it.
- Extend the daisy chain to all 6 servos.

### S8 · Choreography
- Turn on **pose-and-record**: torque off, Jonathan physically bends the arm
  into a shape, presses a key, the pose is saved to `gestures/`.
- He builds `wave`, `high-five`, `hug`, `sleep` by hand. No code.
- **Milestone: film it. Send the video to the class. Consider @MarkRober.**

---

## Phase 3 — Mini HH-robot (later, scoped after Phase 2)

Sketch only — we'll plan this properly once the arm works:
- ~14–18" body, two arms (second arm = repeat of Phase 2, much faster)
- Head with the XIAO's camera and mic + a MAX98357A amp and speaker → *see,
  listen, talk*
- Raspberry Pi 5 as the "thinking head", ESP32 stays as the "muscles"
- Then the last function on Jonathan's list: **walk or move** (almost certainly
  wheels first — honest engineering conversation about why walking is hard)

---

## Soldering — Jonathan's part

Design goal: **almost nothing needs soldering.** The bus servos and the driver
board are all connectors. What's left is a good first soldering lesson:

1. Practice first on a cheap solder practice kit (~$10), not on the robot.
2. His first real joint: the two speaker wires to the amp board in Phase 3.
   Big pads, low stakes, and it makes a *sound* when it works.
3. Rules: goggles on, iron at 300 °C, fan on, "the black stick is the cold one",
   and Adam's hand stays on the iron for the first five joints.
