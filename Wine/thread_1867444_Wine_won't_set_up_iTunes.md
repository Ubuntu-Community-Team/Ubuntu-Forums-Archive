---
title: "Wine won't set up iTunes"
date: 2011-10-22
forum: Wine
---

### Post by mellottb12 on 2011-10-22
I'm trying to synchronize my iPod touch and no matter what I try, I'm running into problems...

I can't run a lot of the programs that are similar to iTunes because, as I learned while I had windows, there's something about touches that just doesn't work with certain programs.

So instead I installed Wine in an attempt to get iTunes running, but I can't even figure out how to open the setup.exe file! When I use the terminal to run it, it just says: 
wine: cannot find L"C:\\windows\\system32\\itunes64setup.exe"

So then I figured maybe if I moved the iTunes file into system32 it would be able to recognize it... but after moving and trying the same command (wine itunes64setup.exe) it gives a long error report about how the 64-bit process is not supported in this environment and that the file has a bad exe format (which makes no sense to me).

I also tried running it from the desktop without the use of the terminal... but it loads for a few seconds then just stops. No window comes up, no error report appears, it just quits... I'd really like to know what's going on, if it's just because I'm a linux noob or if it's something else entirely:confused:... I just want to put some more music on my pod!

---

### Post by norseman-has-a-laptop on 2011-10-23
wait you got itunes to work with wine? 
I have been trying to get it to work with wine since I have been using Linux

---

### Post by mellottb12 on 2011-10-23
No no no, I'm *trying* to get iTunes to work with wine... but the setup file for iTunes won't even open

---

### Post by Toz on 2011-10-23
Have a look at playonlinux ([www.playonlinux.com](www.playonlinux.com) - also in the software repositories). It has support for iTunes installations.

---

### Post by mellottb12 on 2011-10-23
ohp, wait... I was just being retarded

There's a choice between a 32-bit or a 64-bit version before you get to the download page

problems solved... for now.

---------------------

and if I have any more problems (which I'm sure I will) I'll be sure to check playonlinux out, thanks!

---

