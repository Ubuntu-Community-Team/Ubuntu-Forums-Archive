---
title: "trackpad driver bug"
date: 2007-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by benkillin on 2007-11-06
The I have a synaptics touchpad on an HP pavilion dv5215us laptop and there is a bug with the trackpad driver: when I am moving the mouse or moving and holding down the left mouse button on the trackpad the mouse freezes up and moves erraticly and does some random clicking. 

dmesg revealed these driver messages:

[ 1795.603023] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.606073] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.608246] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.609761] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.626565] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1795.628829] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.631187] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.635225] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.636825] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.646466] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1795.664943] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1795.666482] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.667851] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.669540] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.671129] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1795.671132] psmouse.c: issuing reconnect request


how do I make it so this doesn't happen?

I am using 7.10 x86_64 on an AMD64 processor (Turion64).

---

