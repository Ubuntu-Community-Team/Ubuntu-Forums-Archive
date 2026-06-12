---
title: "DVD and video problems"
date: 2006-09-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by OptimusPrime on 2006-09-30
I'm sure there is something out there that will let me play DVD's and watch movies I download, could anyone tell me where I can find it?  I'm using Gnome on a 64-bit.

---

### Post by xstaticxgpx on 2006-09-30
sudo apt-get install libdvdcss2 totem totem-xine

then just do "totem" in Terminal then Movie > Play Disc or Movie > Open file and then point to your VIDEO_TS.vob

---

### Post by OptimusPrime on 2006-09-30
This is what I get:

Reading package lists... Done
Building dependency tree... Done
libdvdcss2 is already the newest version.
totem is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  totem: Depends: totem-gstreamer (>= 1.4.3-0ubuntu1) but it is not going to be installed or
                  totem-xine (>= 1.4.3-0ubuntu1) but 1.4.1-0ubuntu4 is to be installed
E: Broken packages

---

### Post by reacocard on 2006-09-30
try xine instead

```
sudo apt-get install xine-ui
```

---

### Post by city-17 on 2006-10-02
This guide worked for me: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by RAOF on 2006-10-03
> **OptimusPrime said:**
> ...
The following packages have unmet dependencies:
  totem: Depends: totem-gstreamer (>= 1.4.3-0ubuntu1) but it is not going to be installed or
                  totem-xine (>= 1.4.3-0ubuntu1) but 1.4.1-0ubuntu4 is to be installed
E: Broken packages

This means, I believe, that you don't have the dapper-updates repository enabled.  Could you post the contents of the file **/etc/apt/sources.list**?

---

### Post by kuja on 2006-10-03
> **RAOF said:**
> This means, I believe, that you don't have the dapper-updates repository enabled.  Could you post the contents of the file **/etc/apt/sources.list**?
RAOF, that is most definitely it, check for yourself even: apt-cache show totem-gstreamer

---

