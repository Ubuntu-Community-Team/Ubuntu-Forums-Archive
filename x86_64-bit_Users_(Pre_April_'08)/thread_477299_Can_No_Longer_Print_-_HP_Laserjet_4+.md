---
title: "Can No Longer Print - HP Laserjet 4+"
date: 2007-06-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by _simon_ on 2007-06-18
Used 32bit Ubuntu for years and always been able to print using hpijs

Now I'm using Ubuntu 64bit and no matter which driver I select, the printer spews out complete junk.

Has anyone got this printer working under 64bit? I'm on the verge of putting 32bit back on.

---

### Post by John.Michael.Kane on 2007-06-18
From this [http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus) seems you need to use the Postscript PPD.

Another option is this, and make sure ppdev is listed in the file that open's

```
sudo gedit /etc/modules
```

Then run
```
sudo modprobe ppdev
```

And try reselecting your printer again.

---

### Post by _simon_ on 2007-06-18
No joy :(

Deleted printer, added it again via CUPS interface using the ppd on that site.

I added ppdev

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ppdev

```

Ran modprobe and even restarted but it still prints junk.

---

### Post by John.Michael.Kane on 2007-06-18
It could be a bug in the driver under 64bit, and the way it's comunicating with your printer. That however is just a guess.

I know for myself using a hp laserjet 5p it works fine.

---

### Post by _simon_ on 2007-06-18
I tried it via the live cd just incase there was something wrong with my install but it doesn't work from that either.
It does work from the 32bit live cd though.

Looks like I'll have to put 32bit back on.

---

### Post by capecove on 2007-06-18
Well, this may sound crazy, but why not use a Generic PCL driver for it? That what I ended up doing with my Oki B4300 and it works like a charm. The Oki B4300 driver did the exact same thing you are experiencing, until I changed to the Generic PCL driver. I just used the PCL version I knew the printer could handle. According to the attached link your printer would support up to PCL5E. Good luck, let us know how it works out. :)

[http://www.csgnetwork.com/hppclhist.html](http://www.csgnetwork.com/hppclhist.html)

---

### Post by _simon_ on 2007-06-18
I was really hopeful.

Tried the generic in 32bit Ubuntu and it worked.
Tried from 64bit and it won't.

It's as though the correct data isn't even being sent as the printer doesn't pause for a few seconds whilst getting the data, it just starts straight away,

---

### Post by capecove on 2007-06-18
Okay, I should have said (and you may have already done this)...

Try to install the driver, reboot Ubuntu and power cycle the printer. Try it again. :)

If you already did this, forgive my suggestions. Otherwise, don't give up hope yet, you could be so close!

---

### Post by _simon_ on 2007-06-18
Well I gave up, reinstalled 32bit then had a thought, reinstalled 64bit again lol and got it working.

All I needed to was go into BIOS and set Bi-Directional.

---

### Post by capecove on 2007-06-18
LOL... god thing Ubuntu is so quick to install, huh? :)

Thanks for the word on that. WIll remember that for myself next time.

---

### Post by _simon_ on 2007-06-18
Could do with being faster but yeah it's certainly quicker than some!

Hope this thread will save other people some time and effort. Kicking myself for not thinking of it sooner.

---

### Post by John.Michael.Kane on 2007-06-18
Glad you got it working.

---

### Post by _simon_ on 2007-06-18
Thanks for all the suggestions guys, they have been appreciated. :)

---

