---
title: "x64 sluggish response"
date: 2009-05-21
forum: x86 64-bit Users
---

### Post by nixIT on 2009-05-21
Hello all,

Installed 9.04 64-bit the other day, updated with patches, and then installed the following:

Restricted Extras
Envyng, and then ATI drivers
VLC
Banshee
Deluge

Once I was done installing and updating, my system seemed VERY sluggish.  I turned off desktop effects and still the system was not as responsive as 8.10 32-bit.

I have the following hardware:

Athlon 64 X2 5400+
G.SKill 4 gigs memory
Saphire Radeon HD 3870 512megs
GIGABYTE GA-MA770-DS3 AM2+/AM2 AMD 770 ATX motherboard

I have always had some issues running 64 bit linux distros on this system.

Any ideas why?

-nixIT

---

### Post by Anubis on 2009-05-21
"sluggish response" is not enough information to tell you anything. How about you run some sort of benchmark to give us numbers or something? Search the repos of Hardinfo. Better yet goto the website and get the latest Hardinfo, use the network updater that Hardinfo has, then post some results.

---

### Post by nixIT on 2009-05-21
right clicking desktop and selecting Change Desktop Background would take 30+ seconds, and if/when it does come up changing between the tabs (Theme, Background, Fonts, Interface, etc) would be painfully slow, or the window would turn dark like it has locked up.  It would remain this way for over a minute and sometimes I would then gain control but the tab did not change.

Going under System Preferences and selecting anything MAY launch the desired application, if it didn't I would try again, nothing.  Giving up I open a browser to come here, and 30+ seconds later I would have X number of the system preferences app loaded.   Trying to close them would result in the window going dark (ie. appears to be locked up).

Anyone else experiencing this?  I have since started an install of 32 bit on this system as I can't work with a system this non responsive.

--nixIT

---

### Post by pixel :-) on 2009-05-21
The problem is most certainly in

Restricted Extras
Envyng
ATI drivers

All 3 are not supposed to install ati drivers? Remove enyng and ati drivers (from web site) and reinstall the default of the official repositories.

---

