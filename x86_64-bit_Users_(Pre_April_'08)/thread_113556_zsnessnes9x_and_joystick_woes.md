---
title: "zsnes/snes9x and joystick woes"
date: 2006-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pridkett on 2006-01-06
I've been trying to get either zsnes or snes9x working nicely on my system and I can get about 90% of the way there.  I was able to install zsnes using a --force-architecture argument and the program starts up properly and I'm able to play games if I use the keyboard.  I can also assign joystick buttons using the GUI in zsnes, however it doesn't seem to read the axis.  I noticed it shows this message when starting up:

Device 0 /dev/input/js0
  2 axis, 2 buttons, 0 hats, 0 balls
Device 1 /dev/input/js1
  2 axis, 2 buttons, 0 hats, 0 balls

Which is blatantly incorrect as it should say something like this (taken from ubuntu 386 laptop):

Device 0 Logitech Inc. WingMan Gamepad Extreme
  4 axis, 10 buttons, 0 hats, 0 balls
Device 1 Logitech Inc. WingMan Gamepad Extreme
  4 axis, 10 buttons, 0 hats, 0 balls

This indicates that it's probably having problems reading the joystick information and understanding the parameters of the devices.  When I try to run the 32 bit version of snes9x it reports:

joystick: You need at least driver version 1.0 for joystick support.

The 64 bit version of Snes9x correctly identifies the gamepads, but has issues with actually loading roms, so at the moment switching the version of snes9x in universe is a no go.

Finally, I fired up Mame and saw similar behavior to snes9x, even on the 64bit version of mame.  Basically, it recognizes the keys but not the axes of the joysticks.

I know that the joysticks work,  because I've used the gamepads with no problem in TuxRacer and NeverBall (both 64bit) and jscalibrator shows them working fine.

---

