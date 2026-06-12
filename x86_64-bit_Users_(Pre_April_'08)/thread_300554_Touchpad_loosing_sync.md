---
title: "Touchpad loosing sync"
date: 2006-11-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-11-15
Just switched over to amd64 ubuntu. Everything works except for my touchpad. My touchpad keeps loosing sync and then stops working.

Dmesg says:
```
[  650.125266] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[  650.126418] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  650.135347] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[  650.429610] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[  650.430190] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  650.434670] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.

```

When it dies.

What could be causing this?

---

### Post by hackel on 2006-11-23
I'm having this problem too, on a Compaq V5000.  I'm not using amd64, however, so this issue doesn't appear to be unique to that architecture.

I have found no solution yet, other than switching to the standard ps2 mouse driver (instead of synaptics) and it makes using X extremely difficult.

Here is my pointing device:

I: Bus=0011 Vendor=0002 Product=0007 Version=0000
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I would really love to figure out what is wrong.

---

### Post by alek66 on 2006-11-24
I ve been having that same problem here for over 1year.

---

### Post by moshuptrail on 2006-11-26
I've been having the same problem for some time.
The touchpad will work for a while, then suddenly stops.
dmesg output:
[17193241.668000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
(message repeats)

Can you re-start the mouse driver to regain sync?  How?

I've got a Dell laptop (model C600 I think)
Pentium 3 CPU, 512M ram, running Ubuntu 6.06

---

### Post by enigma_0Z on 2006-11-27
> **moshuptrail said:**
> I've been having the same problem for some time.
The touchpad will work for a while, then suddenly stops.
dmesg output:
[17193241.668000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
(message repeats)

Can you re-start the mouse driver to regain sync?  How?

I've got a Dell laptop (model C600 I think)
Pentium 3 CPU, 512M ram, running Ubuntu 6.06

You can reload the driver like this:

```

sudo modprobe -r psmouse; sudo modprobe psmouse

```

in a console. I don't know what fixed the problem, but I installed ubuntu from the desktop CD and everything works fine now... hrm.

---

