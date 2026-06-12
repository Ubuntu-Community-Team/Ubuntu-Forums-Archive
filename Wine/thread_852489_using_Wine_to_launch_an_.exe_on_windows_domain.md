---
title: "using Wine to launch an .exe on windows domain"
date: 2008-07-07
forum: Wine
---

### Post by ziegster on 2008-07-07
Hello everyone

What I'm trying to do is start a program that is installed on an windows domain. Everything is already installed on the domain so i was trying to launch the exe through the terminal.

I made a shortcut on my desktop and when i typed $ wine Probookw.exe this is what i got.

ziegen@ziegen-desktop:~/Desktop$ wine Probookw.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing
ziegen@ziegen-desktop:~/Desktop$ 



If anyone can lead me in the right direction or anyone needs more info i would greatly appreciate the help.

Thank you

---

