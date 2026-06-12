---
title: "[SOLVED] Logitech Dual-Action gamepad"
date: 2008-08-16
forum: Wine
---

### Post by Plasma_NZ on 2008-08-16
Right...

Here's what's wrong... 

Linux see's the gamepad correctly..

Games see the gamepad, but buttons and axis pads dont work...

the game is - "18 wheels of steel convoy"

found a post on wine about this... but its too kriptic for me to understand..

Say's to add key and string if it doesnt exsist, which is doesnt in the wine regedit...

> 
+-DirectInput
      |  |
      |  +->*<joystick name> = <axes mapping>
      |      [Linux only (js* devices). This maps axis of joystick "joystick name".  The "axes mapping" is comma
      |       separated list of "axes type"s - one for each joystick axes (hat-pov uses 2 axis).
      |       "axes type" is one of: X, Y, Z, Rx, Ry, Rz, Slider1, Slider2, POV1, POV2, POV3, POV4.
      |       To find the joystick name run 'WINEDEBUG=+dinput wine program.exe 2>&1 | grep joydev_enum_device'
      |       Example: "Logitech Logitech Dual Action"="X,Y,Rz,Slider1,POV1". (two "Logitech" is not a typo)]


totally confused..

---

