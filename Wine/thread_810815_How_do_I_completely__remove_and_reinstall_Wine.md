---
title: "How do I completely  remove and reinstall Wine"
date: 2008-05-28
forum: Wine
---

### Post by MR.UNOWEN on 2008-05-28
Some time ago I messed around with wine and screwed it up. How do I reinstall it from scratch. What do I need to remove.

---

### Post by cogadh on 2008-05-28
Open a terminal and run these commands:
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

---

### Post by MR.UNOWEN on 2008-05-28
Thanks for the help. During the installation, I got a bunch of error during "winecfg".

> preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


Have any clue....

---

### Post by Faud on 2008-05-28
```

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000

```
is normal if you are running.60 & .61

```
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```
is not though.
Try this:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by cogadh on 2008-05-28
Actually, that is just as normal as the preloader errors (the two go hand in hand). Using the info on the Wine wiki page will make it go away.

---

### Post by MR.UNOWEN on 2008-05-29
Well I'm trying to run a program called diptrace (diptrace.com) and it doesn't work. It installs fine, but right when I run it, the program closes on me. It asks if I want to try the 30 day trial and after that it crashes on me. I know people who use it with Wine, so I don't know why it's happening to me.

Here's What I get:
> 
:~/.wine/drive_c/Program Files/DipTrace$ wine Schematic.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


BTW what would cause Ubuntu to logout without the user doing it.

---

### Post by cogadh on 2008-05-29
If you are still getting preloader errors, then you didn't apply the fix on the Wine wiki page Faud linked to, or you only applied the temporary fix and then rebooted, which will reset it back to the default.

As for what would make Ubuntu logout without the user's permission, I don't think there is anything on the system that would do that automatically, but a logout or reboot command could be issued remotely, if your system is insecure. Have you made any changes to the network settings in Ubuntu? It is also possible that a hardware failure of some kind could do that, but that would usually be a reboot, not just a logout.

---

