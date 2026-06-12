---
title: "setup doesn't find cdrom"
date: 2015-09-12
forum: Wine
---

### Post by MikeCyber on 2015-09-12
Hi
I try to install an app.exe and it says "insert CD1"
I've tried all kind of stuff but no luck.
Thanks

---

### Post by yoshii on 2015-09-13
Go to the Ubuntu Applications menu (the ubuntu logo) and select Wine > Configure Wine.  Then wait a few minutes for Wine to load.  If it's the first time you are running Wine since bootup, it will take sort of a long time to load.  But just be patient.  This is normal.  It's faster every other time after that.  OK.  Now browse to the Wine Config tab labeled "Drives".  Then click "Show Advanced".  Now click "Add..." if you don't already see your CD drive in the list.  Choose a letter for the drive.  An early letter is typically what Windows would have, such as D: or E: ... OK now browse to /cdrom/ and set the type to CD-ROM from the "type" menu.  I hope what I've told you is accurate.  But you get the idea, hopefully.  Now quit Configure Wine and retry your installer.  You might have to reboot the computer once before it works though, or at least log out once before it works.  Good luck.

---

### Post by MikeCyber on 2015-09-14
Sure I did. I use wine for many years but trying to install Realflight 4.5 it keeps asking for cd1 even after doing like you said. I'm simply bored to boot windows for a quick RF flight.
in winecfg it's E: as cdrom and even starting setup from winefile e:setup.exe brings up that message.
[IMG]http://i62.tinypic.com/54aejp.png[/IMG]

---

