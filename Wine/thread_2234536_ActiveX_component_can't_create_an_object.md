---
title: "ActiveX component can't create an object"
date: 2014-07-15
forum: Wine
---

### Post by paul1945 on 2014-07-15
Hi, I am trying to get a medication guide called MIMS going under Wine.
It installs OK but when I try to run it it complains that the number of users are not defined,
then loads the splash page, and comes up with the error "ActiveX component can't create an object"
and exits.
Has anyone an idea on how to fix this? 
I am running Ubuntu 14.04 and the standard Wine that came with the install iso. I have had this program running under an earlier Ubuntu install, in which the initial "number of users" error also came up, but the program ran OK, so it must be possible to get it running.
This as you may imagine is rather important to me.
Thanks, Paul.

---

### Post by paul1945 on 2014-07-28
Hi, All.
Eventually managed to fix this myself.
I guessed that the problem was a poorly functioning or broken .net 4 system.
Also found that mscoree.dll was missing.
Updated the files in the c:\program files\common files\microsoft shared\dao\ directory and copied the contents of the VB6 directory from a working Windows XP install to c:\program files\common files\microsoft shared\vb6\ . Also copied the files DAO350.DLL, hha.dll, HHActiveX.dll, hhctrl.ocx, hhsetup.dll, mscoree.dll, VB6STKIT.DLL to c:\windows\system32\ and registered Dao360.dll at the Wine command prompt by typing as follows: regsvr32 dao360.dll
Some of these files may not be necessary, but as I am not quite sure which components do what, this was the only way out for me.
It now all works a treat.
Paul.

---

