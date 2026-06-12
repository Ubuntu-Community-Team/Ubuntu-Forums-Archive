---
title: "Wine tells me it cannot find this computer's CD ROM drive"
date: 2012-01-11
forum: Wine
---

### Post by IsThisThingOnOrWhat on 2012-01-11
After installing Morrowind and copying the disc's file into folder on the hard drive and changing the permissions to executable I open the main Morrowind screen asking play, data files, options, elderscrolls.com, technical support, uninstall, quite. Clicking play here gets me the attached error message. "Unable to find CD-ROM drive on this computer". This of course right after I just installed the game, from the CD drive, and I've burned CD's with it.

I'm using Ubuntu 10.10 and Wine 1.2.2

---

### Post by carl4926 on 2012-01-11
Worth checking
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1015](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1015)

I suspect something is wrong in: .wine/dosdevices/

---

### Post by IsThisThingOnOrWhat on 2012-01-12
Is there a command I can put into the terminal that will reconfigure the settings to default? I've used this on VLC to get it to work when I switched the wrong two options and killed my app. Could Wine work similarly?

---

### Post by carl4926 on 2012-01-13
Can you be clear.
Is this happening on a wine install that was previously OK looking for the Optical drive?
Or is this a new install or the first time you tried such a action.

---

### Post by IsThisThingOnOrWhat on 2012-01-13
It was a new install, which is probably why the problem was fixed when I updated the wine version. Thanks.

---

