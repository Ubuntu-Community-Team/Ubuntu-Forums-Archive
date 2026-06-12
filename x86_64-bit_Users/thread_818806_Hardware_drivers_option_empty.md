---
title: "Hardware drivers option empty?"
date: 2008-06-04
forum: x86 64-bit Users
---

### Post by radamo on 2008-06-04
I used ENVYNG to load ATI driver 8.3 a few weeks ago.  I would now like to move to a higher version.  I went to System => Administration => Hardware Drivers and nothing appears. It says "No Proprietary Drivers are in use on this system". No options to use one either. 

Can somebody help?  Is this something EnvyNG did to my system?

RA

---

### Post by Sef on 2008-06-04
If you used ENVYNG, then you would have to use ENVYNG again, if it had the new ATI drivers.  The other option would be to uninstall ENVYNG, but that does not guarantee something would show up under the hardware drivers.

---

### Post by radamo on 2008-06-05
> **Sef said:**
> If you used ENVYNG, then you would have to use ENVYNG again, if it had the new ATI drivers.  The other option would be to uninstall ENVYNG, but that does not guarantee something would show up under the hardware drivers.

Prior to using Envy, after my initial install of 8.04 Beta, there was the ATI proprietary driver in that utility.  Then during some update I lost the ATI driver and the system had the mesa driver.  Being new to linux I chose to try Envy to get the ATI driver back.  It worked but it still only has version 8.3.  ATI is up to 8.5 now. 
I was just looking for alternatives for keeping up to date. 

Thanks for any help anyone can provide.
RA

---

### Post by Sef on 2008-06-05
Well, your other option would be in to, again, unistall ENVYNG and install the drivers from [ATI]("http://ati.amd.com/support/driver.html").  Not sure how easy or hard it would be.

---

### Post by radamo on 2008-06-05
> **Sef said:**
> Well, your other option would be in to, again, unistall ENVYNG and install the drivers from [ATI]("http://ati.amd.com/support/driver.html").  Not sure how easy or hard it would be.

Well... that is the rub. I had tried uninstalling Envy and still nothing appeared.. Does the "blacklist" / "whitelist" affect the items that appear in that utility?
RA

---

### Post by kingtaurus on 2008-06-05
How did you uninstall envyng? Did you use 
```

envyng --uninstall-all

```

Further, did you make sure that you re-install the fglrx driver from the ubuntu repository?

---

