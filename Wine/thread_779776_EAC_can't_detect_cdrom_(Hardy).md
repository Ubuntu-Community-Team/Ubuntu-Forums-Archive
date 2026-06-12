---
title: "EAC can't detect cdrom (Hardy)"
date: 2008-05-03
forum: Wine
---

### Post by logos34 on 2008-05-03
Exact Audio Copy worked fine in Gutsy (x64).  (-->set to EAC Options>Interface tab>Native Win32 NT/2000/XP)

Using wine 09.60

Won;t see audio cd in drive using either Native or external ASPI interface.

Nor do Cdex and dBpoweramp and foobar2000 recognize the cdrom anymore.

I've been trough wine config again and the cdrom drive is seen (A).  EAC.exe is set like the others for windows server2003.  Worked fine before.

If I set the interface tab on EAC to use 'Native win32 interface' and restart, it just freezes and I have to kill it.

Between this and a couple of other probs I'm ready to go back to gutsy.

---

### Post by logos34 on 2008-05-03
The devil really is in the details.  Jeez, it took me a long time to get to the bottom of that!

I had to through and click on each drive/partition/device in winecfg and check that each was showing up correctly under type.  Turns out the audio cd in the drive was incorrectly designated as one of the local drive partitions. The was a duplicate entry too, so had to delete that.

So if anyone else is having the same problem, it's not enough to accept the autodetect results; click on each one, check that the type is correct, then click on the mountpoint and navigate to the location.  If the drive letters change remember to go back and change EAC's output folder and paths to plugins/codecs.

(Edit: 

It wasn't saving the settings - I was still having a problem with EAC not be able to detect the cdrom after restart or sometimes from standby resume, so I ended up reverting to wine version .47 (same one that I last used in gutsy).  That seemed to do the trick.  I *think*)

---

