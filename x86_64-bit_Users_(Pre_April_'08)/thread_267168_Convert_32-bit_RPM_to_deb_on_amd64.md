---
title: "Convert 32-bit RPM to deb on amd64"
date: 2006-09-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by cybertoast on 2006-09-28
I know I can "alien <rpm>", but is there a way to build the 32-bit .deb from a 32-bit .rpm on a 64-bit machine? the error I get when I try to do the conversion is:
[INDENT]```
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
```[/INDENT]

I'm trying to get the pixma-ip4000 drivers installed, and the japanese drivers only come in 32-bit rpm flavors.

thanks much.

---

### Post by FluffyElmo on 2006-09-28
Do you get that error when converting it to a .deb or when you try to install the resulting .deb file? If it's the latter you can use the --force-architecture switch like so:
```
sudo dpkg -i --force-architecture packagename_i386.deb
```

You may have issues using 32bit printer drivers witha  64bit system, I've never tried it but report back if it works:)

---

### Post by ulefr01 on 2006-09-28
Same problem as : [http://www.ubuntuforums.org/showthread.php?t=265122](http://www.ubuntuforums.org/showthread.php?t=265122)
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280

---

### Post by cybertoast on 2006-10-01
my question is how to generally convert 32-bit rpm files into amd64 installable .deb's. alien on a 32-bit machine will convert the 32-bit rpm, but is there a way to do it on amd64? since there is a backwards-compatibility layer for 32-bit apps, is there a way to create the 32-bit .deb with alien on the amd64?

---

### Post by tuxcantfly on 2006-10-05
install a 32 bit alien, which will convert your 32 bit rpms into 32 bit debs, then sudo dpkg --force-architecture -i it

---

### Post by amanita on 2006-12-13
I have installed alien(64) over the Synaptic but how can I install 32bit on my Edgy 64 then to convert i386 packages on my amd64? Could you be more specific, please...

---

### Post by mbobak on 2007-04-09
Same question here.

I'm trying to install 32-bit lightscribe, which is distributed as an RPM.

I need to convert the 32-bit RPM to 32-bit .deb.  When I try that w/ the alien that's installed, I get:
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)

So, what now?

Any ideas, anyone?

-Mark

---

### Post by Lonthong on 2007-04-09
> **cybertoast said:**
> I know I can "alien <rpm>", but is there a way to build the 32-bit .deb from a 32-bit .rpm on a 64-bit machine? the error I get when I try to do the conversion is:
[INDENT]```
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
```[/INDENT]

**_I'm trying to get the pixma-ip4000 drivers installed,_** and the japanese drivers only come in 32-bit rpm flavors.

thanks much.

A little bit out of topic but you might want to check [this site]("http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon") for your canon driver

---

