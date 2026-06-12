---
title: "[SOLVED] wine error running old win 3.1 app"
date: 2007-09-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Indian Summer on 2007-09-16
Hi,

I'm a very new Ubuntu (Feisty + AMD64) user who is trying to make wine work with an old Windows 3.1 application (a dictionary). This worked fine on SUSE 9.2 (AMD64) and OpenSUSE 10.1, but of course that was probably also an older version of wine.

I followed the installation instructions on the wine site:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I run wine from the terminal, but it doesn't start up. This is what I get:
> $ wine CLUEW.EXE 
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:seh:check_no_exec No-exec fault triggered at 0x17e079, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1148ee, enabling work-around
err:ntdll:RtlpWaitForCriticalSection section 0x7b9274c0 "syslevel.c: Win16Mutex" wait timed out in thread 000b, blocked by 000c, retrying (60 sec)
wine: Critical section 7b9274c0 wait failed at address 0x7bc39110 (thread 000b), starting debugger...
Unhandled exception: wait failed on critical section 0x7b9274c0
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39110
$ Process of pid=000a has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)

I'm not all that familiar with wine either, so I suppose it could be a wine configuration issue as well.

---

### Post by leo_rockway on 2007-09-16
you have to tell wine that you want it to run as win 3.1 (i think it comes as xp or 2000 as default)

in kubuntu gutsy i do it by going to system preferences -> advanced tab -> windows applications -> windows version.

i don't know how to go about it in gnome since i never used it.

---

### Post by Indian Summer on 2007-09-16
Yes, I think I did that using winecfg. winecfg brought up a GUI, and in there I set the default to Windows 3.1.

---

### Post by crjackson on 2007-09-16
I understand you want to use this particular dictionary app. but did you know that Ubuntu 7.04 Feisty already has a very good dictionary built in.

---

### Post by Indian Summer on 2007-09-16
Ah, I did not know that. But since you mentioned it, I had a look. It seems like an okay dictionary - thanks! It can probably help me part of the way, but not all the way. I would love to find a native Linux replacement for Clue, but it would need to have translations: English to Norwegian and Norwegian to English.

---

### Post by leo_rockway on 2007-09-17
I used to use babylon a lot on Win (i'm a spanish/english translator).
Babylon is fast and usually accurate, but i realized it works better for me to use online dictionaries (like word reference or webster) since i get more results and a better understanding of the word i'm looking for.

I haven't even tried to run babylon on my linux machine. i heard there's a babylon replacement in linux (that uses old babylon glosaries) but i haven't tried that either.

---

### Post by Indian Summer on 2007-09-22
I was about to start compiling wine from the source code, but then a new version of wine became available in the repository today (wine-0.9.45), and that solved the problem! I'm so relieved :D

Now I just need to figure out how to make Firefox run those pesky Java applets, and everything will be perfect ...

---

### Post by leo_rockway on 2007-09-23
how to make java work is all over the web, you only need to google it.

---

