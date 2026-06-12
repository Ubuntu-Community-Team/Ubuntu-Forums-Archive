---
title: "Word 2003 under Wine 1.1.2 - language bar won't go away"
date: 2008-08-05
forum: Wine
---

### Post by pedrogent on 2008-08-05
Hello folks.

I installed Microsoft Word 2003 under Wine as I have to work in .doc format on a big project I'm doing and I have to be sure that I have correct formatting. (OpenOffice writer tends to mangle .doc files in my experience.)

I now have a little problem. The language bar thing that comes with Word - as seen below in the attached picture - opens up whenever I start up Word and then won't go away until I reboot. I can move it about the screen (& I do move it down to the bottom corner) but it's a little annoying having it there all the time without being able to get rid of it. So I wonder if anyone can let me know if they've had the same problem and if so, what they did about it.

Thanks a lot.

---

### Post by Rashedul on 2008-12-09
same issue here. Did a little bit of googling and came across this on the wine app db, comment by another user (Danila Sentiabov):

10) to disable annoying language bar:
$ wine cmd
$ c:\>regsvr32.exe /u msutb.dll
$ c:\>exit
Now rename ctfmon.exe in your .wine/drive_c/windows/system32 to something else (or just delete it).

*edited for missing part*

---

### Post by Bodifar on 2009-03-12
Solution worked for me, thanks!

---

