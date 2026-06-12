---
title: "Trackpad on Apple PB 1.67 slooow in Dapper?"
date: 2006-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by wanderfowl on 2006-03-12
Hey,

I'm using the latest versions of Dapper, and ever since I moved from Breezy, the Trackpad on my Powerbook is incredibly slow and the Gnome Mouse Settings panel doesn't help it.  Any idea how I can fix this?

Edit: The following worked for me!

[QUOTE=Coolit] found a problem with removing synaptics, if you have a 3rd mouse button you lose this functionlity, so after a little research on the synaptics touch pad driver site I discovered a better way of sorting this, Just add the following lines to the your xorg.conf.

[B]Section "InputDevice"

Option "MinSpeed" "0.75"
Option "MaxSpeed" "0.85"
Option "AccelFactor" "0.0015"[/B]

I found that a value of 0.75 and 0.85 gave me the perfect screen to touch pad ratio 1:1 in fact but you can adjust this as necessary. [/QUOTE]

---

