---
title: "Can't enable compiz.."
date: 2009-06-04
forum: x86 64-bit Users
---

### Post by MasterNetra on 2009-06-04
For some reason I cannot enable compiz-fusion on jaunty. tried to enabling it first via visual effect option (eg. normal under visual in apperance) then tried compiz --replace in term and ended in failure.

---

### Post by Darkdelusions on 2009-06-04
> **MasterNetra said:**
> For some reason I cannot enable compiz-fusion on jaunty. tried to enabling it first via visual effect option (eg. normal under visual in apperance) then tried compiz --replace in term and ended in failure.

Have you installed the driver for your video card?

---

### Post by MasterNetra on 2009-06-04
> **Darkdelusions said:**
> Have you installed the driver for your video card?

Wouldn't even know what to install, compiz has worked in previous versions of Ubuntu and I never needed to install any addtional drivers for it. *points to signature as it shows his specs*

---

### Post by Darkdelusions on 2009-06-04
> **MasterNetra said:**
> Wouldn't even know what to install, compiz has worked in previous versions of Ubuntu and I never needed to install any addtional drivers for it. *points to signature as it shows his specs*


System>>Administration>>Hardware Drivers

***oops just noticed your specs :) I am so used to nvidia \ ati questions :)

This might help [http://ubuntuforums.org/showthread.php?t=620843&page=2](http://ubuntuforums.org/showthread.php?t=620843&page=2)

---

### Post by MasterNetra on 2009-06-04
> **Darkdelusions said:**
> System>>Administration>>Hardware Drivers

***oops just noticed your specs :) I am so used to nvidia \ ati questions :)

This might help [http://ubuntuforums.org/showthread.php?t=620843&page=2](http://ubuntuforums.org/showthread.php?t=620843&page=2)

That applies to hardy it seems, compiz worked for me on hardy & interpid just not on Jaunty for some messed up reason.

---

### Post by istblacken on 2009-06-05
you can run compiz-check script to find out what is preventing it to work.
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by exk on 2009-06-05
This seems like the appropriate place for my problem as well (sorry to intrude on the tread).

I am also having trouble enabling compiz on 9.04. I have a GeForce 9400 GT with Nvidia 180.44 drivers installed; although the driver is not showing up in Hardware drivers, but running nvidia-settings shows that 180.44 is running.

I ran the script that was suggested by istblacken and got the following output:

```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation D9M-20 [GeForce 9400 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

Any suggestions are welcome.

---

### Post by MasterNetra on 2009-06-06
nice apparently my Intel Card is blacklisted however thanks to the script I can now bypass it and enable it. Thanks!

---

### Post by MasterNetra on 2009-08-30
*With updates intel card no longer blacklisted thread is being marked as solved.*

---

