---
title: "Ultra Fractal 5 hangs on wine 1.4"
date: 2012-05-05
forum: Wine
---

### Post by rosros-5 on 2012-05-05
Program: "Ultra Fractal 5"
Downloadable from: [http://www.ultrafractal.com](http://www.ultrafractal.com)
Wine version: 1.4
Linux: Ubuntu 12.04 LTS

Terminal output:
fixme:system:SetProcessDPIAware stub!
err:listview:LISTVIEW_WindowProc unknown msg 108c wp=00000000 lp=00000000
fixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0

Ultra Fractal 5 (or even X) hangs after "LISTVIEW_WindowProc unknown msg 108c".
No wine configuration change (but I tried native comdlg.dll, with the same result).
BTW: I (patched for my system and) recompiled wine 1.1.34,
compilation was successful; I then ran wine from the build dir,
and got the same message (among others).

---

### Post by flemur13013 on 2012-05-05
I had similar error msgs and sound problems (12.04 w/wine 1.4), fixed by installing Wine 1.5 (.3)

---

### Post by rosros-5 on 2012-05-06
A bug report has been filed on this, [link]("http://bugs.winehq.org/show_bug.cgi?id=30604").

wine1.5-i386_1.5.3-0ubuntu1~ppa1~precise4+pulse17_i386.deb
cannot be installed on my system:

root@Aspire5230:~/Downloads# dpkg -i wine1.5-i386*.*
(Reading database ... 243876 files and directories currently installed.)
Preparing to replace wine1.5-i386 1.5.3-0ubuntu1~ppa1~precise4+pulse17 (using wine1.5-i386_1.5.3-0ubuntu1~ppa1~precise4+pulse17_i386.deb) ...
Unpacking replacement wine1.5-i386 ...
dpkg: dependency problems prevent configuration of wine1.5-i386:
 wine1.5-i386 depends on wine1.5:any (= 1.5.3-0ubuntu1~ppa1~precise4+pulse17).
dpkg: error processing wine1.5-i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.5-i386

---

### Post by rosros-5 on 2012-05-06
Installing the native comctl32 with
[FONT=Courier New]winetricks comctl32 [/FONT]
"did the trick".
Now 'Ultra Fractal 5" works with wine-1.4.

---

