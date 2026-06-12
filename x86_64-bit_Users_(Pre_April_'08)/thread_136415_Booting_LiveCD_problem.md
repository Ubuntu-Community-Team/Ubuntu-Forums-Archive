---
title: "Booting LiveCD problem"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by FlakJacket on 2006-02-25
I'm trying to boot a LiveCD of Breezy on a tray-loading iMac.  Everything works perfectly until you get to the bootup screen with the ubuntu logo and the check list of boot items.  Everything is marked ok until it gets to Gnome Desktop Manager.  The first time it said failed continued and then I was at a bash prompt.  The second time it never said failed but went to a blank screen while the cd drive continues to churn.  The iso's md5's were fine so I'm not sure if this might be a ram issue or what.  Any help would be most appreciated.

Thanks,
  Flak

---

### Post by ssam on 2006-02-26
there is a bug with the graphics detect on the imac, if you have a browse though this forum you'll find some posts about fixing it. the trouble is you may have to do it everytime you run the live cd.

---

### Post by jdp on 2006-02-26
It might also be a problem with the Gnome Date Bug.  Be sure the date is set to something sane.

---

### Post by FlakJacket on 2006-02-26
I changed my xorg and I got to a brown screen with a grey rectangle but then it went back to black and nothing. How do I check the date?

Flak

---

### Post by jdp on 2006-02-26
Switch to another console, with Ctrl-Opt-F1.  Then login and use the **date** command to set the correct time.  Then do a reboot.  You might also want ot check that the PRAM (Mac clock) battery isn't dead in your Mac.  If you unplug the machine and you lose the time again, the battery is dead. They are about $5-6 online, and probably $12+ at RadioShack for the 1/2AA 3.6v Lithium cell you need.

---

### Post by FlakJacket on 2006-02-26
I got to Update Notifier in the GNOME startup but then both the logo and the cursor disappeared.  It's hooked up to the internet so the date should set at startup anyway.

Flak

---

### Post by FlakJacket on 2006-02-26
How do you go back to gdm after hitting ctrl+option+f1?

Flak

---

### Post by jdp on 2006-02-26
It's usually on F7.

---

### Post by FlakJacket on 2006-02-26
when i do an hd install will i also have to edit the xorg.conf?

Flak

---

### Post by jdp on 2006-02-26
Either that or run **sudo dpkg-reconfigure xserver-xorg**.  You'll only have to do it the one time though, as it will be saved to the HDD in that case.

---

