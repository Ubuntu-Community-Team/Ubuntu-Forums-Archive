---
title: "ERROR: ld.so: objec"
date: 2022-05-16
forum: Wine
---

### Post by yasirrwebdesigner on 2022-05-16
Hi, So I am using Ubuntu Unity Remix 20.04, I installed wine but I get this error if try to create a prefix or use wine 

> **zero@GenOS:~$** wine --version
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
wine-6.0.3 (Ubuntu 6.0.3~repack-1)

> 
**zero@GenOS:~$** wine --help
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/libgtk3-nocsd.so.0' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS64): ignored.
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit


I tired a few things like these following packages > **I had to download this one manually because apt was show package not found**[QUOTE]libgtk3-nocsd0:i386[/QUOTE] and this one > gtk3-nocsdbut I still get the error. How can I fix it while staying on Unity.

---

