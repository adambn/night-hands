# Design decisions (and why)

## The six degrees of freedom

Jonathan wants 3 fingers, and Adam wants the *concept* of joints and DOF to be
visible. So: **6 motors, 6 degrees of freedom.** Small enough to understand,
big enough to do something real.

| # | Joint | Motor | What it buys us |
|---|---|---|---|
| 1 | Shoulder lift | STS3032 | raises the whole arm — needed for a high-five |
| 2 | Elbow | STS3032 | reach out and pull in — needed for a hug |
| 3 | Wrist rotate | STS3032 | turn the palm to face you |
| 4 | Thumb | SCS0009 | tendon |
| 5 | Finger 2 | SCS0009 | tendon |
| 6 | Finger 3 | SCS0009 | tendon |

**Kid activity:** Jonathan counts the joints in his own arm (shoulder 3, elbow 1,
wrist 2, each finger 3+) and compares. A real arm is ~27 DOF. Ours is 6. That
number *is* the engineering conversation.

## Why serial bus servos, not normal hobby servos

This is the single most important choice, and it's not the obvious one.

Normal hobby servos (SG90/MG90S) are cheaper and have more tutorials. We are
**not** using them. Feetech bus servos (`SCS0009`, `STS3032`) win on four things
that matter specifically for a 7-year-old's project:

1. **One wire, not eighteen.** All six servos daisy-chain on a single 3-pin
   cable, each with an ID number. A hobby-servo build needs a power distribution
   board and 18 wires. Wire spaghetti is where kid projects die.
2. **Pose-and-record.** These servos report their own position. You can grab the
   arm, physically bend it into a wave, and press a key to save that pose.
   Jonathan can choreograph the robot **with his hands instead of with code.**
   This is the best thing in the whole project.
3. **Torque limit.** You can tell the servo "never push harder than 30%." The
   robot then *physically cannot* squeeze or pinch hard. A hobby servo has no
   such setting — it pushes at full strength until it strips its gears.
4. **No jitter.** Hobby servos buzz and twitch. These hold still.

Cost of the choice: ~$18/servo instead of ~$5, and slightly more setup on day 1
(each servo needs its ID set once). Worth it.

## Why 6 volts for everything

`SCS0009` and `STS3032` are both **6V** parts. Running the entire robot on one
6V rail means **one power supply, one bus, one voltage** — nothing to get wrong.

We deliberately did *not* use the popular `STS3215` (the SO-101 arm servo).
It's a 7.4V or 12V part, so it would force a second power rail, and at 30 kg·cm
and 55 g it is far too big and strong for a 14-inch robot. `STS3032` is
4.5 kg·cm and 25 g — correctly sized.

> **Shoulder torque check.** Arm ≈ 150 g, centre of mass ≈ 7 cm out from the
> shoulder → about **1.1 kg·cm** to hold it horizontal. STS3032 stalls at
> 4.5 kg·cm, so we have ~4x margin at stall but less on *continuous* holding.
> Fix: a **rubber band counterbalance** from the upper arm to the shoulder
> bracket. It's one cent of rubber that halves the motor's job — and it is a
> genuinely great thing to show a 7-year-old. ("Feel how heavy the arm is.
> Now feel it with the rubber band on.")

## Why XIAO ESP32-S3 Sense as the brain

Adam picked ESP32-S3 now / Raspberry Pi later. The **XIAO ESP32S3 Sense** is the
best version of that choice because it already has a **camera and a microphone
on the board**. Two of Jonathan's five functions (*see*, *listen*) are then a
firmware problem, not a shopping problem. It pairs with Seeed's
**Bus Servo Driver Board for XIAO**, which is the exact half-duplex UART adapter
the Feetech bus needs — no level-shifter circuit to build.

The Raspberry Pi joins in Phase 3 as the talking/thinking head. The ESP32 stays
as the muscle controller. Jonathan gets a clean mental model: **"the Pi decides,
the ESP32 moves."**

## Why we design the hand in OpenSCAD

Adam has no printer — three friends do. That means **each print revision costs a
week**, so we cannot iterate our way to a design. Two consequences:

1. **Cardboard first.** Every part gets mocked in cardboard and hot glue before
   anyone prints anything. Jonathan is good at cardboard. Cardboard is free.
2. **Parametric CAD.** The hand is written as code in
   [OpenSCAD](https://openscad.org/) — free, runs anywhere, and the model *is*
   a text file of numbers. Jonathan changes `FINGER_LENGTH = 60;` to `75` and
   watches the hand get longer. He does not need to learn Fusion 360 to
   participate in the industrial design. **This is the "building with AI" part:
   he says what he wants, we write the number, the shape changes.**

## Hand scale: bigger than the robot

Jonathan's drawing puts a hand on a foot-tall robot. At that scale the hand
would be ~1.5" across — too small for servos, and too small to actually
high-five a human.

**Decision:** the Phase 1 hand is built at **~70% of an adult hand** (about the
size of Jonathan's own hand — we will literally trace it). It lives on a desk
stand and can really slap your palm. The Phase 3 mini robot gets its own,
simpler mitten-style hands for hugging, and the big hand stays as its own demo
object. Alternatively we make the mini robot ~18" so a 70% hand is in proportion
— that's a Phase 3 decision, not a today decision.

## Known hard parts (where this will actually get stuck)

| Risk | Mitigation |
|---|---|
| **Tendon tuning** — the #1 time sink in every tendon hand | PTFE tube guides through the palm, braided Dyneema line (not mono), and a tensioner screw at the servo end so tension is adjustable *without* re-tying knots |
| Fingers don't spring back open | Elastic cord on the back of each finger, sized *before* printing final parts. Test on the cardboard mock. |
| Print tolerance on hinge pins | Design hinges around **1.5 mm brass rod**, holes at 1.7 mm. Never print a pin. |
| Servo screws stripping printed plastic | **M2 heat-set inserts** everywhere a screw goes into plastic |
| A week per print revision | Cardboard mock first; print all variants of a small part at once (print 3 finger designs, pick the best) |
| Kid loses interest during a print week | Phase 1 is deliberately front-loaded with things that move on day one |
