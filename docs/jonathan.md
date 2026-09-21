# Jonathan's job

The rule: **a real job in every step.** Here is the list, so nobody forgets.

## Design
- Trace his hand. Measure the fingers with a ruler. Read the numbers out loud.
- Decide which 3 fingers, how long, what the fingertips look like.
- Change numbers in `cad/hand.scad` and watch the shape change on screen.
- Build every part in cardboard before it gets printed.
- Name the robot's gestures.

## Electronics
- Choose which servo is ID 1, 2, 3… and label them with masking tape.
- Find the minimum and maximum number for every joint (this is calibration —
  tell him that's what it's called).
- Pick the torque limit and test it against his own hand.
- Later: solder the speaker wires, with Adam's hand on the iron.

## Mechanical
- File the brass hinge pins smooth and push them home.
- **Thread all the tendons.** His job, start to finish.
- Tie the knots.
- Drill the base block.

## Software
- Drag the sliders on the iPad and discover what each one does.
- Write the sensor rule in English: *"if something is closer than 20 cm, close
  the fingers."* Adam translates it to C in front of him.
- Physically pose the arm and press the record key. He is the animator.

## Things to say out loud during the build
- *"How many joints does your arm have? How many does ours have?"* → **DOF**
- *"Feel how heavy the arm is. Now feel it with the rubber band."* → **torque**
- *"These strings are its tendons. Touch the back of your hand and wiggle your
  fingers — you can feel yours."* → **tendon drive**
- *"This number is how hard it's allowed to push."* → **torque limit / safety**
- *"One wire, six motors. How does it know which one you mean?"* → **addressing**
- *"It didn't work. What changed since it last worked?"* → **debugging**, the
  most valuable thing in the whole project
