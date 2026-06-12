---
title: "anydvd and dvdclone2 in wine?"
date: 2008-01-19
forum: Wine
---

### Post by billmik on 2008-01-19
Can anyone tell me if and how i can get anydvd and dvdclone 2 running in ubuntu with wine maybe?

thanks

---

### Post by pytheas22 on 2008-01-19
Why do you want to use those programs?  Linux can play DVD's from any region if you install the proper decryption files (which do not ship with Ubuntu because it would not be legal, but they're easy to install if you search the forums for a guide).  And K3b should be able to copy DVD's easily.  tovid is also a great program for creating your own DVD's, in whichever regional encoding you choose, to be played in any DVD player or computer.

---

### Post by Eck on 2008-01-20
He's trying to rip encrypted.

The current answer is DVDFabHDDecrpyter and DVDShrink (need msvcp40.dll, quartz.dll, and mfc42.dll from Windows XP.  Deposit them into ~/.wine/c:\windows\system32 and in winecfg add quartz as a new overide native/builtin.  Set DVDShrink in winecfg applications to Windows XP.)

Always do a deep analysis with DVDShrink on files created by DVDFab stuff as they do wacky stuff to get around protections and Deep Analysis fixes it up so stand alone dvd players can play the dvds.  Do it even if the size doesn't need shrinking.

Have DVDShrink create an iso image and burn a dvd image to DVD+R with K3b or Brassero.

If using KDE and K3b, K3b can take the VIDEO_TS folder created by DVDShrink in encode to folder mode and burn a DVDVIDEO project, but the ISO method is just as easy to do and you can use Gnome burning software that way.

---

### Post by billmik on 2008-01-20
Ok thanks man I'll give that a try, Shrink used to give me problems in xp so ive been using dvdclone2 with anydvd too bad i cant keep dvdclone2

---

### Post by billmik on 2008-01-23
What is dvdfab? wheats it used for? windows version or linux? Is there a guide somewhere for this set up? thanks

---

