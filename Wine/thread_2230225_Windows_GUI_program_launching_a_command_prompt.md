---
title: "Windows GUI program launching a command prompt"
date: 2014-06-18
forum: Wine
---

### Post by seanos on 2014-06-18
I’ve got a couple of programs working under Wine (1.6.2 on Ubuntu 14.04) and they both launch command line programs.  This all works fine, but Wine doesn’t show me the command windows so I have to monitor the files they are writing to so I can tell when they’re done.

Is there any way to get Wine to show me these command windows?

---

### Post by Karlchen on 2014-06-18
Hello, seanos.

As I do not know what your 2 GUI programmes are trying to do in detail, I can only tell you this: In order to open a cmd.exe window from inside a Windows programme launched by Wine execute ```
start cmd.exe
``` Depending on some details of your Wine environment it may be necessary to actually execute it like this: ```
C:\windows\command\start.exe cmd.exe
```
HTH,
Karl

---

### Post by seanos on 2014-06-18
Thanks for your reply, Karlchen, but...

They&#8217;re not *my* programs so I have no control over how they launch other programs.  I couldn&#8217;t even tell you what mechanism they use to launch these programs exactly, but in Windows they produce a command prompt window with output so it&#8217;s possible that they invoke cmd.exe.

---

### Post by seanos on 2014-06-24
The solution I found for this was to either run the program from a terminal or include ```
Terminal=true
``` in the .desktop file that launches the program.  Looks a little ugly, but all the output from console programs run by the Windows gui program goes to the original terminal.

---

